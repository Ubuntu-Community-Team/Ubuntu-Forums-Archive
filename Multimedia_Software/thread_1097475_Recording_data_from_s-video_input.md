---
title: "Recording data from s-video input"
date: 2009-03-16
forum: Multimedia Software
---

### Post by davidbilla on 2009-03-16
Hi,

I need to record data given to the s-video input of a TV tuner card. Which program should I use for recording from s-video input? There are a lot of programs like ffmpeg, mencoder etc., but I would appreciate an example, since I haven't been able to figure a way to choose s-video as the input source yet.

---

### Post by mocha on 2009-03-16
I would really recommend MythTV.  It does everything you want with TV and DVB cards.  It's fairly easy to install in Ubuntu, just check out the official documentation.  You might think at first that it's bulky or too much for your uses, but after you get used to it you realize that you were really missing out.

---

### Post by davidbilla on 2009-03-16
Thanks. But as I understand it, MythTV is too much for my needs, I think. All I want to do is this.

I'll give my S-video input to the TV tuner card. And I need a simple command to record whatever is available from S-Video in raw format. Then I'll convert it and check whether I've managed to record whatever I see in tvtime's screen. That's it. Once this is made sure of, I'll be writing my own code to communicate with the driver to collect and dump the raw data to a file.

Any ideas?

---

### Post by lovinglinux on 2009-03-16
> **davidbilla said:**
> Thanks. But as I understand it, MythTV is too much for my needs, I think. All I want to do is this.

I'll give my S-video input to the TV tuner card. And I need a simple command to record whatever is available from S-Video in raw format. Then I'll convert it and check whether I've managed to record whatever I see in tvtime's screen. That's it. Once this is made sure of, I'll be writing my own code to communicate with the driver to collect and dump the raw data to a file.

Any ideas?

There is an extension for Firefox that I'm developing, [FoxMediaCenter]("http://fmc.isgreat.org/"), that can record from S-video. It is a lightweight alternative, but with some interesting features. The PVR uses transcode to record the TV input and a channel for S-video is already included (it is named S-VHS by mistake).

You can record on-the-fly, schedule recordings, record weekly shows automatically and schedule recordings based on xmltv programme.

---

### Post by davidbilla on 2009-03-16
Thanks. I'll try it out and reply tomorrow.

---

### Post by davidbilla on 2009-03-17
Hi, thanks a lot. I was able to record from SVHS input. I presume you pass the recording time and the input channel to transcode as parameters; if not, correct me! This would be great for watching and recording TV but that's not what I'm going to do. I need to know how to choose SVHS as input in transcode and I want to record it in raw format. Any ideas?

---

### Post by lovinglinux on 2009-03-17
> **davidbilla said:**
> Hi, thanks a lot. I was able to record from SVHS input. I presume you pass the recording time and the input channel to transcode as parameters; if not, correct me!

Yes, that's correct.

> **davidbilla said:**
> This would be great for watching and recording TV but that's not what I'm going to do. I need to know how to choose SVHS as input in transcode and I want to record it in raw format. Any ideas?

Open the PVR tool in the extension, select the "Settings" tab, then replace the part of the transcode command which contains "-y ffmpeg -F mjpeg" with "-y dvraw". I guess this will do what you want. It will be recorded with avi extension, but that doesn't matter, just rename the file if you need to.

---

### Post by shane2peru on 2009-05-28
> **mocha said:**
> I would really recommend MythTV.  It does everything you want with TV and DVB cards.  It's fairly easy to install in Ubuntu, just check out the official documentation.  You might think at first that it's bulky or too much for your uses, but after you get used to it you realize that you were really missing out.

I installed mythtv and got it all setup and working, at least I can see what is being played by my camcorder through the rca jack (I don't think it is picking up the sound though).  However I can't figure out how to record with it.  Also, I have seen a lot of times:  cat /dev/video0 > file.mpg  when I do that it creates a very large file.mpg, however when I play it with vlc there is not video, no sound nothing.  It is a big empty file.  Any help on this would greatly be appreciated.  

Shane

PS  I'm using a K-World lite PCI PVR-TV 7134SE card, configured correctly.  I can see what is being played through tvtime and can even hear the sound when I run some command aplay or something, it escapes me at the moment.  Any help on this would greatly be appreciated.

---

