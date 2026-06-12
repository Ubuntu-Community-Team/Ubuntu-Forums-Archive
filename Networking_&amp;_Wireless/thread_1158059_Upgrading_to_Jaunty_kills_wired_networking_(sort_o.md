---
title: "Upgrading to Jaunty kills wired networking (sort of)"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by R3M3 on 2009-05-13
I just upgraded to Jaunty (from Hardy using the update manager), and after the upgrade found that I couldn't get any internet access. I first noticed it with Synaptic hanging when updating package lists, but no internet also happens with Firefox and even ping. Curiously, when I boot into recovery mode "ping www.google.com" doesn't work with the "root prompt with networking", but it *does* work with the plain root prompt. (The "fix packages" option also has network access.)

So I'm left with a situation where activating networking disables it, but leaving it disabled allows it.

I'm connecting to the internet with an AT&T DSL modem (with one wired ethernet connection). While AT&T doesn't support linux, I was able to get it working by setting up the connection with Windows on another computer, and then connecting my Ubuntu box. Best I can tell, the modem stores login information internally, so I've never had to initiate a connection from within Ubuntu. (Although it's been a while, so I may have forgotten some setting or another I had to massage to get it to work.)

What would the netroot recovery boot option be doing which might be killing my internet access?

---

### Post by superprash2003 on 2009-05-13
in the normal mode, as soon as you boot up ( dont disable or enable anything ) , post output of **ifconfig **from the terminal.

---

### Post by R3M3 on 2009-05-13
I think I've got it.

I'm running off a xubuntu base, and it seems that xubuntu is now using NetworkManager (which was absolutely no help during troubleshooting). Once I installed gnome-network-admin, I saw that my eth0 connection was set to "Roaming mode enabled". Once I changed eth0 to dhcp, internet started working again.

In case you're wondering, here was the ifconfig results prior to the change:
```

eth0      Link encap:Ethernet  HWaddr 00:16:ec:77:f5:23  
          inet6 addr: fe80::216:ecff:fe77:f523/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:796 (796.0 B)  TX bytes:953 (953.0 B)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:900 (900.0 B)  TX bytes:900 (900.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:71.150.251.58  P-t-P:71.150.251.254 Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:170 (170.0 B)  TX bytes:94 (94.0 B)

```

After the change, I lose the ppp0 section, and gain a 
[INDENT]          inet addr:192.168.1.64  Bcast:255.255.255.255 Mask:255.255.255.0[/INDENT]
line under eth0

---

