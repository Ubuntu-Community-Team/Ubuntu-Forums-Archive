---
title: "I broke my wireless connection"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by johnrobert on 2010-02-15
I've been struggling to connect to my home wireless network, but up until now my Broadcom card has been able to at least detect the network. I know this because in Network manager, in the Add Network Connection dialog box, if I tell it to scan for wireless networks then I see my home network along with all the other local wireless networks.

But in struggling to get Network Manager to actually make the connection, I have somehow managed to shut down my card and/or its operation. In Network Manager, scanning no longer shows any wireless networks at all.

Can someone help me get back to where I was when my home network was at least being detected? I know that the network is still running since I have other computers that can access it.

Thanks for any help.

---

### Post by Cabs21 on 2010-02-15
Are your drivers for the network card up to date?

---

### Post by johnrobert on 2010-02-15
Should be; I just installed a week ago and did all my updates after I installed. Like I say, it was detecting all the local wireless networks up until an hour ago.

More information: I think the problem occurred when I used Network Manager to "disable wireless" momentarily. I have now clicked the little toggle to enable wireless again, but it doesn't seem to be working. When I run 
```
iwlist scan
```
what I get back for eth1 is "Interface doesn't support scanning"

Here is the relevant output from lshw -C network

>   *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: c4:17:fe:47:f8:f7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f0a00000-f0a03fff

If I knew what Network Manager actually carries out when you click "disable wireless" I might be able to reverse it, but I don't know what the command is.

---

### Post by teward on 2010-02-15
lets try to manually reboot the interface, in terminal.
```

sudo ifconfig eth1 down up
```
that will take down the interface, and load it back up

If that doesn't work, make sure you don't have a wireless on/off hardware switch on your comp.  If you do, switch the switch to "ON".

---

### Post by johnrobert on 2010-02-15
Even more information. Here is the output of ifconfig for eth0 and eth1:

> eth0      Link encap:Ethernet  HWaddr 00:26:b9:21:02:a1  
          inet addr:192.168.0.249  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b9ff:fe21:2a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26475 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14853 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38843104 (38.8 MB)  TX bytes:1106917 (1.1 MB)
          Interrupt:36 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr c4:17:fe:47:f8:f7  
          inet6 addr: fe80::c617:feff:fe47:f8f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

---

### Post by johnrobert on 2010-02-15
Hi TrekCaptainUSA, thanks for the suggestion.

I tried that, but no joy. Iwscan still tells me that eth1 doesn't support scanning, and Network Manager can't find any wireless networks to connect to. Network manager shows my "enable wireless" option as grayed out.

My Dell Studio 15 does have a button on the keyboard (otherwise known as the F2 key) that shows an icon of a radio tower, and I thought about the possibility that I might have pushed it. But pushing it again now doesn't seem to do anything that I can detect through iconfig, iwlist, or Network Manager.

---

### Post by bkratz on 2010-02-15
Don't know if this is any help but see posting three

[http://ubuntuforums.org/showthread.php?t=1389617&highlight=radio+tower](http://ubuntuforums.org/showthread.php?t=1389617&highlight=radio+tower)


and another

[http://ubuntuforums.org/showthread.php?t=1337788&highlight=radio+tower](http://ubuntuforums.org/showthread.php?t=1337788&highlight=radio+tower)

---

### Post by johnrobert on 2010-02-15
Thanks bkratz, yeah it turned out to be the Dell wireless keyboard button, but for whatever reason I had to go back to Windows in order to turn the wireless back on. My home wireless connection is working fine under Windows, so I was able to know when the key was toggled to the right position and leave it while I rebooted back into Kubuntu. Now the local networks show up fine in Network Manager. Hurray.

Now I can get back to actually getting my connection to my home network working, now that Network Manager knows that there is a network there. Baby teps. Baby steps.

Thanks to everyone for their suggestions.

---

### Post by Cabs21 on 2010-02-16
mark as solved please

---

