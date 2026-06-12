---
title: "need to fix bad install of bcm3428 in 8.10 on hp pavillion"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by cjoki on 2008-12-14
Hello,

I had a install of ubuntu 8.10 desktop and was able to get everything up and running, including the wireless. For other reasons I needed to install the server version after which I used the command to add the desktop for the gui. I have tried for nearly 1.5 days to get the wireless installed but can not get the broadcom sta drivers to display in the hardware drivers.

```
~$ lsb_release -d
Description:	Ubuntu 8.10

```

```
~$ uname -mr
2.6.27-9-server i686

```

```
~$ sudo lspci |grep Broadcom
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
```

```
~$ lspci -n |grep 03:00
03:00.0 0280: 14e4:4328 (rev 03)
```

```
~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
```

```
~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:ba:f2:40
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.7 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: de:7c:03:83:9a:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

I am a windows migrant...the commands I got are from reading another post...I hope they help.

---

### Post by ieee488 on 2008-12-14
Broadcom chipset means in all likelihood you need to use ndiswrapper.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Ayuthia on 2008-12-14
You can try the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo /etc/init.d/networking restart
```
That should get the Broadcom STA module running.  

If that works and you haven't already done so, you might first try blacklisting the b43 and ssb modules and add wl to /etc/modules:
```
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist
echo wl | sudo tee -a /etc/modules
```
These commands will add them for you.  

If that does not work, you can use:
```
echo -e '#ssb/wl workaround, added' `date` '\ninstall wl modprobe -r b43 b44 b43legacy ssb ndiswrapper; modprobe --ignore-install wl $CMDLINE_OPTS;' | sudo tee -a /etc/modprobe.d/wl
```
This will add a list of commands to run when the wl module is loaded.  It will unload the b43, b44, b43legacy, ssb, and ndiswrapper modules and load the wl module.  

Hope that helps.

---

### Post by Ayuthia on 2008-12-14
> **ieee488 said:**
> Broadcom chipset means in all likelihood you need to use ndiswrapper.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

You don't necessarily need ndiswrapper for your 4328 card.  It might work with the Broadcom STA driver.  The b43 driver does not support the 4328 card yet.

---

### Post by cjoki on 2008-12-15
Thank you all for your responses....I was quite frustrated by the whole experience and so reinstalled the unbuntu 8.10 desktop. Once rebooted and ran the update I was able to install the nvidia graphics driver and the broadcom sta driver from the system->admin->hardware drivers. One more reboot and configuring my wireless connection and BAM! magic.

I am happy with the desktop installer, the server....less so. Well that is not entirely fair. I was under the impression that a gui would open with the server install and was left scratching my head when i was only left with a command prompt. A clue would have been nice before I installed the server....anyways I did a web search and found a command to install either the gnome desktop or the kde desktop on the server. I suspect that this install method is missing a few pieces and is why I did not have the broadcomm sta drivers displayed in the hardware drivers gui.

Now....why did I go from the desktop that was initialy fine to the twitchy server/desktop install that prompted my post? LAMP, I am a web designer and for years worked under windows xp, 98 and vista (the last of course promtped my linux move). I found some issues getting lamp installed correctly on my ibex desktop. Turning to the web for information I found a article repeated in many places claiming setting up a lamp stack in 15m. The sum of the article was "install ubuntu server"...long story short (or is it to late for that?) that and my own ignorance of linux lead me to the mess that I posted.

what saved me and I hope may save someone else looking to setup a LAMP development system should read this simple install guide 

[http://www.spoffle.com/technical/how-to-set-up-lamp-on-ubuntu-desktop-edition/](http://www.spoffle.com/technical/how-to-set-up-lamp-on-ubuntu-desktop-edition/)

this guy needs a metal, honor or, money even...

I will say I like Ubuntu a lot, my laptop was pre-installed with vista and after the service pack where installed it became so unstable that IE7 would freeze the computer prompting a hard reboot....glad to put that behind me.

---

### Post by jarviw on 2008-12-17
Well, just to let you know, the wl driver is buggy... see bug report here:
[https://bugs.launchpad.net/bugs/292450](https://bugs.launchpad.net/bugs/292450)

It causes random kernel panic -- I am not exactly sure about the mechanism, but it has been plaguing us for a while.

They just released the bug fix into the hardy-proposed repository with linux-restricted-modules-2.6.24_2.6.24.15-23.55

According to the launchpad tracking, it doesn't seem to be ported to Intrepid as yet.  But you might want to keep your proposed repository open for update.

---

### Post by Ayuthia on 2008-12-17
> **jarviw said:**
> Well, just to let you know, the wl driver is buggy... see bug report here:
[https://bugs.launchpad.net/bugs/292450](https://bugs.launchpad.net/bugs/292450)

It causes random kernel panic -- I am not exactly sure about the mechanism, but it has been plaguing us for a while.

They just released the bug fix into the hardy-proposed repository with linux-restricted-modules-2.6.24_2.6.24.15-23.55

According to the launchpad tracking, it doesn't seem to be ported to Intrepid as yet.  But you might want to keep your proposed repository open for update.

Just beware that the proposed repository contains packages that are in testing still.  The packages are usually pretty stable, but it is not 100% guaranteed.

---

