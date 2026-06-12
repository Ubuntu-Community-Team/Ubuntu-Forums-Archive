---
title: "Need &quot;dynamic&quot; slideshow with transitions"
date: 2008-08-31
forum: Multimedia Software
---

### Post by rsay on 2008-08-31
We are setting up a photobooth for a party that we are hosting. I am using a webcam with cheese to capture images to a directory on an NFS share. I'm displaying the images with a second computer attached to a large display. What is a good way to set up the second computer to do a continuous slideshow that will:

-Loop through the directory continuously.
-Display random transitions.
-Pick up new pictures as they are dropped into the directory.


I have found several programs that do 2 of 3.

EOG does the loop nicely and picks up new pictures but I can't figure out any transitions. So far this is my leading candidate.

GQView does the transitions but doesn't pick up new pictures that arrive in the directory after the slideshow has started

Feh also seems to only loop through the pictures that were in the directory when the command was run unless someone knows how to do a script that will let it reload the list and keep going.

---

### Post by rsay on 2008-09-02
I still haven't found a program that fills the bill. Right now the best solution that I have come up with is to attach my zaurus to my wife's digital picture frame. I can then send the pictures from my laptop in the photobooth to my zaurus with rsync and the picture frame displays the images with random transitions. The zaurus acts as a usb storage device.  I was hoping for a bigger display (the frame is only 8x10) but at least I have something working.

---

### Post by rsay on 2008-09-12
At the 11th hour, I found a program that worked great.The screensaver GLslideshow did just want I wanted. I had to install xscreensaver and then use the installed tool xscreensaver-demo to change the default picture directory to match my camera's picture directory. I then locked the screen and my slideshow started to play. A few people actually fiddled with my keyboard during the evening but the slideshow just restarted 60 seconds later. Panning, zooming, transitioning in the foreground while loading all the new pictures getting pushed to the display computer from the capture computer with rsync.

---

