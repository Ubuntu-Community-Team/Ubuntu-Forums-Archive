---
title: "Mythbuntu 9.10 and Hauppauge Nova T-500"
date: 2009-10-30
forum: Mythbuntu
---

### Post by utar on 2009-10-30
I'm going to upgrade (or more likely reinstall) my 8.04 install to 9.10 in the near future.

Just wondering if anyone can give me comments on if the Nova T-500 works okay?  I'm just asking because I've seen a number of posts suggesting that it's broken on later kernels and I wanted to check that it will work on 9.10 before I install.

[Edit: I also have a Tevii S650 USB which is somewhat less common then the Nova but works very well on 8.04 (after I updated the V4L drivers).  If anyone has any experience of using this on 9.10 I would appreciate a comment]


Cheers


Utar

---

### Post by SiHa on 2009-10-30
I'm going to be doing just this over the weekend, so I'll report back.

---

### Post by AJ1000 on 2009-10-30
The Nova T 500 works well for me. I found it is best not to do the Myth Tv setup as part of the installation prcess, but instead do it after the installation.

This is the extra stuff I had to do before doing MythTv-setup:

1) sudo apt get dvbstream
2) Make options.conf file
3) do dmesg|grep -i dvb (and check the nova t 500 is in warm state)
4) now run mythtv-setup

I have done both the upgrade and a clean install and I can report that the clean install is better as it is a lot faster than the upgraded version. I am very impressed with Ext4 and the performance improvements in 9.10.

I have had a lot of the problems that already that occur with the nova t 500. So if you have an issue then just post it on the forum and it can be solved.

Another thing I did which was impressed me about Ubuntu 9.10 is that I got meTv and kaffeine to work on the seperate tuners, so I can now watch two programs at the same time.

The only thing that did not work with the nova t 500 for me was Totem.

Any questions, please ask, I will monitor the forum and try to provide answers. Please put nova t 500 in the subject.

---

### Post by utar on 2009-10-30
SiHa / AJ1000


Thanks for the replies.

From my googling I'm pretty sure the Nova will work fine, but I know from experience just how awkward the card can be even if you set all the options in the way the card likes, so I want to make sure.  At the moment on my 8.04 system it falls over after a warm reboot!

The Tevii on the other hand just works . . .



Utar

---

### Post by SiHa on 2009-10-30
[QUOTE=utar]At the moment on my 8.04 system it falls over after a warm reboot![/QUOTE]
Strange, I've had mine rock-solid on my 8.04 system for 18 months.

Anyway, I've just installed 9.10, I'll leave it running overnight and see if the dreaded I2C errors show up.

---

### Post by utar on 2009-10-30
> **SiHa said:**
> Strange, I've had mine rock-solid on my 8.04 system for 18 months.

Anyway, I've just installed 9.10, I'll leave it running overnight and see if the dreaded I2C errors show up.

Well to be fair I only gave half an answer.  The Nova was solid on 8.04 (well it was after I changed several Myth options) but it got awkward again when I installed the latest V4L drivers (at that time) so that the Tevii would work.

Anyway let me know how you go, those I2C errors are the ones i'm dreading too.



Utar

---

### Post by SiHa on 2009-10-31
Ah, I see.

Seems OK overnight...

---

### Post by utar on 2009-10-31
Thanks SiHa.


Utar

---

### Post by tonycollinet on 2009-10-31
I've just upgraded from 9.04

I have been getting some i2c errors on 9.04, but not in the last 2 weeks.

So far no problems with 9.10, but it is early days yet.

---

### Post by xyphias on 2009-11-11
I have a Nova T-500 on my Ubuntu 9.10 upgrade and all seems to be running fine except for the remote control. All was fine on 9.04 but the upgrade will not allow the remote to work in MythTV. When I run irw it shows all the correct key presses but MythTV does nothing with them.  Am I missing something in the new setup?  Any help very much appreciated.

---

### Post by byronmyth on 2009-11-12
Hi. I'm running the NOVA-T, my re-install went to pot (I'm new to this Linux stuff) but the fresh install to 9.10 was quite smooth, just had to change the firmware for the NOVA-HS-S2 which doesn't work out of the box.

---

### Post by utar on 2009-11-12
Well I thought I would update this thread on my progress.

I installed at the weekend and have had zero I2C errors or tuner drop outs, although I don't leave my media centre on 24 hours a day.

Hopefully it won't fall over now that I have made this post!


Utar

---

### Post by Kencho on 2009-11-13
This card sounds good. I've had a lot of issues with HVR-1100 (and some haven't been fixed yet), so I'm considering to switch to this model. I just have a question: Do the IR remote control work fine in Karmic with this card? This is the most crucial part to me, as this box will be used by 50+ years-old people that aren't too familiar with computer keyboards, so the RC is the only "accessible" medium.

Thanks in advance!

---

### Post by anton610 on 2009-11-13
Hello,

I'm new here, and this is my first post, and it is a problem with my mythbuntu. sry

I've the nova-t 500 with karmic

rhe remote works, but when i trie to strat the pc without keyboard and mouse, the remote dont work.

does anyone have similar problems, and solved it?
the search spits nothing out.

what logs do i need to paste here?

sry for my bad english

Thanks Anton

---

### Post by Kencho on 2009-11-13
Can't help much here, but sounds like you've hard-coded the /dev/input/eventX file. So there will be gaps in the sequence (the mouse and keyboard event files). Can you post the result of this command?
```
cat /proc/bus/input/devices
```
That probably will be helpful.

And thanks for letting me know the remote works :)

---

### Post by tonycollinet on 2009-11-13
Follow the steps related to the remote control here.
[http://ubuntuforums.org/showthread.php?t=1140411&highlight=nova+t+500+remote](http://ubuntuforums.org/showthread.php?t=1140411&highlight=nova+t+500+remote)

---

### Post by anton610 on 2009-11-15
Thanks!

---

