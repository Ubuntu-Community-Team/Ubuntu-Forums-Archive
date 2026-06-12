---
title: "I had my ethernet shared to another ethernet, but now all of the sudden It wont work"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by dracule on 2009-10-03
I followed this guide: 

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

To get my eth1 connection to share to my eth0 connection which was connected to my laptop. 

I changed nothing (i never shut off my desktop since i need it to constantly to do some stuff for all my projects). 

Anyways, so everything was great for about 4 days. then i woke up one morning, and my laptop wasnt getting intenet from the ethernet connection (the wireless is really really crappy where my laptop is, hence the ethernet connection sharing). 

So I switched my monitor over to my dekstop's feed, and clicked the network manager icon by the clock. it disappears (NetworkManager Applet 0.7.0.100). I logoff, log back on, the icon is back, but again when I click it, it disappears. So I decide it wont be that bad if I just give a full update and reboot. 

When I reboot, everything is there, and it stays active when I click the icon. It says eth0 isnt connected (eth1 is working and i have full internet access to the desktop). So I try to connect eth0, and it wont connect. 

So I look in the settings and make sure it is set to "share with computers" (before it wouldnt connect unless I had it set to this). It looks OK. So I go through the connection sharing guide again, nothing connects. I look at my laptop's network settings, nothing has changed. 


It is a big mystery. I cant figure out why eth0 wont make a connection. (on my laptop it says i am connected "local only").

---

### Post by Iowan on 2009-10-04
Perhaps some more background information. Shouldn't matter, but is laptop Windows? Post results of **ifconfig -a** and **route**.

---

### Post by dracule on 2009-10-04
the laptop is windows.

```

eth0      Link encap:Ethernet  HWaddr 00:**:08:2*:**:4*  
          inet6 addr: fe80::***:***:**2*:***a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4618 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:400906 (400.9 KB)  TX bytes:17257 (17.2 KB)
          Interrupt:11 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:08:**:54:77:**  
          inet addr:1**.7*.*1.**0  Bcast:1**.7*.*1.***  Mask:255.255.255.0
          inet6 addr: fe80::***:a****:**54:***c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:563634 errors:0 dropped:0 overruns:0 frame:0
          TX packets:385381 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:532123380 (532.1 MB)  TX bytes:63448610 (63.4 MB)
          Interrupt:5 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:73585 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73585 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:383977765 (383.9 MB)  TX bytes:383977765 (383.9 MB)

pan0      Link encap:Ethernet  HWaddr 26:03:41:ed:ed:6c  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
an * means i blocked it out.

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
1--.7-.-1.0     *               255.255.255.0   U     1      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         cisco31.----.   0.0.0.0         UG    0      0        0 eth1

```

and in this block a - means i blocked it out (so i wont confuse the reading of the gateway column.

---

### Post by Iowan on 2009-10-04
I probably should have requested **route -n** for numeric information, but... is cisco31.----. your internet connection? I presume your configuration is in */etc/network/interfaces* (since you have two active). Can the desktop access internet?

---

### Post by dracule on 2009-10-04
> **Iowan said:**
> I probably should have requested **route -n** for numeric information, but... is cisco31.----. your internet connection? I presume your configuration is in */etc/network/interfaces* (since you have two active). Can the desktop access internet?

yup. the desktop has full access. That is what Im using right now because my laptop's wireless is soooo slow (like 20kbps, and drops off all the time). So not being able to share my Ethernet is really getting frustrating. 

again

internet->eth1->desktop->eth0->laptop

where eth1 and eth0 are both on the desktop and eth0 is sharing eth1's connection to my laptop.

---

### Post by Iowan on 2009-10-05
The laptop is configured with address in same subnet as desktop's eth0 interface, and uses it as a gateway? (I suspect the guide mentions this - it's been awhile since I read it.)

---

### Post by dracule on 2009-10-06
> **Iowan said:**
> The laptop is configured with address in same subnet as desktop's eth0 interface, and uses it as a gateway? (I suspect the guide mentions this - it's been awhile since I read it.)

yup.

---

### Post by dracule on 2009-10-08
bump

---

### Post by Iowan on 2009-10-08
How is the eth0 address set - since it doesn't show an address in your post.

---

### Post by dracule on 2009-10-08
> **Iowan said:**
> How is the eth0 address set - since it doesn't show an address in your post.

manually, i followed the guide i linked perfectly so it is set through ifconfig

---

