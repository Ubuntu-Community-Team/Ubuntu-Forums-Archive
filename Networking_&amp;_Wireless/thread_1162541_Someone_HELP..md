---
title: "Someone HELP."
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by HunterThomson on 2009-05-17
there is no problem with my router, wifi signl, interferance, laptop, wifi car,

However, ONLY in ubuntu I can serf the web but if I install a program or update. I get 

"Segmentation faulty tree... 50%"

All I did this time was...
Fresh download of Ubntu, Fresh burn. Fresh install. 

Then booted up ON Ethernet. I installed WICD to see if network manager was the problem. So, I then rebooted. Conneced to my wireless G %90 signil connection Open wireless network. Then opend up sysnaptic and installed terminator.

Now add-remove crashes, synaptic crashes, update manager crashes, and apt-get in the shell shows the segmentation fault and crashes.

What is going ON It's and Intel card 5300 ? 
I installed Archlinux on it like 20 times now and I have no problem in Archlinux. I also have no problem in the Ubuntu Live CD.

PLEAS help.

With out wireless internet my computer is useless.

---

### Post by HunterThomson on 2009-05-17
I now installed CrunchBang Linux and all is well with the wireless.

What could be the problem with Ubuntu ????

This blows my mind !

---

### Post by dmizer on 2009-05-17
Quick search in google gave this: [http://ubuntuforums.org/showthread.php?t=19563](http://ubuntuforums.org/showthread.php?t=19563)

Searched on:
apt-get "Segmentation faulty tree"

---

### Post by DakabinSHS on 2009-05-17
Have you tied using terminal for a remote connect?
connect <connection game>

---

### Post by HunterThomson on 2009-05-18
> **dmizer said:**
> Quick search in google gave this: [http://ubuntuforums.org/showthread.php?t=19563](http://ubuntuforums.org/showthread.php?t=19563)

Searched on:
apt-get "Segmentation faulty tree"

Cool Thanks :)

I have been having so many problems with this computer my brain is fried.

I'll go ahead and install agin and try it.

I'll post back if it works.

---

### Post by HunterThomson on 2009-05-18
Nope still the same problem with anything over wireless


WTF!!!

---

### Post by dmizer on 2009-05-18
Please post the output of:
```
lshw -C network
```

---

### Post by HunterThomson on 2009-05-18
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:24:81:b1:ea:93
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.8-3 ip=10.0.0.139 latency=0 module=e1000e multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: Wireless WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:6a:2b:56:12
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: da:ae:68:8c:17:48
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by dmizer on 2009-05-18
There are several bugs against this card, but none that specifically reference your problem. I suggest ditching the native driver and configuring your card via ndiswrapper: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper). If you run into problems, please see this thread: [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

---

### Post by HunterThomson on 2009-05-18
is there a way to use the driver for it that is used in 8.10.

Cruchbang is realy just Ubuntu 8.10 and it works fine.

---

### Post by dmizer on 2009-05-18
> **HunterThomson said:**
> is there a way to use the driver for it that is used in 8.10.

Cruchbang is realy just Ubuntu 8.10 and it works fine.

I have no idea. I'm actually not really very skilled with wireless, so I'll defer to those with more experience. All I can suggest is to look for the old driver version in Synaptic.

---

### Post by HunterThomson on 2009-05-18
Well well well....

I just installed Janty CLI x86_64 then ran the Crunchbang for Janty 9.04.01 installer. And no problems. I downloaded the ATI catalyst over wifi and the checksome was good. In Ubuntu 9.04 EVERY time I download it over wifi the checksome is way way off like even 5-8 #'s longer... 

I think it is a bug in Ubuntu and Ubuntu only. Not the drivers fault.

But I am happy now cruchbang is way better then installing Ubuntu.

---

### Post by dmizer on 2009-05-18
Glad you got it working. Never personally heard of crunchbang.

---

### Post by HunterThomson on 2009-05-18
Cruchbang is on the right track. I still much prefer Archlinux. But archlinux dosn't support ATI cards because ATI doesn't support Linux. They are far to slow in development.

Archlinux is going to be on Kernel 2.6.30 in a few weeks or less. The new ATI catalyst doesn't even support 2.6.29 yet.

Well the crunchbang "lite" is good don't bother with the desktop build.

---

