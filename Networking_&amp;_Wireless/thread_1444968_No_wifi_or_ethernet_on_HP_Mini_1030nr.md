---
title: "No wifi or ethernet on HP Mini 1030nr"
date: 2010-04-02
forum: Networking &amp; Wireless
---

### Post by whackedspinach on 2010-04-02
I just installed UNR from a usb drive on my hp mini 1030nr.  I followed a guide and got the drivers installed from the drive, but they would not activate in the restricted hardware dialog.  I tried to run update over wired, but I couldn't get ethernet working.  ifconfig -a anly shows lo, eth0 doesn't seem to exist.  Could anyone tell me how to get wifi working?

---

### Post by Iowan on 2010-04-02
Please post results of **sudo lshw -C network**

---

### Post by whackedspinach on 2010-04-02
lshw -C network:
```
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:feafc000-feafffff
```

---

### Post by tjeremiah on 2010-04-04
I just installed remix on my mother's hp mini and Ubuntu doesn't even detect the hardware for wifi to be enabled :(

---

### Post by Iowan on 2010-04-04
Well, it's not showing a driver for the wireless - and doesn't even see the ethernet. I'll see if there are some similar threads that might help.

[This]("http://ubuntuforums.org/showthread.php?t=1347680") one claims success...
[Another]("http://ubuntuforums.org/showthread.php?p=9056823") that might help.
Yet [another]("http://ubuntuforums.org/showthread.php?t=1368699")...

---

### Post by rousseau on 2010-04-10
I get the same thing as well for my Broadcom BCM4322. The network is "unclaimed" and the ethernet doesn't appear in the list.

---

### Post by rousseau on 2010-04-10
I should add that I tried the solutions linked to by Iowan without success.

---

### Post by rousseau on 2010-04-14
I give up on Ubuntu. I simply cannot get Ubuntu to recognize my ethernet card no matter what I try, and the wifi will not work, no way no how. 

I'm going back to Windows 7.

---

### Post by Iowan on 2010-04-14
@rousseau:
Ubuntu isn't for everyone - good luck with Windows 7.

---

### Post by cryptotrust on 2011-04-17
I found a solution

download the windows atheros driver from softopia

sudo apt-get install ndisgtk

extract the windows atheros driver to a folder

start up ndisgtk and point it to the atheros driver inf. I used the one in the 8131 folder under win2k.

Once it is done installing restart the computer and create a network connection and you are good to go.

---

