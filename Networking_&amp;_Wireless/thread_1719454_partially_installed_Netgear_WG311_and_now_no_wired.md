---
title: "partially installed Netgear WG311 and now no wired internet"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by Bossman7121 on 2011-04-01
Hi All, 

I've been a on again off again linux user for a while, but never really got into it full speed until a few weeks ago, after yet another windows issue. I installed 10.04 onto an old dell and its was running great, internet etc.. I then had my home desktop crash and said great, let me bring the dell home so the wife can use it. At home, i have a wireless card ( Netgear WG311 ) that I then installed into the Dell. Being that she was needing to use it online right away, I searched for the first install as it was not detected, and used used synaptic to install the bcmwl-kernal-source as that was the prefer ed driver for Netgear. So now that I  installed that, not only have I not fixed the wireless issue, I now have no wired internet.  I've been searching and re reading as many steps as I can, but am running out of time as she needs the computer tomorrow. 

Installed the ndwrapper ? but was not able to actually get the driver installed. 

All the other threads seem to be older ubuntu versions, and maybe its just me but the slight variation from one to the nex has me a little confuzed. 

from some of the other threads, I posted some of the command outputs, but could really use some help getting the driver installed as well. 

mike@mike-desktop:~$ sudo lshw -c network
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 4
       bus info: pci@0000:01:04.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:fe9e0000-fe9effff memory:fe9f0000-fe9fffff
  *-network:1
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth0
       version: 01
       serial: 00:11:43:7f:1f:65
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:17 memory:fe9de000-fe9dffff memory:40000000-40003fff(prefetchable)
mike@mike-desktop:~$ 

Thanks in advance ... and please save my marriage ! ! !lol

---

### Post by Bossman7121 on 2011-04-02
Got the wireless workign last night, but now the machine puts itself into either sleep or a hibernate mode randomly. I am getting really frustrated with this. I understand the learning curcve, but wow. Its one thing to learn a new os but to also have to learn scripts, programming language. 

Need help please !

---

### Post by Enigmapond on 2011-04-02
Go to Preferences/Power Management and tell it not to sleep....

---

### Post by Bossman7121 on 2011-04-02
Thank you..
was already set to not sleep and also disabled the monitor sleep. I replaced the battery, reset the times etc.. 

Any help on the wg311 issue? I had it working last night, and upon the machine restarting, it does not automatically load I used the writeup from 

[http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/](http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/)

This is what got me working. I attempted the script, but don;t think I worked.

---

### Post by Bossman7121 on 2011-04-02
I run this command to get the internet working

$ sudo ifconfig wlan0 up

---

