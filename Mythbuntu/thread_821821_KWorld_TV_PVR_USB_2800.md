---
title: "KWorld TV PVR USB 2800"
date: 2008-06-07
forum: Mythbuntu
---

### Post by kayvee on 2008-06-07
I am an absolute beginner and decided to install Mythbuntu on a spare computer to connect it to my TV. I use that system just to access my videos, music and photos from my home server. I did not have any TV tuner cards at the time of installation. 

Recently, somebody gave me a cheap USB TV Tuner card. It is a KWorld TV PVR USB 2800. From what I understand from the user manual, I can use it to record TV programs and all that. It also came with a remote control. Now my problem is to get it to work. As I mentioned earlier, I am an absolute beginner. I connected the said device to my computer but I don't really know what to do next. Any help would be highly appreciated....

---

### Post by swingboy3 on 2008-08-21
I'm pretty new too, but I've had some luck with the Kworld 2800.  I still don't have it working but here is what I've got.  

This uses the em28xx driver.  Spcecifically it is the em2820.  This is readily available.

>sudo apt-get install mercurial
Or instructions available at 
[https://wiki.ubuntu.com/em28xx](https://wiki.ubuntu.com/em28xx)

There are at least 12 cards that this driver supports and you have to make sure how to select #12 for the Kworld 2800 RF.  You can see this if you type dmesg and scrolling and looking for the em28xx driver modules.  I have only been able to get this to work during a single session by typing:

>sudo em28xx card=12

This can be configured long term in some config file that I have not found yet.

---

