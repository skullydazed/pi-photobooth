# Raspberry PI Photobooth

This program turns a Raspberry PI (any model) with a connected camera module and printer into a Photobooth. It will use the main display to show a live preview from the camera, and when a user presses F10 (or one of the other hot-keys) it will capture a jpg from the camera and print it out.

## Prequestities
    * sudo apt install python3-picamera
    * sudo pip3 install rpi-ws281x

There are environment variables you can set to control the LED strip:
    * LED_COUNT=144
    * LED_PIN=10

## Example shell command

    LED_COUNT=12 LED_PIN=23 pi-photobooth

## Keyboard Controls

While the program is running users can use the keyboard to type captions that will appear over the image. These captions will also appear on the printed image. Besides entering text for the caption the following hot-keys have been mapped:

    * F8, Ctrl-U: Clear the caption
    * Up/Down: Adjust contrast
    * Left/Right: Adjust brightness
    * F1/F2: Adjust sharpnesss
    * F3/F4: Adjust the grey level of the caption
    * F5: Cycle through image effects
    * F10, Page up, Page down: Print the current image on screen

## Printing

Photos will be printed using `lp -o fit-to-page`, which should work fine for most setups as long as CUPS knows how big the paper in your printer is. If you have more than one printer ensure that the default printer is the one you want to print to.

Printed images will be saved in the current working directory as `webcam-YYYMMDDHHMMSSS.jpg` and will not be cleaned up. If you plan to run this for an extended period you will need to find a way to clean those up periodically.

## Errata

The RGB strip support is not currently working.
