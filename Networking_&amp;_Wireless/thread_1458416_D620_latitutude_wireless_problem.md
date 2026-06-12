---
title: "D620 latitutude wireless problem"
date: 2010-04-20
forum: Networking &amp; Wireless
---

### Post by nitram9 on 2010-04-20
I just installed ubuntu on my d620.  The wireless card seems to exist and looks fine but I don't know how to turn it on.  It says the network is disabled everywhere I look but I can't find the option to turn it on.  I know this is probably simple.  Below is the output from various commands.  I included my service tag which you can use on the dell site to find specifics about my hardware.  Thank you very much in advance for any help you can give.

ifconfig does not show wlan0 and so I can't do ifconfig wlan0 up which is the only solution I've found online so far.


My service tag is 1P67PB1


iwconfig

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:dfdfc000-dfdfffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:48:e8:be
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=5752-v3.19 ip=192.168.1.124 latency=0 multicast=yes
       resources: irq:27 memory:dfcf0000-dfcfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:cf:3e:ea:91
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

 iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

---

### Post by pfnorris on 2010-04-20
Not sure if this will directly help you, but I am running Ubuntu on a Dell D630. That model has a small switch on the left hand side looking from the front, that can activate/deactivate the wireless device(s), including bluetooth I believe.

Might be worth a look just to check.

---

### Post by nitram9 on 2010-04-20
I just installed ubuntu on my dell latitude d620 (2006). The wireless card seems to exist and looks fine but I don't know how to turn it on. It says the network is disabled everywhere I look but I can't find the option to turn it on. I know this is probably simple. Below is the output from various commands. I included my service tag which you can use on the dell site to find specifics about my hardware. Thank you very much in advance for any help you can give.

ifconfig does not show wlan0 and so I can't do ifconfig wlan0 up which is the only solution I've found online so far.


My service tag is 1P67PB1


iwconfig

wlan0 IEEE 802.11bg ESSID:"" 
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated 
Tx-Power=0 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


lshw -C network
WARNING: you should run this program as super-user.
*-network 
description: Network controller
product: BCM4311 802.11b/g WLAN
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:0c:00.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=b43-pci-bridge latency=0
resources: irq:17 memory:dfdfc000-dfdfffff
*-network
description: Ethernet interface
product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:09:00.0
logical name: eth0
version: 02
serial: 00:15:c5:48:e8:be
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=5752-v3.19 ip=192.168.1.124 latency=0 multicast=yes
resources: irq:27 memory:dfcf0000-dfcfffff
*-network DISABLED
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:16:cf:3e:ea:91
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

wmaster0 Interface doesn't support scanning.

wlan0 Failed to read scan data : Network is down

---

### Post by bkratz on 2010-04-20
Well, it really doesn't seem to have the correct driver

[COLOR="DarkRed"]configuration: driver=b43-pci-bridge latency=0[/COLOR]

 which generally is the STA (wl)  driver for your card. You might want to look at this thread.  The b43 driver could also be used but is not generally.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by Iowan on 2010-04-20
Threads merged.
From Code of Conduct
> Please do not cross post, or post the same thing in multiple locations.

Thanks!

---

### Post by nitram9 on 2010-04-20
Thank you I am not a regular poster on internet forums so I don't exactly know the etiquette.  However I didn't get a reply from the post in the other forum so I thought maybe I should try this forum.  If there was a way for me to transfer that post to this one I would have.  How should I do this in the future?  Am I not allowed to ask the same question twice ever?  What happens when my post gets old and no one sees it any more but I still don't have a solution?  I'm not going to give up.

By the way the previous poster solved my problem.  Thank you

---

### Post by bkratz on 2010-04-20
> **nitram9 said:**
> Thank you I am not a regular poster on internet forums so I don't exactly know the etiquette.  However I didn't get a reply from the post in the other forum so I thought maybe I should try this forum.  If there was a way for me to transfer that post to this one I would have.  How should I do this in the future?  Am I not allowed to ask the same question twice ever?  What happens when my post gets old and no one sees it any more but I still don't have a solution?  I'm not going to give up.

By the way the previous poster solved my problem.  Thank you

The last important thing to do is to go to the thread tools and mark the thread [solved] in case it helps someone else.
Glad you got it!

---

### Post by Iowan on 2010-04-21
> **nitram9 said:**
> How should I do this in the future?  Am I not allowed to ask the same question twice ever?  What happens when my post gets old and no one sees it any more but I still don't have a solution?The "Report abuse" icon at the lower left (below username and avatar) can be used to contact a moderator - you can use that to request threads/posts moved or deleted (in addition to spam, or other undesirable behavior).
If no one responds to your post, you can "bump" it (reply to your own thread) - good manners dictates no more than once/day.

---

