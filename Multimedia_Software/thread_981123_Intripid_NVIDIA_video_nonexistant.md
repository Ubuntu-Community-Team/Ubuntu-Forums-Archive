---
title: "Intripid NVIDIA video nonexistant?"
date: 2008-11-13
forum: Multimedia Software
---

### Post by grenadier32 on 2008-11-13
So I've got a brand new Dell XPS M1530 machine here, and it's running Intrepid just fine. But video is still being stupid. Problems:

* The webcam doesn't work--Cheese displays a completely blank video screen, even though the webcam itself turns on and blinks just fine.
* DVD video is screwed up, even with all the libraries installed--I get errors in both totem-xine and totem-gstreamer, and VLC keeps has video that keeps blinking and even then doesn't display things right.
* Some videos that play, but not all, are bluish tinted when they shouldn't be. Both VLC and Totem do this.

I have all the Medibuntu stuff installed, including libdvdcss2 and w32codecs. libdvdcss2 doesn't seem to be cooperating in spite of being installed and present. Regionset has been done, my DVD region is set correctly. I can't figure out what's working wrong. Since this seems to be persistent across all videos except .flv and Youtube, I have a feeling it has something to do with NVIDIA drivers.

Anyone know anything about this that might help?

---

### Post by vanquishedangel on 2008-11-22
I hope this is not too late but I have been tirelessly looking to get my webcam to work in ubuntu intrepid 8.10 to the point of pulling my hair out but I didn't give up and if this doesn't help you then maybe it will help someone like me but I found this on another web page and compiled it from others and it worked like a dream, I will copy and paste the article

The only way I have managed to make totem show the videos was to set the output on the video tab of gstreamer-properties to "X Window System (No Xv)".

How to change the properties in gstreamer: press alt, f2. Then type gstreamer-properties, then go to the video tab and under default imput change the plugin to "x window system ( no xv)" Now start cheese.

---

### Post by grenadier32 on 2008-11-22
Cheese still crashes, unfortunately, even though the Test button in gstreamer-properties works just fine with those settings...I don't suppose it has anything to do with Compiz running?

---

