---
title: "RT2870STA Keebox Wireless not working"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by toomuchcomputertime on 2011-04-30
I'm using Ubuntu 11.04 and can't get my new Keebox W150NU usb wifi chip to work. 

Using ndiswrapper, it crashes my computer almost every time I try to use it. 

Any suggestions? 
[Here is the download page for drivers/etc. ]("http://www.keebox.com/downloads/list_subcategory.asp?TYPE_ID=48&SUBTYPE_ID=1338")

---

### Post by chili555 on 2011-04-30
Which specific Windows driver did you use? Windows XP? Here is a snip from *man ndiswrapper-1.9*:> NAME
       ndiswrapper  -  Linux kernel module and user space tool to load and run ***Windows XP*** drivers for wireless cardsWe could probably trick the native rt2870sta driver to use your device.

---

### Post by toomuchcomputertime on 2011-04-30
I tried both the x86 and the 64 bit XP divers, as well as both Vista drivers. The Vista drivers don't do anything, the XP 64 driver (I'm running 11.04 64 bit) can't connect to the internet, and usually crashes Ubuntu when I plug it in. 

Thanks.

---

### Post by chili555 on 2011-04-30
Are you game to trick the built-in driver to grab your device? You don't have much to lose. Please post:```
lsusb
```We'll erase the ndiswrapper driver and write two files and see what happens.

---

### Post by toomuchcomputertime on 2011-04-30
Sure, Thanks! 

```

matthew@matthew-Satellite-L505D:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 14b2:3c2c Ralink Technology, Corp. Keebox W150NU 802.11bgn Wireless Adapter [Ralink RT3070]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bc2:2300 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
matthew@matthew-Satellite-L505D:~$ 

```

---

### Post by chili555 on 2011-04-30
This is a bit experimental, but no pain, no gain, right?

First, run:```
ndiswrapper -l
```It will tell you the name of the driver you installed. It is probably rt2870. Next, we'll remove it:```
sudo ndiswrapper -e rt2870
```Substitute what you found if not rt2870.

Now remove the device and in a terminal, do:
```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```

Add one long line:
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="14b2", ATTR{idProduct}=="3c2c", RUN+="/sbin/modprobe -qba rt2870sta"
```
Caps, brackets, punctuation, etc. are crucial. Proofread twice, save and close gedit.
```
sudo gedit /etc/modprobe.d/network_drivers.conf
```
Add one long single line:
```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "14b2 3c2c" > /sys/bus/usb/drivers/rt2870/new_id
```
Proofread twice, save and close gedit. Insert the device. If it doesn't start immediately, you might have to do:
```
sudo modprobe rt2870sta
```Let us know; this is the first time we've seen this device, certainly in 11.04, so we're breaking new ground.

---

### Post by toomuchcomputertime on 2011-04-30
WOW!!! Thanks!!! It is working!!! I've spent many hours trying to get this working and that was simple - for me. Thanks!

---

### Post by chili555 on 2011-04-30
Awesome! You will help some searchers, too. Are you ready to use Thread Tools at the top and mark this as Solved?

---

### Post by toomuchcomputertime on 2011-05-01
Yes, Thanks, I forgot about that.  I read quite a few other simiilar posts before posting myself.

---

### Post by Asmodean91 on 2011-05-12
Thanks!  This also worked for my ASUS eee with the netathw driver (ath9k).

---

### Post by chili555 on 2011-05-12
> **Asmodean91 said:**
> Thanks!  This also worked for my ASUS eee with the netathw driver (ath9k).What?? How does a change in the pci.id for a Ralink card help an Atheros card? Am I getting confused??

---

### Post by FourM on 2011-07-21
I have this same exact device. This works perfectly for me! Thank you! I hope this can become included in the future. Ralink updated their Windows drivers to support this device so I'm sure it would work with their Linux driver if the hardware ID was added.

Thank you so much!

---

### Post by cabetza1 on 2011-10-17
Good for ubuntu 10.04

---

