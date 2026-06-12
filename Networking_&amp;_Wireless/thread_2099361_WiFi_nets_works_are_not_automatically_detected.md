---
title: "WiFi nets works are not automatically detected"
date: 2012-12-29
forum: Networking &amp; Wireless
---

### Post by oxf on 2012-12-29
I just did a fresh install of Precise (and changed desktop back to Gnome)
I have the b4318 wireless card so I had to do the download of fw-cutter etc and all went to plan and the Wifi is enabled and working nicely.

The only minor problem is that the networks don't seem to be automatically detected and listed. I have to uncheck "Enable Wireless" and then re-enable it again, after which the available wireless networks show up in the pulldown menu.

Any suggestions on how to fix this?

Thanks

Caitlin

---

### Post by oxf on 2012-12-29
Update: It seems that occasionally, but not often, it will detect them after a longish and inconvenient delay.

---

### Post by srekcahrai on 2012-12-29
Keep this in start up
```
sudo ifconfig <wireless interface> up
```

---

### Post by oxf on 2012-12-29
> **srekcahrai said:**
> Keep this in start up
```
sudo ifconfig <wireless interface> up
```

Thanks,
Do you mean I just run that in terminal?
What exactly do you mean by "keep in startup"?

---

### Post by Hadaka on 2012-12-29
Hi oxf, please post the output of..

```
cat /etc/modules 
```
and.
```
lspci -nn | grep AN
```

Thanks.

---

### Post by srekcahrai on 2012-12-30
For temporary, run in terminal
For permanent, store in start up

To store in startup, click on the icon like settings icon at top right. Startup application option will be available.

---

### Post by oxf on 2012-12-30
> **Hadaka said:**
> Hi oxf, please post the output of..

```
cat /etc/modules 
```and.
```
lspci -nn | grep AN
```Thanks.

Thanks  ....

```
mbdb@M2000:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

```

```
mbdb@M2000:~$ lspci -nn | grep AN
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

```

I should also add the following:

1. Sometimes if I wait long enough they are eventually detected and listed in the pulldown, however, can be quite a wait.

2. It's not just the available WiFi networks that are not listed. In fact everything in the menu above "Enable Networking is missing. This includes: 
Wired networs
Wireless networks
Connect to Hidden network
Create New....
VPN ......   etc etc

Caitlin

---

### Post by oxf on 2012-12-31
> **srekcahrai said:**
> Keep this in start up
```
sudo ifconfig <wireless interface> up
```

Actually that doesn't seem to affect it either way. This problem is a bit of an irritating one as the WiFi is in essence working OK it's just doesn't always load/show in the menu. 

It's definately related to the "Enable Wireless" check box,  i.e if I uncheck and then recheck "Enable Wireless" voila...it's detected. Also some times if I leave it long enough it will detect on it's own.

---

### Post by Hadaka on 2012-12-31
Hi, this may help,it will load your dirver on startup or reboot.

```
sudo su
echo b43 >> /etc/modules
exit
 
```

---

### Post by oxf on 2012-12-31
> **Hadaka said:**
> Hi, this may help,it will load your dirver on startup or reboot.

```
sudo su
echo b43 >> /etc/modules
exit
 
```

Thanks I'll try that. I presume thats entered in Startup Applications? in which case three separate entries since there's only one line available?

Caitlin

---

### Post by Hadaka on 2012-12-31
Hi, no its just a terminal entry,your normal user default terminal.
ctrl/alt/t....you are placing b43 in /etc/modules...but no need to
cd there as you are telling it where to write with the echo command.
no other directories or entries are required.

---

### Post by Hadaka on 2012-12-31
Hi, since you have changed back to Gnome panel, take a look at this
thread with a like problem you are having

[http://askubuntu.com/questions/149522/how-to-reset-top-panel-on-ubuntu-12-04-to-upgrade-standard-classic-view](http://askubuntu.com/questions/149522/how-to-reset-top-panel-on-ubuntu-12-04-to-upgrade-standard-classic-view)

hope this helps.

---

### Post by oxf on 2013-01-02
> **Hadaka said:**
> Hi, no its just a terminal entry,your normal user default terminal.
ctrl/alt/t....you are placing b43 in /etc/modules...but no need to
cd there as you are telling it where to write with the echo command.
no other directories or entries are required.

Well thanks for the idea. Unfortunately that made no difference. I guess something is stopping it from loading because as soon as I un-enable wireless/enable wireless it works fine.

---

### Post by oxf on 2013-01-06
Hi all...

Well I wonder if there are any further ideas how to fix this? 

To recap the b43 fwcutter jiggle obviously worked because I do have fully functioning wireless capability. It's just it doesent seem to automatically load on boot-up. Once I uncheck and recheck "Enable Wireless" in the pulldown menu it loads and wireless works.

This bc4318 wireless card has always been a bit funny in this laptop right from when I forst used Ubuntu. However, once the driver was installed it's always worked/loaded fine. This is the first time I've had this problem!

Caitlin

---

### Post by oxf on 2013-01-13
Any ideas?
I'm stumped with this one..

---

### Post by oxf on 2013-01-23
Bump!!!!!!!!!!!

---

