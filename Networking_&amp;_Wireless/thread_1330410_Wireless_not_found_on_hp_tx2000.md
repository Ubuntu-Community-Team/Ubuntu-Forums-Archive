---
title: "Wireless not found on hp tx2000"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by Torri on 2009-11-18
Hi everyone. I know this is a common problem, but haven't gotten anywhere with the info from previous threads. 

I just installed Xubuntu on my HP tx2000 laptop. Everything works except my wireless internet. I tried installing the ndiswrapper in add/remove applications, but it says it can't be installed on my computer. 

Incidentally, I just installed Ubuntu on my desktop which is basically the same system as my laptop, and everything worked right out of the box, including the wireless. 

Anyone know how to fix this (preferably step-by-step for an Ubuntu newbie)?? Thank you!

---

### Post by Favux on 2009-11-18
Hi Torri,

Did you try installing the Broadcom proprietary drivers through System > Administration > Hardware Drivers?  If you don't see them did you enable Proprietary drivers in Software Sources?

---

### Post by Torri on 2009-11-20
Okay, weirdness happens. It just started working this morning. I don't know why... It just turned on and stayed on. 

Which makes me think it's going to just turn off without warning. Oh well... I guess I'll just wait and see.

---

### Post by Torri on 2009-11-20
ARRRGH! Okay it was working just fine, perfect all day, then I turned off my computer, turned it back on and my wireless is GONE. The drivers are gone too, and now I can't find them anywhere. I didn't do anything between being online and turning off my computer... so now what? Where did it go???? I need the exploding head smilie, seriously.

---

### Post by Torri on 2009-11-21
Has anyone encountered this problem before??

---

### Post by lukejohnson on 2009-11-21
Torri, I am experiencing a similar problem. I also have an HP Pavilion tx2000. I am currently running Karmic but I had the problem with Hardy before I decided to upgrade. 

I will describe what I have done so far but I have no solution. I am thinking of starting another thread with my problem and will link similar threads that I think could be related to this issue. 

I initially install the proprietary Broadcom driver and my wireless worked flawlessly. Now the Broadcom driver is not available in the menu suggested by Favux. Now I get the following output in terminal

```
luke@Oryx:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.
vboxnet0  no wireless extensions.
```When I do "lsusb" with the physical wireless switch on (blue light) I get the following. When it is switched off the wireless does not show up in "lsusb" (as expected I suppose)

```
luke@Oryx:~$ lsusb
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]

```Now I have done a few other things but with no luck but I did just notice this 

```
luke@Oryx:~$ ls /etc/modprobe.d/
alsa-base.conf          blacklist-bcm43.conf  blacklist-firewire.conf     blacklist-modem.conf  blacklist-watchdog.conf  ndiswrapper
blacklist-ath_pci.conf  blacklist.conf        blacklist-framebuffer.conf  blacklist-oss.conf    libpisock9.conf

```I am not sure about the significance of the file blacklist-bcm43.conf but bcm43 is related to the Broadcom driver. I have to learn some more about this blacklist thing to see if it is relevant. 

It might not be of much use but I would be interested to know if you also have the blacklist-bcm43.conf. I would also like to know what you have in blacklist-bcm43.conf. (type " gedit /etc/modprobe.d/blacklist-bcm43.conf " in terminal )

I hope this is of some help.

---

### Post by Favux on 2009-11-21
Hi lukejohnson,

I'm pretty sure that's the legacy Broadcom module and you don't want it (i.e. you want it blacklisted).  I'm not a wireless guru but I'm pretty sure the Broadcom proprietary driver is 'wl' and it should be in lsmod if it is auto-loading:
```
lsmod | grep wl
(or just)
lsmod
```
To see if it's there, even isn't it isn't loading, and it's location:
```
modinfo -n wl
```
On my Intrepid system it's at "/lib/modules/2.6.27-15-generic/volatile/wl.ko".

---

### Post by lukejohnson on 2009-11-22
Favux, 

Thanks for the pointer. When I type "lsmod | grep wl" I do not get anything. Should I "modprobe wl" since it isn't auto loading? 

Also I know this might sound silly but how do I determine the chipset? When I use lsuse I get the ID 03f0:1710 as I mentioned before. But I seem to be getting mixed messages from online searches. Any suggests?  

Thank you

PS Sorry Tori for semi hijacking your thread. I'll make my own now.

---

### Post by Favux on 2009-11-22
Hi lukejohnson,

OK, you've established the module isn't loaded.  Do the other command to see if it's on the system.  It sounds like both of you have it installed.

Well like I said I'm not a wireless guru.  So there might be a file you need to insert the module into (insmod) or something might be breaking the module dependencies which you need to re-establish (depmod -a).  And yes maybe a modprobe.  But I don't know any of that stuff.

But if the module is installed on the system what I was going to suggest is adding it to the modules file.  That should "force" it to load.  Try adding it (wl) to the bottom of the file I guess:
```
gksudo gedit /etc/modules
```
Save, Close, and reboot.

---

### Post by Favux on 2009-11-22
Oh, sorry I forgot to answer your question about the chipset.  It should be in lspci so:
```
lspci | grep Broadcom
```

---

### Post by JBAlaska on 2009-11-22
Run this in a terminal:
```
sudo apt-get install bcmwl-kernel-source
```

Reboot and check hardware drivers, you should now be able to see and install the Broadcom Proprietary driver.
Reboot, Enjoy!

---

### Post by Bucky Ball on 2009-11-22
Plug an ethernet cable in and get all updates. Apparently JBAlaska's idea seems to work in 9.10.

---

### Post by Torri on 2009-11-22
No worries for thread hijacking. :) This is all helpful. I'm not on my laptop at the moment but I'll post my results in a bit. I did plug in my ethernet and got all updates, which didn't seem to help. 
 
Oh and get this.... I turned the f****** thing on this morning and the wireless was fine. Sometimes it's there, sometimes not. What would cause that?? Are you having that problem as well Luke? Or are yours not showing up at all?

---

### Post by Torri on 2009-11-22
> **JBAlaska said:**
> Run this in a terminal:
```
sudo apt-get install bcmwl-kernel-source
```
 
Reboot and check hardware drivers, you should now be able to see and install the Broadcom Proprietary driver.
Reboot, Enjoy!
 
Also, I tried this first, and it worked like a charm. At first. Then it disappeared again. That's the problem I'm having. It's here, then it's gone, comes back, gone again... 
 
Maybe it's the hardware? I've never heard of wifi going bad before, but I'm sure it happens. I'm thinking about just getting rid of this computer. It's the worst I've ever owned; it has so many weird quirks and problems. I was really hoping that dumping vista and installing linux would breathe some new life into it. But so far, no luck. Too bad too, cause everything else works beautifully with xubuntu, even the tablet, which I was expecting to have to give up.

---

### Post by Bucky Ball on 2009-11-22
Is the machine under warranty still?

Which model is it exactly? If it is one of these:

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01087277&lc=en&dlc=en&cc=us&product=3370281&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01087277&lc=en&dlc=en&cc=us&product=3370281&lang=en)

... then it could well be hardware and if it is 24 months or less from the start of your warranty you would be eligible for a repair.

If not you might look into wicd instead of Network Manager if that hasn't been mentioned already ...

You can get the model and product number from the BIOS or the bottom of the machine. I have a dv6000 which just died two months outside the period so I don't really have a leg to stand on. I am looking into it though.

---

### Post by lukejohnson on 2009-11-22
So I did some reading on the HP Support Forums and found this thread

[http://h30434.www3.hp.com/psg/board/message?board.id=Internet&thread.id=328&view=by_date_ascending&page=1](http://h30434.www3.hp.com/psg/board/message?board.id=Internet&thread.id=328&view=by_date_ascending&page=1)

It looks like it is one of many of people complaining about the tx1000 and tx2000's wireless. Many are experience this intermittent wireless connectivity and some are saying it is a hardware issue. Another thread (I couldn't find the link again) said that issues start with the wireless, then bluetooth, and then the display. 

Initially I had off and on wireless.  Most of the times I would fiddle with something and think I solved the problem only to discover in two days it didn't work again (this occurred for a month or so). But now my wireless hasn't worked for a week and my bluetooth is being sketchy. I use to never have a problem maintaining a connection between my mouse and computer but now it will work for 2 minutes then not work for 10 minutes. It seems like it is also getting worst. 

If I didn't mention this before when I dual boot into vista I experience that same problems. This was my biggest reason for thinking it was hardware. I am going to give the most recent suggestions a try over thanksgiving but I am also going to start trying to contact HP about replacement. Some people on the HP forums said that HP replaced their laptops (after much hassle) even though their model were not on the extended warranty list.

EDIT: So it seems that for the first time in a week the wireless connected automatically at boot. I am not sure what is different now since I was in Windows for a day to back up files and can't remember the last thing I did in Ubuntu. This is not a satisfying way to solve a problem but I am ready to be done with this.

---

### Post by lukejohnson on 2009-11-23
I just rebooted and the wireless is gone again. Maybe I should have just gone to bed on a good note...

---

### Post by Torri on 2009-11-23
Yep that's exactly what's going on with mine. And i started having problems with Vista when I did the dual boot too, which was why I too thought it might be the hardware. Kind of scary that the wireless going is apparently a bad omen for future problems.
 
It seems to be working today, but who knows. I have a loooong list of weird quirky issues on this computer.... overheating, disk drive won't stay closed, clicks off with no warning, tablet works only sometimes, keys falling off, cursor jumps to the lower right corner, I could go on. 
 
I'm going to try a couple more things but mostly I think it's just time to retire the tx2000. Sucks too cause I've only had it a year and a half. And honestly, I don't want a replacement after the problems I've had with this one.

---

### Post by Bucky Ball on 2009-11-23
I advise you to contact HP immediately. The wireless going on and off is a bad sign and sounds like definitely hardware. Back up your valuable data and get onto HP. You may switch on your machine one day and find a black screen staring at you with the thing trying to restart itself. That's what happened to me about a month after the wireless card died (when the card did die HP insisted it was a wireless card issue and tried to charge me for a card and installation despite the fact I had sent them all the links to the Limited Warranty Service Enhancement and the dead card is the first symptom of this issue on the list!). 

When the wireless drops out, can you still find the device or has that disappeared too? You can check by pasting this in a terminal:

```
lspci
```... and toward the bottom of the output there should be your wireless device. If it is not there and the wireless is down, you have an issue and that is definitely hardware.

---

