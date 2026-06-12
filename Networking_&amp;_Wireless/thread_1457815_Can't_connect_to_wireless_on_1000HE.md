---
title: "Can't connect to wireless on 1000HE"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by Conf on 2010-04-19
Hey,
I've recently installed ubuntu 9.10 for the first time on my Asus 1000HE and I can't connect to my wireless.
I first tried it using the default network manager program, it would display the nearby wireless networks but when I entered in my password and clicked on connect it would try for a minute and then just stop, I believed it wasn't properly encrypting my password so I decided to uninstall and then install wicd, but wicd is doing the same thing. I can see nearby wireless networks but it doesn't connect, even though I know the password I'm using is correct.

I've been looking around for an answer for the last few days and I've tried many different things to no avail, so I've pretty much given up, but I thought I'd try here as a last resort. Hopefully someone here will know how to fix it or else I'll just have to go back to Windows =/.

I've got a Atheros AR928X Wireless Network Adapter, if that helps,
and here is my output for: sudo ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:24:8c:48:1a:ec  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:43:71:58:b1  
          inet6 addr: fe80::222:43ff:fe71:58b1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:594 errors:0 dropped:0 overruns:0 frame:0
          TX packets:607 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67122 (67.1 KB)  TX bytes:93204 (93.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-43-71-58-B1-37-31-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```Thanks!

---

### Post by Conf on 2010-04-20
Also:

lspci | grep Network
```
01:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI Express) (rev 01)
```

And if I go into System>Administration>Hardware Drivers nothing shows up, it just says "No proprietary drivers are in use on this system", which I thought was weird.

---

