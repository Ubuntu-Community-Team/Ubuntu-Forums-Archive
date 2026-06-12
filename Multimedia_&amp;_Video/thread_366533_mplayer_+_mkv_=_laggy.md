---
title: "mplayer + mkv = laggy"
date: 2007-02-21
forum: Multimedia &amp; Video
---

### Post by suikula on 2007-02-21
hi

Im using edgy on my toshiba satellite laptop.. I have installed mplayer, ffmpeg and x264 from reposities, but when I start to play 720p mkv file the output is really laggy. I can play normal 720p avi without any lag or frame droppings...

Anyone else having these kind of problems ? Can someone help me ?

---

### Post by josesanders on 2007-02-22
I had the exact same problem on many different machines under both windows and linux with mkv files.  I just gave up and used Tovid to convert them to mpeg (it does take a while, unfortunately).  Now I just try to avoid mkv whenever possible.

---

### Post by shirilover on 2007-02-22
Do you have sufficient processing power to play 720p h.264 video?
This is the tradeoff of using h.264; it requires more processing power.
The media container, be it mkv or mp4, makes no difference.

---

### Post by suikula on 2007-03-01
> **shirilover said:**
> Do you have sufficient processing power to play 720p h.264 video?
This is the tradeoff of using h.264; it requires more processing power.
The media container, be it mkv or mp4, makes no difference.

i have :
t2400 duo core processor 
1gb 533mhz ddr
7900gs gp 256mb 

i think this should be enough. correct me if im wrong

---

### Post by suikula on 2007-03-02
this problem is solved.. 

problem wasnt the fact that my codecs are not up to date or my processor isnt fast enough..
problem was this..
[https://launchpad.net/ubuntu/+bug/22336](https://launchpad.net/ubuntu/+bug/22336)

well, after modding files
/proc/acpi/thermal_zone/THR0/trip_points
and
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
I got it working. Now temps does not raise too high and laptop stays stable..

thanks to everyone for answering to this thread.. sorry my bad english

---

### Post by shelbydz on 2007-04-15
where do you update your codecs? I'm having the same problem. I have a P4 3g, 1g ram, running Edgy Kubuntu. I have a few 720p mkv. if I play them from mplayer, vlc, kaffine or xine, they're choppy. A friend of mine has a 2.6g w/ only 512mb ram running XP playing the same vid files w/ CCCP and he says they're fine.  

What's going on?

thanks

**EDIT** I broke down and installed a dual boot on this computer w/ XP on the other partition. XP plays the same video files perfectly. So I know the problem isn't with my system. I think it's the codec we currently have for MKV files.

---

