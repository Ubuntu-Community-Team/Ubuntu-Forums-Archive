---
title: "Broadcom in hp pavilion tx2510"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by arielon on 2009-11-04
Hey folks. I am currently running Karmic, and I have a Hp Pavilion tx2510 
I think the card in it is a **BCM 4322 B/G/N**, but in this page [https://wiki.kubuntu.org/KernelTeam/SuspendResumeTesting/Feedback](https://wiki.kubuntu.org/KernelTeam/SuspendResumeTesting/Feedback) I found that it's a  **Broadcom BCM4328 802.11a/b/g/n (rev 03).**

> ```
lspci -vnn | grep 14e4
08:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

``````
lspci -v
08:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
        Subsystem: Hewlett-Packard Company Device 137f
        Flags: fast devsel, IRQ 17
        Memory at d1100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [58] Vendor Specific Information <?>
        Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [d0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [13c] Virtual Channel <?>
        Capabilities: [160] Device Serial Number 21-00-3e-ff-ff-00-c1-ae
        Capabilities: [16c] Power Budgeting <?>
        Kernel modules: ssb
``````
lshw

-network UNCLAIMED
                description: Network controller
                product: BCM4322 802.11a/b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:d1100000-d1103fff
```went to: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

after reading: [http://forum.ubuntu-fr.org/viewtopic.php?id=237533](http://forum.ubuntu-fr.org/viewtopic.php?id=237533)

and installed those drivers.


make changes permanent:

 ```
sudo cp wl.ko /lib/modules/2.6.31-14-generic/kernel/net/wireless/
sudo depmod -a
sudo gedit /etc/modules
```
 ---- add:
```
lib80211
```

```
sudo gedit /etc/rc.local
```
---add:
```
sudo insmod /lib/modules/2.6.31-14-generic/kernel/net/wireless/wl.ko
```

before ```
exit 0
```
 
All is working ok now. 


"System>Administration>Hardware Drivers" could not do it. I think I should file a bug..


in part, the guide at: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check) was of good help.

---

### Post by Driskell on 2009-11-06
Greet tuto!

I had the same problem on my Dell E6400 () with Karmic installed.:

```

lspci -vnn | grep 14e4
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

```

Your post fixed my problem!
 
Maybe you could help me with the last remaining problem: After a restart, the modules are not correctly loaded.

Is still have to do the following commands to have a working wifi.

```
sudo rmmod ssb
sudo modprobe wl

```It looks like, though it is blacklisted, the ssb kernel is still loaded instead of wl.

Typing these lines is not much to do, but I wonder what was wrong with my install that caused this problem.

Thanks for sharing this solution!

Cheers,

---

### Post by ollibolli on 2009-11-14
Guys, I've got a solution for you. Change the first line in your /etc/rc.local to:

#!bin/bash

Restart your system and enjoy your automagically started new wireless driver!

---

### Post by uhappo on 2009-11-18
In the beginning I uninstalled the Broadcom driver from the Hardware ->

After playing in the console etc and following the steps, wireless wouldn't wake up after reboot.

Then I installed the STA-driver from the Hardware -section and after reboot it works!

Huh, I hope this works also in the future...

This laptop is HP tx2000

---

### Post by ssaxena on 2009-11-20
I have a Dell XPS 1330, which also has the Broadcom BCM 4328 card. Thanks for the great post which solved my wireless connectivity woes in Ubuntu 9.10 Karmic Koala.

some more points to add;


[LIST=1]
[*]I found the readme.txt @ [http://www.broadcom.com/support/802.11/linux_sta.php ]("http://www.broadcom.com/support/802.11/linux_sta.php")to be extremely helpful because it gives step by step guide on how to install the driver (of course its just a make command, no rocket science)
[*]Please note, ```
sudo rmmod ssb
``` is required
[*]As mentioned by arielon, you need to add entries to /etc/rc.local to make the change permanent so that the driver is invoked automatically. Also, you would need to add ```
sudo rmmod ssb
``` before the ```
sudo insmod /lib/modules/2.6.31-14-generic/kernel/net/wireless/wl.ko
```
[/LIST]

---

### Post by ajn946 on 2009-11-23
found solution, post deleted.

---

### Post by uhappo on 2009-11-23
> **ajn946 said:**
> found solution, post deleted.

Whats your solution, please post it or tell us where it is

---

