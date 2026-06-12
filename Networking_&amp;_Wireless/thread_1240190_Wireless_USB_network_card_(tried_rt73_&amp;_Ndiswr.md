---
title: "Wireless USB network card (tried rt73 &amp; Ndiswrapper)"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by toastermm on 2009-08-14
I have been working to get my wireless card working on my ubunty (Jaunty) setup with no success.

Here's the information:

I have a x86 Jaunty system.  My usb wireless card is a linksys/ralink model# wusb54gc.

Supposedly rt73 drivers work out of the box with this.  Not for me.  That was the first thing I tried but the computer does not recognize it.

So I undid everything and tried the ndiswrapper route.  I followed this tutorial:  [Ndiswrapper Tutorial]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapperl")

Right now, I'm running a 40 foot ethernet cord to the computer and have told my roommates that it's temporary.  Let's hope so.

Any ideas?


Here is the output from the command ifconfig as of now:
```

Me@Computer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:6f:38:da  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:fe6f:38da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:816 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:766056 (766.0 KB)  TX bytes:116663 (116.6 KB)
          Interrupt:252 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29279 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29279 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8240035 (8.2 MB)  TX bytes:8240035 (8.2 MB)

```

---

### Post by toastermm on 2009-08-14
ps-  I also know that the device is working because it works on a windows computer immediately.

---

### Post by Bucky Ball on 2009-08-14
Plug in a cable if you haven't already and get all updates. If there are any restricted drivers required for your card it will be picked up and they will be offered.

I know, catch 22. You need to download the drivers to get online!

This may not be your problem, of course, but it has worked for many.

---

### Post by toastermm on 2009-08-14
> Plug in a cable if you haven't already and get all updates. If there are any restricted drivers required for your card it will be picked up and they will be offered.

Thanks. There actually were some updates.  But sadly, no wireless or restricted driver updates.  Still the same output for ifconfig and no wireless options anywhere.

---

### Post by Bucky Ball on 2009-08-14
Plug the card in and post the result of:

iwconfig

Do you have the details of the access point (AP) you are attempting to connect to? It could be working already but wrong details so no go. Is the blue light on? (if there is one ...). If you looking in System->Admin->Hardware Drivers, is there a wireless driver in there unchecked?

In the ifconfig you gave in earlier, the card is not there at all. You are looking for wlan0. eth0 is your cable connection.

---

### Post by toastermm on 2009-08-14
> **Bucky Ball said:**
> Plug the card in and post the result of:

iwconfig

Do you have the details of the access point (AP) you are attempting to connect to? It could be working already but wrong details so no go. Is the blue light on? (if there is one ...). If you looking in System->Admin->Hardware Drivers, is there a wireless driver in there unchecked?

In the ifconfig you gave in earlier, the card is not there at all. You are looking for wlan0. eth0 is your cable connection.

Thanks for the quick reply again.

```

Me@Computer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

There is a light that lights up on the side of the usb stick, I have never noticed it on.  Also I did check the restricted driver list as you said and there is no option there for a wireless usb at all (The only restricted driver I have an option to use is the nvidia graphics driver, which I do use).

---

### Post by Bucky Ball on 2009-08-14
How about posting this file:

```
nano /etc/network/interfaces
```

Your USB wireless doesn't seem to be getting noticed. Hang on, try this:
```

lsusb
```

Can you see it there?

---

### Post by toastermm on 2009-08-14
```
Me@Computer:~$ nano /etc/network/interfaces
```
Contains the following:

> auto lo
iface lo inet loopback

```

Me@Computer:~$ lsusb
Bus 001 Device 007: ID 1737:0077 Linksys 
Bus 001 Device 002: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 1e3d:2092  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I'm pretty sure it's the first one:  Linksys.

---

### Post by Bucky Ball on 2009-08-14
Add this line to 
/etc/network/interfaces
```

auto wlan0
```... so it looks like this:

```
auto lo
iface lo inet loopback
auto wlan0
```You may need a bit more than that but try it. Yes, the Linksys is definitely there, unless you have any other Linksys USB devices plugged in.

After this change, reboot with the device plugged in at boot and see what happens.

---

### Post by toastermm on 2009-08-14
Thanks again. I added that line at the end of the file and here is the output from ifconfig and iwconfig.

```
Me@Computer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:6f:38:da  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:fe6f:38da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:303513 (303.5 KB)  TX bytes:61065 (61.0 KB)
          Interrupt:252 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:302 errors:0 dropped:0 overruns:0 frame:0
          TX packets:302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50705 (50.7 KB)  TX bytes:50705 (50.7 KB)

Me@Computer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

Still no wireless interface.  So I tried reinstalling the rt73 drivers, and no go.  I also checked the update manager, still no new updates or drivers available in the restricted driver section.

EDIT:  also lsusb gives the same thing.

---

### Post by toastermm on 2009-08-14
Anyone have the same problem?  Or even, lucky me, a solution?

---

