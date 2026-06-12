---
title: "Wired internet works, but not wireless?"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by LordBonney on 2010-09-07
Hi,

I've just got a new netbook (a Samsung N150), which came with Windows 7, but I'd heard about Linux, so thought I'd give it a go, and I am now running Ubuntu off a USB stick (I followed everything from here - [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download))

I can get the wireless working in Windows, but in Ubuntu I can only get it working wired? I'm a newbie when it comes to doing anything beyond the basics with computers, so most of the solutions I've looked at on this website have gone over my head. 

I've checked that I can use wireless internet on the 'Users and Groups' option in Administration, and I've tried activating something called the 'Broadcom STA Wireless Driver' under Hardware Drivers, but that keeps on failing.

I dont know if its because I have a different version of Ubuntu or what, but when I right click on the Network Connections button at the top of the screen I dont have an 'Enable Wireless' option, only Network and Notification buttons, and some of the solutions I've read say you need to have Enable Wireless ticked?

Thanks

---

### Post by sgosnell on 2010-09-07
Yes, there should be a checkmark beside 'Enable wireless',  I haven't seen that problem, but there may be threads on the forum discussing it.  You might find help through the search box.

---

### Post by LordBonney on 2010-09-07
I've had a look through the forum and cant find anyone else who cant find the 'Enable Wireless' button. I've tried updating Ubuntu via the Update Manager, as apparently this worked for someone else with an N150, but for some reason it tells me I dont have enough disk space to do this, despite having well over 100GB free?

---

### Post by sgosnell on 2010-09-07
Try this one:
[http://ubuntuforums.org/showthread.php?t=1423477&highlight=can%27t+enable+wireless](http://ubuntuforums.org/showthread.php?t=1423477&highlight=can%27t+enable+wireless)

Putting "can't enable wireless" in the search box turns up a long list of hits, including this thread.

---

### Post by LordBonney on 2010-09-07
> **sgosnell said:**
> Try this one:
[http://ubuntuforums.org/showthread.php?t=1423477&highlight=can%27t+enable+wireless](http://ubuntuforums.org/showthread.php?t=1423477&highlight=can%27t+enable+wireless)

Putting "can't enable wireless" in the search box turns up a long list of hits, including this thread.

I gave that a go, but when I type 'rfkill list' into the Terminal all that comes up is something about Bluetooth (Soft-blocked:No, Hard-blocked:No), nothing about wireless.

---

### Post by sgosnell on 2010-09-07
There are many other suggestions further down in the thread.

---

### Post by LordBonney on 2010-09-07
> **sgosnell said:**
> There are many other suggestions further down in the thread.

I've tried typing in 'sude rmmod -f samsung_laptop', but it says there is no such file or directory. There isnt a physical switch on the laptop anywhere, and the internet definitely works in Windows.

Typing in 'lshw -C network' comes up with this-
  
*-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 00
       serial: 00:24:54:a7:a5:ed
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A ip=192.168.1.4 latency=0 multicast=yes
       resources: irq:29 memory:f0200000-f0203fff ioport:2000(size=256)


Everything else in that thread is to do with a physical switch, which isnt the problem, or something to do with HP laptops, so I dont think theres anything else in that thread that could help?

---

### Post by sgosnell on 2010-09-07
If you put the proper terms into the search box at the top right of the page, you'll get a long list of threads to search.  I don't have time to do that for you right now.

---

