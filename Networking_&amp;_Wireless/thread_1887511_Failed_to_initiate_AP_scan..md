---
title: "Failed to initiate AP scan."
date: 2011-11-27
forum: Networking &amp; Wireless
---

### Post by perezronald on 2011-11-27
Hi Guys, 

I can't get my wifi to work,in oneiric ocelot (11.10), i tried eveything at this post, with no success :(

[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

In /var/log/syslog i got a "Failed to initiate AP scan" 

Nov 27 14:33:31 orbis NetworkManager[716]: <info> Config: set interface ap_scan to 1
Nov 27 14:33:31 orbis wpa_supplicant[972]: Failed to initiate AP scan.

Only can see a feww SSID, when a try to connect to my SSID always failed, the password pop-up came up again and again.

this is my lspci output

02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

orbis#lsmod |grep bcm
bcma                   20219  0 


Right now i'm using the additional STA driver that supports BCM4313

"This package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware."



At synaptic manager i can see the "bcmwl-kernel-source" installed, everything related to b43 is uninstall.


Please help me i'm getting crazy with this problem.

Best,
Ronald

---

### Post by biodojo on 2012-05-29
Hi did you ever get this to work? I see the same error on a netbook running 11.04 using the BCM4313 and the [I]brcmsmac driver
[/I]

---

