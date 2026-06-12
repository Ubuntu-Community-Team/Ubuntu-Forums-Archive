---
title: "&quot;Ubuntu restricted drivers&quot; - where are they?"
date: 2008-04-09
forum: Multimedia &amp; Video
---

### Post by stig1965 on 2008-04-09
I have just decided to try this linux stuff out for myself, so I have just installed Ubuntu 8.04 a couple of hours ago (I took a chance, since this also allows me to see, if the update manager will let me install the final version in a few weeks).

Anyway, installation was a breeze (dual boot with XP), and everything seems to be working correctly. I was of course a bit surprised to find, that I was offered to install 436 updates almost imidiately - I guess that is what you get for installing a beta-version? After that, I decided to see for myself, if all the amazing stuff about Ubuntu I had heard was true.

The first thing was to install was my printer - a HP Lasercolorjet 2600. I plugged in onto my laptop (a Dell Inspiron 630m, by the way). After a few seconds a popup declared, that my printer was ready to print - so I decided to print a test-page - it was black-and-white, though. A quick look at the printing menu disclosed, that the default bw setting had to be changed to color - new testpage, now with colors, however, not sufficiently fine-grained. So I changed the default 1 bit per pane to 2 bits per pane - and now got a fine-grained print, however, now the color adjustment was not perfect. It is ok, though, but I will have to use my XP driver for high-quality prints. But thumbs up for the ease of installation - no fumbling around with the instalation CD.

Next I wanted to install all the restricted drivers one need. But I could not locate the "Ubuntu restricted drivers" package anywhere. So my question is - how do I get flash, multimedia codecs, w true type fonts, java and all those other things you need in this MS-world? I attempted to go to youtube, and the OS offered me to install Adobe Flash, which I chose - but youtube still claims I do not have Flash, allthough Firefox claims I have Flash installed, when I attempt to reinstall it - I guess that was not the way to go around it......

Who can tell me where to find the "Ubuntu restricted drivers" package in 8.04 - I couldn't find it in synaptic, and I couldn't find it in the other (smaller) add/remove program (that I don't know the name of). Anyone that can guide me?

---

### Post by pytheas22 on 2008-04-09
The restricted drivers package is installed by default, but it doesn't include all of the things you mentioned.  It most has non-free hardware drivers, and if you have any hardware that needs them (nvidia, ATI, Atheros) it should pop up a message to ask whether you want to enable them.

The firefox flash installation can be flaky.  Did you make sure you restarted firefox after doing the installation?  Are you using a 64-bit kernel?

You will be prompted to install multimedia codecs if you try to watch a video in Movie Player (aka totem) that uses a proprietary codec.  So this installation is easy.

As for Microsoft fonts, check out [http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/](http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/)

Please feel free to post if you need more help.  Also, keep in mind that you're using a non-stable release of Ubuntu, so things might be a little more frustrating than they'd be on a stable system.

---

### Post by wolfen69 on 2008-04-09
restricted drivers are in system>administration

---

### Post by stig1965 on 2008-04-10
OK -thanks to both of you. I ended up reinstalling, and then using a guide to "Ubuntu - the perfect desktop" to get all the things I wanted.

However, I had hoped to be able to install the reinstall "on top of" the old install, but the installer would not let me do that - at least I couldn't figure out how to do it :confused: So now I have a redundant swap partition and a 3 GB + ext partition with my "old" (well 1 day old)  install of ubuntu.

It seems like a good idea to do a new reinstall, before I use to much time on installing different programs - however, how do I delete the "old partions" first (I tried to delete in manual partitioning, but it would not let me delete the ext3 partition, for some reason)????

So do you know, what is the secret for wiping out the old installs, before I reinstall?

---

### Post by pytheas22 on 2008-04-10
If you choose manual partitioning in the installer, select the partition that you want to overwrite with the new system, and choose / as its mountpoint.  If this doesn't work, you can boot to the live CD and install gparted, a graphical partition editor, with the command:
```

sudo apt-get install gparted
```

and with gparted you can delete both of your existing Ubuntu partitions, and then run the installer again.  Make sure that you don't mount the Ubuntu partitions before trying to do this (i.e. don't try to access the files on your hard drive from the live CD), or it probably won't let you modify those partitions till they're unmounted.

By the way, I think gparted gets installed under Applications>System Tools, or you can just open a terminal and type "gparted" to run it.  It's a friendly, intuitive program.

---

### Post by stig1965 on 2008-04-10
Thank you so much - I will try to use gparted saturday, since it sounds like it fits my needs....

BTW I am quite impressed with the quality of many of the programs that are available....

---

