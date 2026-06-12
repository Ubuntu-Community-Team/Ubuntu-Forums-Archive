---
title: "Internet works in Win7, not in 10.04, even though wifi connected."
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by WindmillGuy on 2010-08-12
Good day!
 
Today I got my laptop back after its motherboard was replaced (soundcard failure) and I am having problems connecting to the internet.
 
Connection to the wifi network is succesful, but Pidgin is not connecting ("SSL Connection Failed") and I can't view any webpages in Firefox. I loaded up Win7 and everything worked fine, connecting to the same wifi network and using the same proxy settings ("No Proxy").
 
Any suggestions?
 
I am still fairly new to all of this, so dumbed down instructions will be appreciated.
 
Thanks so much!
 
Francois

---

### Post by Kerubu on 2010-08-12
in ubuntu, start a Terminal window :

Applications->Accessories->Terminal

And then type:

ifconfig

Post the results here.

---

### Post by WindmillGuy on 2010-08-13
Okay, so below is the ifonconfig result, but something else happened. Yesterday after making my post I left my laptop running while I had to run some errands. When I came back after a couple of hours everything was working perfectly.
 
When I switched my laptop on again this morning, I got the same behaviour i.e. wifi connected, no internet. PIMA.
 
Suggestions?
 
Thanks!
 
****IFCONFIG OUTPUT****
eth1      Link encap:Ethernet  HWaddr 00:23:54:80:d5:66  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:31 Base address:0x2000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6256 (6.2 KB)  TX bytes:6256 (6.2 KB)
wlan0     Link encap:Ethernet  HWaddr 00:21:5d:37:bf:72  
          inet addr:10.0.0.12  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::221:5dff:fe37:bf72/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1001 errors:0 dropped:0 overruns:0 frame:0
          TX packets:229 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:190473 (190.4 KB)  TX bytes:25568 (25.5 KB)

---

