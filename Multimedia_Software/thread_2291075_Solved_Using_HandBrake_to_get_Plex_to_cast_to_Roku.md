---
title: "Solved: Using HandBrake to get Plex to cast to Roku full screen using RarFlix"
date: 2015-08-17
forum: Multimedia Software
---

### Post by Finston on 2015-08-17
There seem to be a lot of people in chat rooms who do not like video being displayed in their HD TV's with black lines letter boxing their actual video content. 

I had the same issue when casting video content to my HD TV from my Ubuntu 14.04 laptop using Plex Media Manager to cast to my Roku 2 box running RarFlix.

There was a lot of confusing technical jargon but no one explained, in simple terms, how Handbrake 0.10.2 can help solve my issue. Hand Brake seems to be mainly set up to get content to play on apple and android devices without black lines. Nowhere is this explained - like a lot of Linux - I guess you are expected to know this already.

The answer seems surprisingly simple, once I found it.

Once you have your video in .mp4 format, play it in VLC to see if it displays full screen or letter boxed by black lines. To do this select full screen (assuming your Screen is 16:9 format). If letterbox lines show, do the following:

Run HandBrake 0.10.2. Select file/preferences/general and untick the "use i-pod/i-tunes friendly .m4v file extension for MP4" box. Select "source". Navigate and select the guilty file. I normally insert "1" in the destination file name, before the .mp4, so as not to overwrite the original file (In case I get it wrong). 

HandBrake automatically starts in Autocrop mode in the Summary tab (The line of tabs 1/3 of the way down the screen). This automatically crops the file to a vertical number of pixels which represents the actual picture (i.e. deletes the pixels top and bottom which are the black lines).

Select the Picture tab (next to the Summary tab) and select loose crop. Click on auto crop box to clear it, if it stays selected. Get hold of a handheld calculator divide 16 by 9 and store the result (~1.77). Multiply the vertical number of pixels (The second number y in crop dimensions x x y) by the 1.77 result. This becomes the target number of x axis pixels (horizontal) to give a 16:9 full screen output.

Nearly there!
 
Subtract the target number of x axis pixels from the number x presently shown in x x y. Divide this remaining number by two. The result is the number of pixels that need removing from either side to give a full screen 16:9 display.

You remove the pixels by selecting the + of the -+ on either side of the Cropping display (The one which already shows the amount cropped from top and bottom).

If you don't like the maths, crop away equally from both sides and watch the display aspect ratio under Display Geometry. When it gets as near to  16:9 as possible, your're there. HandBrake makes all the necessary adjustments to pixel aspect ratio automatically - clever. The pixels are decreased in 2;s by the way.

Finally press start and your freshly produced full screen production is under way and will be placed next to your original file, when complete.

---

### Post by chris405 on 2015-08-18
So this is if you don't want to use the Roku Plex channel?

---

