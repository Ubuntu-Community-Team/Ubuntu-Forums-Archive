---
title: "D-Link DWA-130"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by andjustmaybe on 2009-12-13
I just recently installed ubuntu 64-bit and i cant find my wireless network. i think it might be a driver problem but am not sure. I use a D-Link DWA-130 wireless usb router. Thanks 

ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:26:18:7b:9c:c2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B 
```

---

### Post by bkratz on 2009-12-13
I use the DWA-130, but I did not know they had 64 bit drivers available.  Are you sure yours are?

---

### Post by andjustmaybe on 2009-12-13
Yeah i have 64-bit drivers. I got a CD with the modem and it had separate 64 and 32 bit drivers on it.

---

### Post by bkratz on 2009-12-13
> **andjustmaybe said:**
> Yeah i have 64-bit drivers. I got a CD with the modem and it had separate 64 and 32 bit drivers on it.

Which version do you have--the A1,B1,C1 or D1
(it is on the label)

---

### Post by andjustmaybe on 2009-12-13
The C-1

---

### Post by bkratz on 2009-12-13
The C1 version doesn't appear to have Linux drivers (just the B) so you will have to use ndiswrapper and the windows drivers. It looks like they are called net8192u.inf and rtl8192.sys. I downloaded the software.

With you wired connection go to System---Administration--Synaptic package manager and search for Ndisgtk. It will find three files, check these off and tell it to load them.

After this,  put those two files somewhere (mine are in my home folder) Plug in the usb dongle  and go to System---Administration--windows wireless drivers and tell it to install a new driver---pointing it at the .inf file (wherever you stored it). 
It will first say hardware not found ignore it. And if you press configure the network it will say tool not found ignore that too.
It will eventual show up if the drivers are correct versions.
Go to System--Preferences--Network connections and set up your network connections.  Right now something in 9.10 is preventing you from using encryption so remove it from your AP for now.  Hopefully, it will be corrected soon.  Reboot the system.


Remove the wired connection and hopefully enjoy the wireless.
If you want to make sure that your device has been found correctly you can go to the terminal   Applications---Accessories---Terminal and type in lsusb (LSUSB) in lowercase and it should show up.

I will subscribe to the thread and check up later.


You might want to read this--apparently a lot of users have problems with the C version.
[http://forums.dlink.com/index.php?topic=8667.0](http://forums.dlink.com/index.php?topic=8667.0)

---

### Post by andjustmaybe on 2009-12-14
That helped a lot i was able to get it to work.

Thanx.

---

### Post by bkratz on 2009-12-14
> **andjustmaybe said:**
> That helped a lot i was able to get it to work.

Thanx.



Please go to the thread tools at the top of the page and mark the thread solved, so someone else can benefit (and so I can find it again if needed, I hate to type that much!)

---

