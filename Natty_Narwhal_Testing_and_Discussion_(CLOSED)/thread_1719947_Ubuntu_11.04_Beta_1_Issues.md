---
title: "Ubuntu 11.04 Beta 1 Issues"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by doppel.ganger on 2011-04-02
I recently downloaded Ubuntu 11.04 Natty Desktop Beta 1 onto my Ubuntu 10.10 machine and used the Startup Disk Creator to put the ISO onto a 16GB flash drive. When I booted up from the flash drive, I noticed the Unity was missing, replaced with a little Ubuntu logo that leads to a drop-down menu. There were also several graphics errors. On the top panel in the notification area, the text was slightly repeated in a small line below. I assumed these were Live Image issues, so I went ahead and installed 11.04. The problems still persisted. **_I have since reverted back to 10.10._**
My desktop is a Dell Dimension 8110 with a Celeron CPU. Will someone also tell where the 'About' area is so I can find out about my graphics card? This computer was given to me by my uncle...

---

### Post by fooman on 2011-04-02
> **doppel.ganger said:**
> I recently downloaded Ubuntu 11.04 Natty Desktop Beta 1 onto my Ubuntu 10.10 machine and used the Startup Disk Creator to put the ISO onto a 16GB flash drive. When I booted up from the flash drive, I noticed the Unity was missing, replaced with a little Ubuntu logo that leads to a drop-down menu. There were also several graphics errors. On the top panel in the notification area, the text was slightly repeated in a small line below. I assumed these were Live Image issues, so I went ahead and installed 11.04. The problems still persisted. **_I have since reverted back to 10.10._**
My desktop is a Dell Dimension 8110 with a Celeron CPU. Will someone also tell where the 'About' area is so I can find out about my graphics card? This computer was given to me by my uncle...

when i first installed 11.04 on one of my spare drives...i also had only the icon in the top left and no unity.  after installing my video drivers (nvidia) and rebooting....unity was alive and well!

see if you have video drivers waiting to be installed....go to: system > administration > additional drivers

when it opens,  look to see if there are drivers listed for your video card,  if so...click on one,  then click "enable"

hope that helps.

---

### Post by fabricator4 on 2011-04-02
> **doppel.ganger said:**
> I recently downloaded Ubuntu 11.04 Natty Desktop Beta 1 onto my Ubuntu 10.10 machine and used the Startup Disk Creator to put the ISO onto a 16GB flash drive.

11.04 is a _beta_  of course there will be issues. Discussions about Natty should be done over on Testing/Development: Natty Narwhal.

You should also have run update manager and got the latest updates.  You might have found that the problems were resolved. It's rock solid over here after the updates, but flakey before.

Lastly you should have reported any bugs that still existed to Launchpad - the developers (hardly) never read these forums.

Chris.

---

### Post by doppel.ganger on 2011-04-02
I am in 11.04 live. the drivers say: "No proprietary drivers are in use on this system." I tried the flash drive on my teacher's computer (with his permission) and Unity worked like a charm.

---

### Post by Perfect Storm on 2011-04-02
Moved to Development & Testing Discussion forum.

---

### Post by doppel.ganger on 2011-04-02
Thanks, but would somebody please HELP me?!?!?

---

### Post by fooman on 2011-04-02
see what video card you have....open a terminal and type:

```
lspci
```

press enter....your video card will be listed in there.  probably around the middle next to: vga compatible controller

---

### Post by doppel.ganger on 2011-04-02
Decipher this, please:

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

---

### Post by doppel.ganger on 2011-04-02
Response, please. I've been sitting here for a while; sorry about my impatience

---

### Post by cariboo on 2011-04-02
Unfortunately, you aren't going to be able to run Unity 3D with that chipset, you can still run unity 2D though.

With a flash drive that size, you could do a full install on it, instead of your hard drive, but you have to have Natty installed somewhere, in order to install Unity 2D.

BTW, we consider it impolite to bump your own thread more than once every 24 hours.

---

### Post by fooman on 2011-04-02
nevermind...explained in previous post.

---

### Post by doppel.ganger on 2011-04-02
do you mean use the flash drive as the hard drive? Please try to explain it as much as possible, I'm very young

---

### Post by Devilz_108 on 2011-04-04
Is it worth for me to try and upgrade and help with testing or I'll just end up with problems?
My main PC broke months ago so I had to go with my backup one which got Geforce 2 
I'm currently running Ubuntu 10.10 but I'm not running any 3D effects with GNOME but I have a driver for 3D , Is it worth to try the 11.04 or I'll end up with problems or with Unity being very slow

Anyone did try with Geforce 2?

Thanks in advance :)

---

### Post by fabricator4 on 2011-04-04
> **doppel.ganger said:**
> do you mean use the flash drive as the hard drive? Please try to explain it as much as possible, I'm very young

Yes, install to the flash drive as though it is a hard drive. It will be sdc or whatever.  Do not install to the hard drive sda in this case.

You'll need a smaller flash drive, at least 1Gb to put the LiveUSB onto, or burn the LiveCD instead.

Chris.

---

### Post by fabricator4 on 2011-04-04
> **Devilz_108 said:**
>  Is it worth to try the 11.04 or I'll end up with problems or with Unity being very slow


Do not install 11.04 beta unless you are prepared to deal with any problems that may come along. 

You should not install a beta as your only operating system.

You won't be able to use Unity 3D until you install the 3D drivers. You should do so by allowing the restricted drivers and checking for available hardware drivers from the repositories.

If the 3D drivers did not work, you could still run Unity 2D but you'd have to install it from the repositories.  Note that there is a [bug in the Unity 2D]("http://ubuntuforums.org/showthread.php?t=1720205") in the repositories that causes it to eat memory.  If you didn't use the workaround to free up memory or log out occasionally then sooner or later you'd run out of memory and the system would crash.  I haven't seen any fixes come through for this bug, or indeed any more activity in the bug report beyond it being assigned.


Chris.

---

### Post by MBybee on 2011-04-07
11.04 has a lot of issues, as is normal with Betas. It largely works though - so proceed at your own risk, your mileage may vary, etc.

If you don't want Unity 2D, and Unity 3D isn't working quite yet, you can choose 'Classic' at login time from the menu.

---

