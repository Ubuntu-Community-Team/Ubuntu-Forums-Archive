---
title: "MYTHTV Hauppauge PVR 350 HELP PLEASE"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by raptorman on 2007-10-20
Hello and thanks for any help.

My system is a 1 ghz Intel 865 board 1 gig memory running Ubuntu 7.10 and myth TV. I get the picture on my monitor fine but never have been able to get it on the TV. Have read many posts about 
PVR-350 output users need to enable use of the 350's decoder. In MythTV go into:

Settings &#8594; TV Settings &#8594; Playback

and go to the

"Use PVR-350 Output" screen. Check the box, and make sure it reads /dev/video16.

When I make these changes I get unable to initialize video error.

When I run this test /sbin/rmmod saa7127
/sbin/modprobe saa7127 test_image=1

I get verticle lines on the TV 

It looks like the output is going to the TV but not from within Myth

Any help is greatly appreciated.

---

### Post by raptorman on 2007-11-12
ttt

---

### Post by superm1 on 2007-11-19
Please reference this thread:

[http://ubuntuforums.org/showthread.php?t=615070](http://ubuntuforums.org/showthread.php?t=615070)

It has a ppa listed in it that has a newer version of mythtv with a fix for this exact issue.

---

