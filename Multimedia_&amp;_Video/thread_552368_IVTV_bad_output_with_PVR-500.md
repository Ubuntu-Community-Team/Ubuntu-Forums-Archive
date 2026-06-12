---
title: "IVTV bad output with PVR-500"
date: 2007-09-16
forum: Multimedia &amp; Video
---

### Post by kcleong on 2007-09-16
I'm having problems with the video output of my PVR-500, using the standard ivtv module. The output of /dev/video0 (and video1) looks like this:

[IMG]http://www.leong.nl/image/video_output.png[/IMG]

The dmesg ivtv part look fine:
[http://paste.ubuntu-nl.org/37606/](http://paste.ubuntu-nl.org/37606/)

When I'm writing a capture file with 'cat /dev/video1 > /tmp/test_capture.mpg' the following output shows up in dmesg:

[  301.628934] ivtv1: All encoder VBI stream buffers are full. Dropping data.
[  301.628940] ivtv1: Cause: the application is not reading fast enough.
[  313.871358] ivtv1 warning: CX2341X_ENC_GET_SEQ_END took 116 jiffies (250 per HZ)

I'm encountering this problem on Feisty. I'm sure the tv-card is okay, I tried it on a windows box where the card worked good. Anybody got a clue how I can fix this?

---

### Post by mad &amp;rei on 2007-09-16
Im just noob, but in line 24 it is  :
[   39.393378] tuner 0-0060: type set to 62 (Philips TEA5767HN FM Radio)
and ln line 60 is:
   50.845737] tuner 1-0061: type set to 73 (Samsung TCPG 6121P30A).
If you havent 2 tuners, than i think it is a problem in the settings of the tuner. That may be a cause. If no, sorry for bothering you.
Best regards., mad_&rei...:)

---

### Post by Laserboy on 2007-09-18
I have the exact same problem, but with only one of my 2 tuners.  I have a PVR-250 and a -150, and the problem only exists on the -150.  I've attached the IVTV part of dmesg.  I thought since I have a working card (the 250), someone might be able to check the IVTV part and see if any differences jump out that would provide a clue as to why one works and the other doesn't.

The errors in the messages file are similar to yours:

```
ivtv1 warning: CX2341X_ENC_MUTE_VIDEO took 124 jiffies (250 per HZ)
ivtv1 warning: encoder VBI: Couldn't find start of buffer within the first 256 bytes
ivtv1: All encoder VBI stream buffers are full. Dropping data.
ivtv1: Cause: the application is not reading fast enough.

```
Maybe it's a problem unique to the -150, since I think the -500 is just two -150s on the same card...

I recently upgraded my linux box from Fedora Core 3 to Fiesty, and afterwards, both cards worked for about a week.  *Then something happened.* I guess the trick now is trying to figure out just what that something was...

---

### Post by Laserboy on 2007-09-19
kcleong,
    I just found this, and plan on trying it tonight.  Maybe it will help you.

[http://www.gossamer-threads.com/lists/mythtv/users/283115#283115]("http://www.gossamer-threads.com/lists/mythtv/users/283115#283115")

---

### Post by Laserboy on 2007-09-22
> **Laserboy said:**
> kcleong,
    I just found this, and plan on trying it tonight.  Maybe it will help you.

[http://www.gossamer-threads.com/lists/mythtv/users/283115#283115]("http://www.gossamer-threads.com/lists/mythtv/users/283115#283115")

Well, that didn't fix the corrupt video.  This did: [http://ivtvdriver.org/index.php/Troubleshooting#VBI_.28CC_and_teletext.29_with_non_default_resolutions_can_cause_video_corruption]("http://ivtvdriver.org/index.php/Troubleshooting#VBI_.28CC_and_teletext.29_with_non_default_resolutions_can_cause_video_corruption")

---

