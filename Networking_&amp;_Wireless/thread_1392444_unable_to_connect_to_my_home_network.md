---
title: "unable to connect to my home network"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by SoVaTraffic on 2010-01-28
ok i have no idea how to use ubuntu yet, just changed my OS from XP to Ubuntu and it won't let me connect to my home network with 9.10. i am using a linxus wireless chip please help

---

### Post by SoVaTraffic on 2010-01-28
i should also say that the computer running the network is an XP home edition. further information is that the wireless router is a linksys wireless-g broadband router

---

### Post by chewearn on 2010-01-28
Left-click on network icon (top-left corner), do you see a list of detected wireless networks?

---

### Post by wimux on 2010-01-28
Hello everybody,

I've got a similar problem.
I want to switch from XP to Koala.
I have a wireless USB-dongle; Linksys WUSB600N, that operates on the 2,4GHz band.
My modem router is also a Linksys (WAG 160N) (N-draft).
With XP everything works fine.

Since Knoppix, I'm trying to get Linux to work properly with Internet,
Hardy doesn't work with internet, Ibex the same thing, now i'm trying Koala.

I seem to need a driver for my dongle, but Linksys doesn't support Linux Ubuntu.
Can anybody help me please!?

P.S. I'm not very familiar with Ubuntu yet, but I'm very charmed of it.

---

### Post by -glow- on 2010-01-28
Ubuntu and wireless .... ive got that problem too : ( im trying it since version 6 or so...   
i have 4 wireless cards here and not even one works out of the box...they all find networks but wont accept the passphrase...(at least it looks like, maybe there is another bigger problem which i cant see i dont know)  
  
Kubuntu accepts all of my wlan cards out of the box...curious isnt it?   

But Kubuntu dont  accept my software raid, and i guess the wlan card is a minor problem compared to that : P
 So i have to solve this wlan problem too... I hope someone can help :(     

i cant believe im the only one with that problem...there seems to be something wrong with ubuntu

---

### Post by Comtronix on 2010-01-28
Same problem here, Ubuntu will not connect to Linksys network.
However, I'm using Ubuntu Live CD, if that makes any difference.
 
Yes, left click and all networks are shown. No Joy!
 
Linksys network is unsecured and connects from my Gateway notebook every time from Vista. Never connects to Linksys with Ubuntu. Will attempt connection to other secured networks, asking for password. But never connects to unsecured Linksys network.

---

### Post by chewearn on 2010-01-28
> **wimux said:**
> 
*edit*


> **-glow- said:**
> *edit*

> **Comtronix said:**
> *edit*

Sorry guys, it will be extremely helpful if you could create your own thread for the problems (one thread per problem).  Else we will be posting on top of each other and make it more difficult to solve.  Plus, more people will notice the thread on it's own.

If you need my help, post a link here after you have created a thread (though I'm not an expert in solving wireless issues, so no guarantee).

---

### Post by -glow- on 2010-01-28
guess you are right.

ok guys follow me :D

---

### Post by SoVaTraffic on 2010-01-28
negative, no networks are shown sir

---

### Post by chewearn on 2010-01-28
Run this command and post the output here.
```
lshw -C network
```

Note: 
This command will show all detected network device.
To aid reading, enclosed the output between [noparse]```
 
```[/noparse]

---

### Post by SoVaTraffic on 2010-01-31
```
*-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: a1
       serial: 00:40:ca:7e:a4:23
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=192.168.1.103 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:22 memory:ed087000-ed087fff ioport:d000(size=8)
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:18 memory:ec010000-ec011fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:23:69:6f:b9:3a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

---

### Post by pdc on 2010-01-31
-

---

### Post by chewearn on 2010-02-01
Ok, the info shows you have Broadcom BCM4318.  I find the following troubleshooting guide for your wifi:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

If you are confident, go ahead and follow the guide.  If not, I will aid you step-by-step.

First, we need to find the pci-id of the wifi.  Post output of this command:
```
lspci -nn | grep BCM43
```

---

