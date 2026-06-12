---
title: "XBMC streaming to XBOX360"
date: 2009-12-22
forum: Multimedia Software
---

### Post by RaFast on 2009-12-22
Hi all,
 
I have recently moved from Windows and installed Ubuntu 9.10. I would like to stream audio and video from PC to the Xbox360 I have in the living room.
 
Previously I made this streaming with TVersity (win WinXP) and it was something like plug-and-play but currently with Ubuntu and XBMC is not so easy. In fact my Xbox360 does not connect with the XBMC in the PC.
 
I have tried with the last version of XBMC (9.10) but nothing changes. It is something strange as XBMC do detects other PCs in the same WiFi network but there is no communication between XBMC and Xbox360. TwonkyMedia works well but the licence expires in a month. Ushare is also OK but is difficult to configure and does not transcode video.
 
I think it is a matter of configuration in XBMC but I do not know where. Samba perhaps?
 
Can someone help me to correctly configure XBMC to stream audio and video to Xbox360?
 
Regards

---

### Post by eddyojb on 2010-03-30
bump -ing this thread, I'm in the same boat as you

---

### Post by Sir Rodness on 2010-04-01
Hello,

Took me a bit to figure it out too, but I got it partially working in Ubuntu 9.10 Karmic. These instructions are assuming you have your libraries and sources already set up in XBMC and using the latest version found using the PPA in Ubuntu Tweak.

In XBMC go to **System->Network->Services**
Once there make sure make sure **share video and music libraries through UPnP** selected. This should initialise the media server.

Note: I also have samba install, but I'm not sure if its required for the uPnP feature to work for the Media Server.

Now to my xbox360 I go to my Video Library and in the list I could now see **XBMC Media Server**. Select that and I'm able to see my videos and play them. Which is great. However, when I went to try out my music I can see the Media Server, but it will not show my music for playback. If anyone has some insight into that I would appreciate it.

---

### Post by celticninja on 2010-05-24
--Bump--

I am having the same music problems, I can get videos to stream but not music. keep getting an error message on the xbox 360.

---

### Post by Predatorian on 2011-01-10
I installed XBMC according to this

[http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide]("http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide")\

and it installed, i was able to set up the libraries, and enable UnPnP like it says up top here, but i am still not able to see my XBMC server. my Xbox 360 Dashboard version is 2.0.12611.0 as of January 5th, 2011. would this be a problem, or am i not configuring xbmc correctly?

---

