---
title: "Broadcom wireless stopped working"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by AKviking on 2009-10-21
My wireless on my laptop just suddenly stopped working yesterday.  The only thing I remember that has changed on my PC is that I installed WireShark, but I can't imagine that hosing me up like this.

I have a HP pavilion ze4900 laptop with a Broadcom BCM4306 wireless adapter.

It's been working flawlessly between home and work for some time now.  Yesterday at home I fired it up and the only WiFi AP it listed was the only unsecure one in the neighborhood.  Usually there's a list of about 6 (5 of which are secure).

Now it won't show any.  In fact when I check my network connections via the icon in the task bar, it won't show my wireless adapter.

[ATTACH]132662[/ATTACH]

Here's what I can see via the CLI.  Any ieas?   What am I missing?
```

akviking@ze4900:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:90:4b:92:c2:a4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
```

akviking@ze4900:~$ sudo iwlist wlan0 scan
wlan0     No scan results
```

```

akviking@ze4900:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:48:d4:50
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.19 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:92:c2:a4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```

---

### Post by Metaljaz on 2009-10-21
Check to see if you turned off your wireless by accident. There should be a switch on the front of the laptop.

---

### Post by AKviking on 2009-10-21
> **Metaljaz said:**
> Check to see if you turned off your wireless by accident. There should be a switch on the front of the laptop.

yep, that was my first choice.  Interesting thing about that button as well is that when Windows was on there, the button worked, but with Ubuntu the button does NOTHING.  However the little blue light that indicates that it's ON is lit up as it should be.

---

### Post by Metaljaz on 2009-10-22
Check system>administration>hardware drivers
and make sure that your broadcom driver is still being used.

---

### Post by AKviking on 2009-10-23
> **Metaljaz said:**
> Check system>administration>hardware drivers
and make sure that your broadcom driver is still being used.

Checked and double-checked.

I read elsewhere that someone else had lost their wireless connectivity after using Wireshark as ROOT.  It warns you of possible troubles with doing that, and I had no problems doing such with my desktop.  Well, I do not have wireless on my desktop.  I'm thinking this is the culprit and may involve re-installing Ubuntu.  Oh well, that just gives me more practice.  :)

I'll just have to find an alternate method of capturing packets here at work.

---

### Post by AKviking on 2009-10-24
Well it's working once again.  

Last night I wiped the drive and re-installed Ubuntu.  Unfortunately that did not fix it. Not sure if the WiFi had just died and that my efforts would be eternally futile, I reloaded (gasp) WindowsXP.  The WiFi worked.  So now I knew it was operational.

Okay, so round two of Ubuntu install.  Due to the card that I have, I have to use b43-fwcutter for installation of the drivers.  The first attempt that failed I installed b43-fwcutter with aptitude via the CLI.  This second attempt was using *synaptic*.  That's the only difference, and it works.

---

