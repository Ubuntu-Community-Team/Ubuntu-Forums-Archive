---
title: "Weird color misalignment with avi in VLC"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by gitpik on 2008-03-06
So as in the image below the color is misaligned. It only happens in VLC and only with some .avi, others work fine and the files in question do work properly in Mplayer. I have already installed the w32codecs from medibuntu and some others too but i can't remember them all right now. Any help would be greatly appreciated. I'm running Gutsy with ATI x1950 if it makes a difference. :confused:

---

### Post by gitpik on 2008-03-09
I've also found an mkv that has the same problem. Anybody have any ideas? If I've posted this in the wrong place could somebody point me in the right direction?

---

### Post by gardener on 2008-03-11
I'm having the same problem after upgrading to hardy heron. It happens with all my videos, in all my players, with both backends.

---

### Post by gitpik on 2008-03-13
So I've searched and searched and then I did some more searching. I can't find an answer to this anywhere. Not on this website, google, the videolan forums anywhere. I even tried IRC but no luck there. I'll try that again later today I guess. Can anybody help please?](*,)

> I'm having the same problem after upgrading to hardy heron. It happens with all my videos, in all my players, with both backends.

Sorry I can't be of any help to you gardener I haven't made the jump yet to Hardy. Still trying to work out all the kinks with my system and Gutsy.

---

### Post by pink_fone on 2008-04-25
this goes for me too. I dont know what happen.  it's driving me nuts :(

---

### Post by haletd on 2008-04-25
I just upgraded to hardy on both my computers I am having this problem with one of them.  Any ideas?

---

### Post by haletd on 2008-04-27
Well, after some searching i found a fix:

launch gstreamer-properties from terminal
change the video output plugin to custom
change the video output pipeline to:

ffmpegcolorspace ! video/x-raw-yuv,format=(fourcc)YV12 ! xvimagesink

Bug in the proprietary drivers that swaps the U and V planes.
The IY12 and I420 formats are identical except that the U and V planes are swapped, so we swap the swap


worked for me!

[https://answers.launchpad.net/ubuntu/+source/totem/+question/7373](https://answers.launchpad.net/ubuntu/+source/totem/+question/7373)

---

