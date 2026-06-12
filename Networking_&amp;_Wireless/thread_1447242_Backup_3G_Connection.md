---
title: "Backup 3G Connection"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by gmansa on 2010-04-05
Hi

I currently have a ubuntu server running as gateway server (amongst other things). I use RP-PPPOE to establish a connection to the internet, and that connect an ADSL router to the internet. I would like to add a USB 3G modem that should become the internet gateway when there is problems with the ADSL connection. I use Shorewall as firewall.

What's the best way to do this?

---

### Post by gmansa on 2010-05-08
bump

---

### Post by alexfish on 2010-05-08
hi

don't know if this helps

with a 3g connection check your routes with ifconfig the P-t-P is the important bit

below is what I have 

ppp0      Link encapoint-to-Point Protocol  
          inet addr:10.198.69.195  [COLOR=Blue]P-t-P:10.64.64.64[/COLOR]  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:3148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2903 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2602324 (2.6 MB)  TX bytes:515813 (515.8 KB)


route -n

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
[COLOR=Blue]10.64.64.64[/COLOR]     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ppp0
0.0.0.0         [COLOR=Blue]10.64.64.64 [/COLOR]    0.0.0.0         UG    0      0        0 ppp0

---

