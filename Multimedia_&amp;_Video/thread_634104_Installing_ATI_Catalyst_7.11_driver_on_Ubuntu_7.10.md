---
title: "Installing ATI Catalyst 7.11 driver on Ubuntu 7.10 system"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by gr3gw on 2007-12-07
I'm new to Linux but I thought I'd share my experience of installing a driver for a Radeon 9550 graphics card in Ubuntu 7.10. Please excuse my clumsy use of Unix terminology.

It has taken me over a week and lots of reading both in this forum and elsewhere but I have been successful. Here's my notes. I hope they will be of use to others attempting the a similar installation.

Graphics card: Radeon 9550.
Principle use: To drive two monitors.
My config: P4, 2.4MHz, 1Gb, Ubuntu 7.10.

Installation of ATI's latest driver Catalyst 7.11 (internally version 8.433.2)
1. Download drive from ATI (now AMD) website: [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)
2. From Terminal program, type sudo ***/ati-driver-installer-7-11-x86.x86_64.run where *** is full path to file.
3. Use ATI GUI program to install driver. (I chose 'all' and 'auto'.)
4. From Terminal, type sudo aticonfig –initial
(I have two monitors and so I typed config –initial=dual-head  --screen-layout=right. Typing aticonfig in Terminal window displays aticonfig options.)
5. Restart.
After restart, look at Applications menu. You should see the ATI Catalyst Control Centre.
6. Start ATI Catalyst Control Centre to configure card and monitors.

This worked for me but your experience may be different. I tried the 'HOWTO: Install the ATI driver on ANY stable version of Ubuntu' procedure but it didn't work for me.

______________
Greg

---

### Post by coskierken on 2007-12-07
Great News!  :) I have installed this the same way.  I have an Asus A8jP with Mobile X1700 vidcard.  It worked for the most part.  I had a little stability problems, but mostly ok.  I am still working with it.  Right now I don't have the ATI console installed.  The driver loaded from fresh install is the same, but without console.  It even updates to the latest if you have your internet connected.  The problem I have is trying to get the TV out (S-VHS) working to output to a TV.  I know it is archaic, but I am working with it.  Any suggestions?  I will be working with the aticonfig this weekend and making this my main priority.:confused:

---

### Post by bsmith1051 on 2007-12-07
After the main GUI install finishes, does it prompt you to either restart or run the config utility?  If you need to run the config *before* rebooting that would be a major step to not communicate!

---

### Post by lguti on 2007-12-08
Hey, mate sorry to bother but could you make the 2nd step more specific

---

### Post by Yellow Pasque on 2007-12-08
Download the file to your desktop. Then:
```
cd ~/Desktop
sudo bash ./ati-driver-installer-7-11-x86.x86_64.run
```

---

