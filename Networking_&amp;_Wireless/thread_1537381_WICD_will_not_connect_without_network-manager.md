---
title: "WICD will not connect without network-manager"
date: 2010-07-23
forum: Networking &amp; Wireless
---

### Post by worldgnat on 2010-07-23
I'm trying to use wicd instead of network manager because I want a "no fuss" way to use wireless on wmii. However, wicd will not find any networks unless network-manager has been run and has connected to a network since startup. If it hasn't connected to a wireless network, the wicd will find no networks, and iwlist won't provide a list of networks either. 

This seems to mean that network-manager is doing something to the interface when it connects that needs to be done to make it usable, but I'm not sure what it is or how exactly to find out. I do know that the interface (eth2) will not appear in ifconfig if network manager hasn't connected, which I assume means that it hasn't been brought up. ifconfig eth2 up makes it show up, but I still can't connect with wicd. What can I do?

I'm running Ubuntu 10.04, generic 2.6.32-22 kernel, MacBook 5,5 using the Broadcom STA driver. (more details below)

Thanks in advance,
-Peter

Relevant section of lshw -C network (while connected with nm):

 ```
 *-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth2
       version: 01
       serial: 00:25:00:4b:df:4c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.123 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:23 memory:d3200000-d3203fff

```

iwconfig (not sure why it says "Not-associated"; it's definitely associated):
```
lo        no wireless extensions.

eth4      no wireless extensions.

eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:4  Signal level:189  Noise level:166
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.
```

---

### Post by dca on 2010-07-23
I could've sworn network-manager and nm-applet had to be uninstalled prior to WICD installation or that WICD automatically removes nm?

---

### Post by worldgnat on 2010-07-23
That's what I thought too, but installing wicd didn't remove network-manager or even ask me if I wanted to remove it. When I removed it on my own it simply couldn't connect (even after re-installing wicd.)

---

### Post by Fremont_Cunningham on 2011-05-22
Acer Aspire 4530/AMD64/Maverick. External USB wifi not seen at all by NM.
Following general advice I uninstalled NM and installed Wicd.
After a fresh boot it can see either external or internal WiFi devices *BUT*
after a suspend/recover (a common operation for a laptop) the internal wifi device has vanished from lsusb, and Wicd sees no wireless network.

Is anyone still working on the general wifi /Wicd problems with UBUNTU. By Google search theres masses of problems and few solutions.

---

### Post by worldgnat on 2011-05-25
If the device is gone from lsusb, then it's not a Wicd issue, it's a hardware issue. I'm not sure what lsusb is actually querying, but I'd guess it's udev? You might try checking into udev issues with your device.

Edit: By the way, I managed to fix my original issue, but I forget exactly how. I believe I either purged network manager, or I used the brute-force OS repair method (fresh install.)

---

### Post by pattelin on 2011-05-26
Hi Worldgnat,

I have the same problem. I installed WICD, then uninstalled NM. wicd worked fine until I rebooted. Then I could not connect at all. Wicd displayed the wireless lans and even authenticated OK. But wicd was not able to obtain an IP address. :(


How exactly did you fix your issue?


Thanx

---

### Post by worldgnat on 2011-05-26
pattelin, I think yours is a different issue. If wicd is detecting the networks, then at least it's working to some extent. When I was using wicd on Maverick, there were some networks to which I could not connect at all, and I was never able to identify the problem (the networks in question were hotspots, so I usually just did without internet access.) However, perhaps it's a bug in wicd; what version of wicd do you have? Maybe try upgrading manually to the latest version?

---

### Post by pattelin on 2011-05-27
Hiya,


I have the latest version of WICD (I installed it with Synaptic).

I think I'll open a new thread with this issue.


Thanx
:D

---

### Post by worldgnat on 2011-05-27
pattelin,

Be ware: packages in Ubuntu repositories are not always the latest versions; in my experience they are usually one to two versions behind. Tryning the latest version is a bit of a shot in the dark, but it might be worth a shot anyway. Good luck.

---

### Post by pattelin on 2011-05-30
OK. I'll give it a try.

Thanx

---

