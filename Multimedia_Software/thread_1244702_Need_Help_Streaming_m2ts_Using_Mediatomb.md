---
title: "Need Help Streaming m2ts Using Mediatomb"
date: 2009-08-19
forum: Multimedia Software
---

### Post by rchrdm on 2009-08-19
Alright so my Googling has gotten me no where with this one.  What I want to do is stream .m2ts video files to my PS3, really I'm just trying to copy them to the PS3 hard drive using mediatomb.  I want to use the m2ts container because of its support for files larger than 4gb, not sure why mp4 files larger then 4gb won't work on the PS, and for its support of ac3 audio.  The only fix that I found that was similar to this was editing the configuration file, mimetype and some other part, however this did not work for me.  Any help would be greatly appreciated.

---

### Post by rchrdm on 2009-08-23
b-b-b-bump

---

### Post by encore2097 on 2010-01-06
Also having the same problem,

adding 

<map from="m2ts" to="video/divx"/> or
<map from="m2ts" to="video/avc"/> or
<map from="m2ts" to="video/avchd"/> or
<map from="m2ts" to="video/divx"/> or
<map from="avi" to="video/avi"/> or
<map from="avi" to="video/mpeg"/>

to config.xml under  <mappings> <extension-mimetype ignore-unknown="no"> did not work.

Nothing shows up in the folder in the ps3 for the .m2ts file

---

### Post by encore2097 on 2010-01-06
Adding the follwoing to the same section under the avi map and a system reboot fixed the problem for me.
        <map from="vob" to="video/mpeg"/>
        <map from="m2ts" to="video/mpeg"/>
        <map from="ts" to="video/mpeg"/>

---

### Post by voidzero on 2010-02-02
Ok, even though this thread is 3 weeks old, I still just want to say thanks.

Thanks! :popcorn:

---

### Post by OSXniCKels on 2010-03-22
> **encore2097 said:**
> Adding the follwoing to the same section under the avi map and a system reboot fixed the problem for me.
        <map from="vob" to="video/mpeg"/>
        <map from="m2ts" to="video/mpeg"/>
        <map from="ts" to="video/mpeg"/>

I hope it's not too late to revive this thread.  I recently needed to accomplish the same thing.

I tried what the above quote suggests, did a system reboot, and still no cake...wierd...

Anyone else still having trouble with this?  Anyone else find a solution other than the above?

THANKS Linux Community!! :-)

--OSXniCKels

---

### Post by buntunoob on 2010-03-24
OSXniCKels that fix should have worked, but... I’d suggest that you make sure that the cfg you think you are using is the one that being used, I had a problem a while back and it turned out that it was looking for it in a different spot, and was using a generic one.
  Try starting it with #sudo mediatomb –f /etc/mediatomb/config.xml –D –l /var/log/mediatomb.log
  And with that your cfg should be in /etc/mediatomb/… or where you expect it and change above as needed
  The –f tells it where to get the Cfg from, -D is debug and the –l is where the logs are kept and why the sudo.
  At the top of the log since debug is on you should see part of your cfg.
  I’m doing this from work so please forgive me if I forgot anything.

---

### Post by OSXniCKels on 2010-03-25
Thanks Buntunoob...I'll give this a shot.  I should have thought to try to specify an explicit config file...I'll reply with my results as soon as I get a chance to try it.

Funny thing is, now that I have streaming setup (for the most part) I haven't had much time to watch anything!  Oh well.  Thank you!

---

### Post by OSXniCKels on 2010-03-26
> **OSXniCKels said:**
> Thanks Buntunoob...I'll give this a shot.  I should have thought to try to specify an explicit config file...I'll reply with my results as soon as I get a chance to try it.

Funny thing is, now that I have streaming setup (for the most part) I haven't had much time to watch anything!  Oh well.  Thank you!


Okay, so I got to it, and got it working!  Looking at some debug output, it was looking at ~/.mediatomb/config.xml where I only was editing /etc/mediatomb/config.xml so I copied the former to the latter and VIOLA!

---

### Post by OSXniCKels on 2010-05-18
I've been using MediaTomb successfully now for a few months and I love it!

For those of you who are Mac users - I use a Macbook Pro for my everyday machine, have an Ubuntu 9.10 Server install at home for my website and other things, and Windows 7 x64 via Boot Camp when I need to.

Until now I've been using mkv2vob to convert MKV's to M2TS but mkv2vob is a Windows-only app.  Recently, I found an app for the Mac that works just as well.

mkvtools found here: [http://www.emmgunn.com/mokgvm2dvd/mokgvmhome.html](http://www.emmgunn.com/mokgvm2dvd/mokgvmhome.html) will transcode or remux depending on your needs.  You can choose to output an AVI or an MP4 file.

For my PS3, I chose MP4, and for example I have an MKV that has a video channel of AVCHD/H264 and an audio channel of DTS.  Since I don't have a DTS decoder sound system, I need to transcode the audio.

So I chose the passthru setting for video and aac for audio.  The file is processed fairly quickly as it doesn't need to re-encode the video since it is a format the PS3 can play already.

Anyway, just wanted to share this for any Mac users that may come across this post.

--OSXniCKels

---

### Post by nastysquar3d on 2010-05-22
I can't seem to get this working. I'm running mediatomb as a daemon on a Ubuntu headless server. I edited my config file to include the lines mentioned. I confirmed that it is the right config file by checking the mediatomb log.

2010-05-22 08:26:33    INFO: Loading configuration from: /etc/mediatomb/config.xml

Yet, the m2ts files refuse to show up on my PS3.

I'm running Ubuntu 10.04 LTS 64bit server and mediatomb 0.12.0

---

### Post by kev77 on 2010-05-22
i use pms-linux seems to be more friendly than mediatomb [http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=5589]("http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=5589")

---

### Post by banff2010 on 2010-06-21
Anyone tried this solution with ubuntu 10.04 
[mkv to m2ts?]("http://sticky123.blogspot.com/2008/03/remuxing-mkv-to-m2ts-on-linux.html")

---

