---
title: "PV-350 blurry after update"
date: 2008-04-17
forum: Mythbuntu
---

### Post by u4ea4me on 2008-04-17
I just updated my mythbuntu 7.10 and while watching live TV or recorded shows it is slightly blurry (the OSD is blurry too.) I have a PVR-350 and I use X forwarding to get it to the TV.
I noticed ivtv driver was updated last month and would that help...?
The frontend is fine and even watching videos through the Video app looks good.
Thanks in advance.

---

### Post by elj4176 on 2008-04-17
I just upgraded to 8.04 and i noticed the same thing but on the FE (don't watch on the BE much). I also have a pvr-350. I've tried changing the playback options but I don't really know what I'm doing in there. I am now using the Default HIGH QUALITY settings and it seems to be better but not much. The same FE was not blurry before the update. I have also tried with compiz on/off on the FE with no change in blurriness.
Anyone know what the fix is?

---

### Post by gazer22 on 2008-04-17
Hmm,  I've also had recent issues with my -350, but I can't blame MythTV...  

For debugging, I've found it useful to use the following:
```
ivtv-tune -c 9
cat /dev/video0 > /tmp/video_test.mpg
(Ctrl-c to exit)
```

(The number following -c is a channel number, so make sure it's one that you get!)

This will create a .mpg file which you can view in mplayer or xine or whatever.

If this file looks good, you've eliminated ivtv and PVR-350 issues from your problem area.  (If it's not good, it's not a MythTV issue...)

> **u4ea4me said:**
> I have a PVR-350 and I use X forwarding to get it to the TV.
-> Does that mean that you're using the Video-out of the -350?

---

### Post by u4ea4me on 2008-04-17
Thanks for jumping this.

I'll try that gazer22 suggests tonight.

I should clarify my previous post:
When I mentioned the ivtv driver being updated I ment that my driver is at an older (7.10 release) level, but I noticed last month they have a new driver and would that clear up this problem (pun intended.)

Also, when I pause the playback from live tv or recorded show the image and OSD clear up nicely but playing again makes the images look out of focus.

I'm thinking of 'upgrading' from the original install disk too.

Thanks again and I should post my test result tonight.

---

### Post by RobJohnston on 2008-04-17
Hi chaps, you might find it's a deinterlace problem.

Check this post for info:
[http://ubuntuforums.org/showthread.php?t=723345](http://ubuntuforums.org/showthread.php?t=723345)

Good luck, Rob.

---

### Post by gazer22 on 2008-04-17
> **u4ea4me said:**
> When I mentioned the ivtv driver being updated I ment that my driver is at an older (7.10 release) level, but I noticed last month they have a new driver and would that clear up this problem (pun intended.)

From what I can tell, the core ivtv stuff is now embedded in the kernel, which means upgrading the kernel to get upgraded ivtv.

Exceptions are the utilities and using the -350's TV-out capability.

If you are using the -350's TV-out, hook a monitor and see if there are any issues there.  Again, if there aren't, you can focus on trouble shooting the playback side, and not worry about the recording side, or vice-versa.

If recording is good, but the blurriness is only on the -350 TV-out, and not on an external monitor, you can troubleshoot that aspect.

If the recording is fine, and playback via MythTV on an attached monitor is blurry - then you can focus on your playback settings and the like.

Good luck!

---

### Post by u4ea4me on 2008-04-17
OK. I pulled the link above suggested by a kind soul above:
[http://www.uluga.ubuntuforums.org/showthread.php?t=723345](http://www.uluga.ubuntuforums.org/showthread.php?t=723345)

and tried one of the suggestions:
Settings -> TV Settings -> Reproduction -> third page (named Playback profiles)

which I couldn't find on my myth (really I have no 'Reproduction' option), but on that thread there was:
...the default playback profile was CPU+, now I will try "normal".

which I ran w/ like a Pink Floydian dog under Utils/Setup -> Setup -> TV Settings -> Playback -> screen 3/9 ' Current Video Playback Profile and I changed it from "CPU+" to "High Quaility"

and... it flippin' fixed the blurry playback.

Thanks to all for the help,
T

---

### Post by elj4176 on 2008-04-18
De-interlace made it worse for me since I'm watching primarily on my laptop. This is a different type of blurry that the deinterlace causes. I'll take a screenshot alter tonight and post it.

Havent had the time to go through the steps above to see if it is my card or the new myth settings. I kinda doubt it is the card since it wasn't blurry in 7.10 but who knows.

---

