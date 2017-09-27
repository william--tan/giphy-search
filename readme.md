# Assignment 6: Giphy Search
####  by William Tan

**Basic useful feature list:**

 * Generate buttons to search GIFs from Giphy
 * You can limit the number of images
 * You can turn off the GIF animated image, and turn it on again by clicking the thumbnails

**Extra Random Features:**

 * Used Bootstrap for the interface
 * Randomized the color of the buttons
 * Loading screen while the animated version of the GIF is being loaded

 :sparkles:
 
 This is how I did the GIF pausing and the loading screen:
 
 1) First, I created the "Loading Text" as a JQuery Object,  I also made a class called 'hidden' to make it hidden:

    ```javascript
    loadtext.css({'z-index': '100',
                      'position': 'absolute',
                      'color': 'white',
                      'font-size': '20px',
                      'font-weight': 'bold',
                      'transform': 'translate(-50%, -50%)', //centering the text
                      'left': "50%",
                      'top': '40%'})
    loadtext.addClass("hidden");
    $card.append(loadtext); //Card is a JQuery object that makes Bootstrap Cards
    ```
2) Then, I made an on-click function attached to the image. Note that the image has an attribute called 'active', which indicates if the image is a still or an animated image. So basically this will turn a still to an animated image, vice versa. One added feature I added is a feature that turns off the animated picture automatically if you click another still image. In the else clause, I added the on-load function to turn on the loading text and darken the image to indicate that the animated image is being loaded:
    ```javascript
    $img.click(function(){
    if ($(this).attr("active") == "1")
      {
        $(this).css("filter", "brightness(1)");
        $(this).attr("active", "0");
        $(this).attr("src", $(this).attr("surl"));
      }
      else
      {
        if (activated != null)
        {
          activated.attr("active", "0");
          activated.attr("src", activated.attr("surl"));
        }
        $(this).attr("active", "1");
        $(this).css("filter", "brightness(0.4)");
        $(this).parent().children().eq(0).removeClass("hidden");
        $(this).on("load", function(){
          $(this).css("filter", "brightness(1)");
          //console.log($(this).parent().children().eq(0));
          $(this).parent().children().eq(0).addClass("hidden")
        })
        $(this).attr("src", $(this).attr("aurl"));


        activated = $(this);
      }
    })
    ```

The live version is on [https://william--tan.github.io/giphy-search](https://william--tan.github.io/giphy-search)


### Stuff used to make this:

 * [JQuery](jquery.com)
 * [Bootstrap](getbootstrap.com)
