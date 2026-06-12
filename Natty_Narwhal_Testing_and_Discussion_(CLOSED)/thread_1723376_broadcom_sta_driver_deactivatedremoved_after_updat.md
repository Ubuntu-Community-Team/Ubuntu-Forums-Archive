---
title: "broadcom sta driver deactivated/removed after update"
date: 2011-04-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by beew on 2011-04-07
I have activated the broadcom sta driver using jockey and wireless was working flawlessly. I then went for an update in Synaptic, checked that nothing got removed, so far so good. After checking my email I restarted to complete all updates.When I logged back in there was no wireless. I started up "additional drivers" again and saw that the sta driver was not activated, so I tried to download and install it again and got an error message and it told me to check the log and I think these are the relevant log entries

> 2011-04-07 01:44:55,365 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-04-07 01:44:55,366 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-04-07 01:44:55,421 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-04-07 01:45:03,587 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-04-07 01:45:03,631 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-04-07 01:45:03,667 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
Any insight to what might have happened?

I am now accessing the internet with a USB wireless card.

---

### Post by beew on 2011-04-07
Ok, update and restart again. Still no wifi. Run jockey again, this time the driver is "activated but not in use"???

Anyone?

---

### Post by cariboo on 2011-04-07
I had a similar problem in an earlier kernel update, I just marked the bcmwl-kernel-source package for reinstallation in synaptic, which rebuilt the wl module.

---

### Post by TBABill on 2011-04-07
```
sudo apt-get install --reinstall bcmwl-kernel-source
```

---

### Post by beew on 2011-04-07
Just reinstalled bcmwl -kernel -source as advised and restarted, still no wifi.  Clicked on jockey it still said driver is activated but not in use. Tried removing the driver from jockey and got the error SystemError: installArchives() failed

---

### Post by cariboo on 2011-04-07
Can you post the output of:

```
sudo lshw -C network
```

---

### Post by manzdagratiano on 2011-04-07
Make sure you do not the free drivers installed - fwcutter and the like (I forget their names). These two conflict and render each other useless. Also, unless you already have these measures performed, make sure you blacklist b43, b44, ssb, b43legacy, and brcm80211 in /etc/modules.d/blacklist.conf. After that, installing bcmwl-kernel-souce followed by ```
sudo modprobe wl
``` should do the trick - always has for me. Also, reboot if you have to.

---

### Post by tjeremiah on 2011-04-07
try using Kernel 2.6.38-1

---

### Post by beew on 2011-04-08
Hi,

Tried reinstalling bcmwl -kernel -source and reboot several times. Still get "driver is activated but not currently inn use" but finally was able to remove the driver, but can't reinstall it.

Here is the log

> 2011-04-08 06:23:08,635 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-04-08 06:23:08,746 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-04-08 06:23:12,989 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-04-08 06:23:13,034 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-04-08 06:23:13,071 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-04-08 06:23:16,537 DEBUG: Shutting down




@cariboo907

Here is the relevant part from the output of lshw -C network

> -network UNCLAIMED     
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:f0200000-f0203fff



Thanks.

---

### Post by beew on 2011-04-08
no interest?

---

### Post by BertN45 on 2011-04-08
I have stopped using the broadcom STA driver in Natty it simply did not work on my bcm4311. For me the open source drivers work fine. I have installed b43 firmware installer and the b43fw-cutter

---

### Post by beew on 2011-04-08
But it was working before I got the update!? Now I just can't install it, so it is not even the case that it is not working!

---

### Post by geojorg on 2011-04-08
I had that same issue last week, I only managed to solve it by using connman. I think is a problem with network-manager and not with the broadcom driver.

sudo apt-get install connman

---

### Post by cariboo on 2011-04-08
> **beew said:**
> Hi,

Tried reinstalling bcmwl -kernel -source and reboot several times. Still get "driver is activated but not currently inn use" but finally was able to remove the driver, but can't reinstall it.

Here is the log




@cariboo907

Here is the relevant part from the output of lshw -C network



Thanks.

There seems to be a bit missing from the output, this is whatI get when I run the command:

```
 *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 90:4c:e5:41:e4:2f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **driver=wl0** driverversion=5.100.82.38 ip=192.168.1.103 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:feafc000-feafffff
```

I've bolded the driver my device uses.

---

### Post by beew on 2011-04-08
Hi Cariboo907

Sorry for the sloppy cut and paste, here is the complete section

> 
*-network               
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:f0200000-f0203fff


---

### Post by beew on 2011-04-08
> **geojorg said:**
> I had that same issue last week, I only managed to solve it by using connman. I think is a problem with network-manager and not with the broadcom driver.

sudo apt-get install connman

Installing connman would remove the network manager though, I am not sure that I would want to do that. But thanks for response.

---

### Post by beew on 2011-04-08
Tried to install the sta driver again and get the same error in jockey's log

> 2011-04-08 23:54:51,293 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-04-08 23:54:51,376 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-04-08 23:54:53,877 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-04-08 23:54:53,920 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-04-08 23:54:53,960 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-04-08 23:54:56,316 DEBUG: Shutting down


---

### Post by beew on 2011-04-09
Bump!

---

### Post by SevenMachines on 2011-04-09
Has the driver actual built correctly? try,
$ dkms status

[EDIT] it should say installed obviously
bcmwl, 5.100.82.38+bdcom, 2.6.38-8-generic, x86_64: installed

---

### Post by beew on 2011-04-09
> **SevenMachines said:**
> Has the driver actual built correctly? try,
$ dkms status

[EDIT] it should say installed obviously
bcmwl, 5.100.82.38+bdcom, 2.6.38-8-generic, x86_64: installed


It says>  bcmwl, 5.100.82.38+bdcom, 2.6.38-8-generic, i686: installed 

But still has no wireless and jockey stills says that the sta driver is not installed and trying to install it results in error (see log above)

---

### Post by SevenMachines on 2011-04-09
Ah well, its just that 
```
WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl
```
is a classic sign of an unbuilt driver, either because the build failed, or you're booted into to a different kernel that it didnt automatically build for. but if
```
$ uname -r
2.6.38-8-generic
```
then that isnt the problem sadly

---

### Post by geojorg on 2011-04-09
Connman in a good replacement for network manager and it would work the same way.

---

### Post by beew on 2011-04-09
> **SevenMachines said:**
> Ah well, its just that 
```
WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl
```is a classic sign of an unbuilt driver, either because the build failed, or you're booted into to a different kernel that it didnt automatically build for. but if
```
$ uname -r
2.6.38-8-generic
```then that isnt the problem sadly


Weird. I did the uname -r command and the result is  2.6.38-7-generic even though dkms status says 2.6.38-8-generic. I can't find 2.6.38-8 from the boot menu either.

---

### Post by beew on 2011-04-09
> **geojorg said:**
> Connman in a good replacement for network manager and it would work the same way.

As it now seems that there is a kernel version problem I don't think network manager is the culprit, but I will keep your advise in mind.

---

### Post by arpanaut on 2011-04-09
Hey beew,
Have you seen this thread, I just did a fresh install on my laptop and applied this fix:
[http://ubuntuforums.org/showthread.php?t=1700897&highlight=broadcom&page=2](http://ubuntuforums.org/showthread.php?t=1700897&highlight=broadcom&page=2)
Fix is from post 14 and on

Not the most elegant but it is working for my BCM4311, Don't forget to lock the kernel-sources in synaptic

---

### Post by SevenMachines on 2011-04-10
> **beew said:**
> Weird. I did the uname -r command and the result is  2.6.38-7-generic even though dkms status says 2.6.38-8-generic. I can't find 2.6.38-8 from the boot menu either.
that looks likes your problem then, you could try either,

1. Fix the missing grub option an boot into 2.6.38-8
```
$ sudo apt-get install linux-image-2.6.38-8-generic linux-headers-2.6.38-8-generic 
$ sudo update-grub
```Might work, technically you shouldnt need to update grub but then it wont hurt either and you'll be able to see whats going on

2. Build the driver for 2.6.38-7, think if i remember rightly the below should work
```
$ sudo dkms build -m bcmwl -v 5.100.82.38+bdcom -k 2.6.38-7-generic
$ sudo dkms install -m bcmwl -v 5.100.82.38+bdcom -k 2.6.38-7-generic
```

---

### Post by scristopher on 2011-04-10
This worked great for me with natty beta! thanks you so much 
but i changed 2.6.38-7 to 2.6.38-8
first i tried to build the drivers w/o checking to see if headers were installed that didnt work (obviously)
so i installed headers/image after install completed it built it by itself, i decided to double check for sanity
and tried to build them w/ dkms build but got message already installed!
rebooted and what do ya kno, wifi works :)
```
$sudo apt-get install linux-image-2.6.38-8-generic linux-headers-2.6.38-8-generic 
$ sudo update-grub

```
```

$ sudo dkms build -m bcmwl -v 5.100.82.38+bdcom -k 2.6.38-8-generic
$ sudo dkms install -m bcmwl -v 5.100.82.38+bdcom -k 2.6.38-8-generic

```

---

### Post by beew on 2011-04-10
It turns out to be a kernel problem. The kernel has not been upgraded properly because I have a dual boot and for some reason Maverick (which controls grub) has not detected the kernel upgrade in Natty.

Updated grub in Maverick and now problem is solved. I wouldn't have thought of that!
[http://ubuntuforums.org/showthread.php?t=1725539&page=2](http://ubuntuforums.org/showthread.php?t=1725539&page=2)

---

### Post by MasterNetra on 2011-04-11
> **beew said:**
> It turns out to be a kernel problem. The kernel has not been upgraded properly because I have a dual boot and for some reason Maverick (which controls grub) has not detected the kernel upgrade in Natty.

Updated grub in Maverick and now problem is solved. I wouldn't have thought of that!
[http://ubuntuforums.org/showthread.php?t=1725539&page=2](http://ubuntuforums.org/showthread.php?t=1725539&page=2)

Not necessary from upgrade, While at this point I'm experiencing the same problem but I also experienced at a earlier date when I installed 11.04 from image. STA didn't work after I installed it fresh. So its not a issue from upgrade. Btw I am NOT duel booting. Just pure Natty.

---

