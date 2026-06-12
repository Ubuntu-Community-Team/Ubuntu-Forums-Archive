---
title: "thinkpad t60 wlan not working"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by calimerox on 2010-02-12
Hello everyone, i know that we had similar stuff like this quite often, but I just cant figure out how i can get my wlan working...

I m on karmic koala and newly installed the system on a thinkpad t60.

i get this output for my network connections:


> *-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:41:a9:6a:05
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=0.5-1 ip=192.168.0.8 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:ee000000-ee01ffff ioport:2000(size=32)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:b8:af:59
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:30 memory:edf00000-edf00fff



usually the t60 should work out of the box so i m not sure what to to and already searched all the posts .... i changed to the wcid client but also didnt help.. for using the wrapper I wasnt sure which driver i need to try but i tried some and they also couldnt find a wlan card... 

Thanks a lot for some help :)

---

### Post by Fire_Chief on 2010-02-12
> ***-network DISABLED**
description: Wireless interface
product: PRO/Wireless 3945ABG [Golan] Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlan0
version: 02
serial: 00:13:02:b8:af:59
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
resources: irq:30 memory:edf00000-edf00fff 

This adapter is showing disabled. Have you checked the hardware switch on the front of your T60 to verify it has the wireless network turned on? This switch controls both Bluetooth and WLAN devices in the laptop. 
Also, could be that wireless is turned off inside Ubuntu. Commonly, NetworkManager has the option to enable/disable Wireless and Wired connections from the Panel applet.
I have the same system on 9.10 working well with NetworkManager so if that doesn't fix it hopefully we can get this figured out.

Cheers!

---

### Post by calimerox on 2010-02-12
Thanks fire-chief, 

no, I actually can´t start the wlan with the hardware-switch, 
when I push the button nothing happens , where you would usually see a LED for the bluetooth and wlan devices... but nothing happens... is there a way to restart the network or to activate it somehow?

I now turned back to the network-manager...

so what else can I do?

edit: and: I cant even swich to wireless in the network manager, usually you can rightclick and enable wireless.. this is not possible here...

---

### Post by Fire_Chief on 2010-02-12
Maybe it's disabled in the BIOS?

---

### Post by calimerox on 2010-02-12
no, unfortunately not.. wireless is all enabled in bios. there was the FN keys disabled though, but it didnt make a difference enabling them, .... ;(
but i saw that the bios is from 2006, so  maybe i need to make a bios update(hopefully not, cause this is one of the things really threatening me...)?

---

### Post by Fire_Chief on 2010-02-12
Just to make sure it's not software related, can you boot from the LiveCD and verify that the Wireless works in the live environment?

---

### Post by calimerox on 2010-02-12
i ll give it a try and will let you know, thanks a lot for your help!

---

### Post by calimerox on 2010-02-13
Oh I was actually tooo stupid! The first advice you gave me looking at the hardware switch was it! I mixed it up with the function keys and thought you meant these...
I changed from a t41 to the t60 and this one had nothing like this.. 
shame on me.....

but still it doesnt work, I tried reinstall the network manager but I get this:

>   *-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:41:a9:6a:05
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=0.5-1 ip=192.168.0.8 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:ee000000-ee01ffff ioport:2000(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:edf00000-edf00fff

so the network now is unclaimed... 
is there a way to claim it? or do I have to unlock it during installation to get the right configuration?
Thanks for all your patience.....

---

### Post by calimerox on 2010-02-13
uff finally i got it! I messed up the configuration 
I guess, and then I got the hint in another post:

> 
 sudo modprobe -rv iwl3945

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

kalimerox@kalimerox:~$ sudo modprobe -v iwl3945

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
insmod /lib/modules/2.6.31-19-generic/updates/cw/cfg80211.ko 
insmod /lib/modules/2.6.31-19-generic/updates/cw/mac80211.ko 
insmod /lib/modules/2.6.31-19-generic/updates/cw/iwlcore.ko 
insmod /lib/modules/2.6.31-19-generic/updates/cw/iwl3945.ko 
kalimerox@kalimerox:~$ 



and everything was fine again... :) thanks...

---

### Post by Fire_Chief on 2010-02-15
Yay! Glad you got it working. If you would, please mark the thread as [SOLVED].

Cheers!

---

