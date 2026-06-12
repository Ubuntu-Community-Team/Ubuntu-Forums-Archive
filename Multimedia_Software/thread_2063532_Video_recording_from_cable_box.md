---
title: "Video recording from cable box"
date: 2012-09-27
forum: Multimedia Software
---

### Post by hitime on 2012-09-27
Hey all,

Overall goal is record SD (HD if possible) from a cable box.

Details: Ubuntu 64bit, in US, Time Warner (clear Qam going away 10/11/2012) Ubuntu 12.04, have analog cable / digital OTA Pinnacle 800e tuner

What I've tried so far is getting analog recordings from xawtv, streamer and mplayer with limited success.  xawtv is the only one that will play with sound when used in conjunction with padsp but the record options always seem to freeze the application. The other two options can bring up video, but no audio even when used with padsp (hw:2,0 should be the device for mplayer).  Weird thing about streamer is the video is inverted also.

Over the air, not much of a problem there since really any DVB capable program seems to work fine on the digital side.

I've seen external devices from SiliconDust, Happuage and others they may do the trick, but the price tag seems to be around $100 or north of that.  If I'm only going to record from the box and will have that do the tuning, paying that much does not seem reasonable unless I drop $150 or so and go with a cable card device.  I would prefer to just pickup some cheap device to do the job.

Anyone have suggestions on how to fix the device I'm using or another low cost option I can pickup and implement into my setup?

Thanks,
hitime

---

### Post by mocha on 2012-09-28
Sounds like you need to do some homework.  MythTV might work the easiest for you.  If you want to use the command line then v4l2-ctl might be able to control the low level options of your card, then you just use something like cat /dev/video0 > output.mpg Or if your card shows up as a DVB adapter then you can generate a channels.conf for mplayer and use mplayer -tskeepbroken -dumpfile output.ts -dumpstream dvb://1@xxxx to record.

---

### Post by hitime on 2012-09-28
> **mocha said:**
> Sounds like you need to do some homework.  MythTV might work the easiest for you.  If you want to use the command line then v4l2-ctl might be able to control the low level options of your card, then you just use something like cat /dev/video0 > output.mpg Or if your card shows up as a DVB adapter then you can generate a channels.conf for mplayer and use mplayer -tskeepbroken -dumpfile output.ts -dumpstream dvb://1@xxxx to record.

The card shows up as a dvb device for broadcast only which is not quite what I'm looking for as in the initial post.  I'll go through and revisit v4l2-ctl, but it does seem odd that padsp will only function with xawtv, maybe I'm missing a switch.  If I can just cat /dev/video0 to a file and get video/audio that's more then fine with me since I can set cron jobs as a dvr then script it with handbrake to do the conversion.  I'll give it a shot when I get home.

hitime

---

