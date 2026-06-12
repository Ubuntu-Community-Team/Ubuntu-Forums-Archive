---
title: "Can't see Wireless Networks (WICD)"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by tristan8276 on 2009-12-08
Hello, I've just got Ubuntu 9.10 installed on a dual boot hard drive. Everthing works great and so far I love the Distro.
 
I have a WUSB100 wireless internet card plugged into a usb port. At first, I tried ndiswrapper, but had no luck and read a couple bug reports about it. Then, I found a working driver from RALINK and now my WUSB100 has blinking lights and shows up in the ifconfig, iwconfig, and lsusb lists. 
 
However, I cannot seem to get it to detect wireless networks. The signals are weak (1 or 2 bars), but they do show up fine under WinXP. Below, I've included relevant screenshots... any help would be greatly appreciated.
 
[ATTACH]139098[/ATTACH]
 
This is after iwconfig:
 
[ATTACH]139099[/ATTACH]
 
This is after lsusb:
 
[ATTACH]139100[/ATTACH]
 
This is after lspci:
 
[ATTACH]139101[/ATTACH]
 
This is after sudo iwlist scan:
 
[ATTACH]139102[/ATTACH]

---

### Post by tristan8276 on 2009-12-08
I tried running sudo lshw -C network just now and still no dice.  I'll see if I can post a screen shot of that command shortly.

---

### Post by mikey.duhhh on 2009-12-08
I've noticed the same thing.  I have a bcm4306 card, and once I finally got it to connect to an open wireless connection, it picked up only three wifi spots.  Yet, on my 9.04 machine I can see 10 wifi spots.  Furthermore I can only connect to open wifi spots.  Encrypted ones (WPA, WPA2, WEP, etc.) bring up Seahorse which asks for my default password, and then it brings up wireless connect password but never connects.  It tries and then asks for the wireless password again.  I am thinking of moving back to 9.04 on that laptop.

---

### Post by tristan8276 on 2009-12-09
If it is a sensitivity or range issue, is there a fix for that?

---

### Post by tristan8276 on 2009-12-10
I think I'm going to bite the bullet and download and install 9.04 to see if that helps.  Or, maybe a pci wireless card would work better?  
 
I'm really not sure because I'm a newbie, but I think this must be a software driver issue that isn't present in the window drivers.  However, ndiswrapper doesn't like the windows driver because according to the system logs, when it tries to load the windows driver it finds an "unknown symbol" and exits.

---

### Post by sophicsage on 2009-12-13
I have to bump this up.  This is a rather serious issue.  I know for a fact there are more than three spots around my house (others routers, etc) however I can see only mine and two neighbors.  My own signal is much weaker than before.  Whoever is developing this program (at Canonical?) needs to get involved and assist us in solving this problem.  I've just about gotten my system in perfect working order besides this issue and a non working microphone.  Other than that it's great so I don't feel like plundering the terminal and other settings before I find a concrete fix for this sensitivity, range, reliability problem.

---

### Post by pwabrahams on 2010-01-09
I'm having a very similar problem under KDE 4.3.4.  I think there's an interface missing, but I don't know how to set it up.  I only have **lo** and **eth0**.  The difference from your situation is that I had wireless connectivity working just fine until I did the latest upgrade.  As I recall, the interface was called **ath0**.

---

### Post by chitowner2 on 2010-02-10
FYI

On my karmic 9.10 (KDE) I use ra0.

CT

---

### Post by viralbus on 2010-05-18
I seem to be having the same problem.

I've just installed Ubuntu 10 on my stepson's computer, which has been running Ubuntu 8 and 9 happily till now.

Now it just can't find the wireless card.

I'm not sure what the network card is called (I didn't back up /var/log).  I could of course open the machine, but I'd rather do it through software. :-)

If I can't find a solution soon, I'll have to reinstall Ubuntu 9. :-(

---

### Post by viralbus on 2010-05-18
Solved it myself -- I needed to install linux-firmware-nonfree to support the ISL3890 card.

Easy enough, but not once the internet connection has disappeared.

It would be useful if Ubuntu could warn about this when upgrading.

---

