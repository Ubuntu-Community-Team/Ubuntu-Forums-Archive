---
title: "Video capture help."
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by adt41287 on 2007-05-23
I need some help capturing video. I have my video camera plugged into the A/V ports on the back of my Hauppauge Pvr-150 card  and i do not know how to go about capturing video from the camera. Thanks for you help in advance!

---

### Post by fenian on 2007-05-23
From a terminal run...

> cat /dev/video0 > ~/Desktop/test.mpg


Start playback from the video camera (you may have to do this before you run the coommand if so start playback hit pause run the command and resume playback).
This will save the output to the desktop with a filename of test.mpg change the path and filename to suit your needs.

---

### Post by adt41287 on 2007-05-23
i did so and it just recorded from my coaxial cable input.... any suggestions... i am going to try disconnecting the coaxial and try again

---

### Post by adt41287 on 2007-05-23
still nothing, looks like its still looking for coax input now just really fuzzy ("snowy") and indeed the video camera was playing

---

### Post by fenian on 2007-05-23
You can try to tell the card which inputs to use with ivtvctl,you need to install ivtv-utils...

> sudo apt-get install ivtv-utils


then run...

> sudo ivtvctl -v input=1,output=1

you may need to change the numbers to get the right input.

---

### Post by adt41287 on 2007-05-23
> **fenian said:**
> You can try to tell the card which inputs to use with ivtvctl,you need to install ivtv-utils...




then run...



you may need to change the numbers to get the right input.

will this screw anything up with MythTv?

---

### Post by fenian on 2007-05-23
I seem to have overlooked the obvious before trying ivtvctl try setting the tuner channel to 3 to read the camera input.Use this command...

> ivtv-tune -c 3 -d /dev/video0 

then run...

> cat /dev/video0 > ~/Desktop/test.mpg

---

