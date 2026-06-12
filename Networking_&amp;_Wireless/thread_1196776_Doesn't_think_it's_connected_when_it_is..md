---
title: "Doesn't think it's connected when it is."
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by statistic on 2009-06-25
So I'm running hardy with xfce on my laptop, and right now as I type this it seems to think it's "Requesting a network address from the wired network".

Only as you may be aware I obviously have internet. I've hit the hardware switch on my wireless card, so it shouldn't be operating. Here is my ifconfig output.
```
eth0      Link encap:Ethernet  HWaddr 00:1b:24:34:d4:f2  
          inet addr:192.168.9.88  Bcast:192.168.9.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:717 errors:0 dropped:0 overruns:0 frame:0
          TX packets:695 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:761433 (743.5 KB)  TX bytes:166881 (162.9 KB)
          Interrupt:18 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2300 (2.2 KB)  TX bytes:2300 (2.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:2d:51:b2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-2D-51-B2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
I had to uncheck the "work offline" option in firefox to get here. I was having similar problems with my home wireless an hour ago. I've tried a reboot, but if anyone knows how to get the manager to resync back up, that would be great.

Thanks.

---

### Post by philcamlin on 2009-06-25
upgrade to 9.04 its better supported and there might be a fix for what your problem is :P

---

### Post by statistic on 2009-06-25
> **philcamlin said:**
> upgrade to 9.04 its better supported and there might be a fix for what your problem is :P

Well considering I'm running the LTS and Jaunty will be outdated about 3 years before hardy will, I don't think that upgrading is really the best solution.

---

### Post by statistic on 2009-07-04
Bumping my thread out of frustration.

So the problem seems to be more troublesome than I originally thought. I originally attributed it to being network-manager's fault so I removed the applet from my computer and just started using dhclient3, however it seems to have similar issues. It gets DHCP jsut fine, but every minute or so my connection will lag for about 4 seconds then resume as if nothing happened. My ssh sessions will hang usually then resume and catch up on all the lagged keystrokes, but it's frustrating as it continues to happen.

If anyone knows about a possible bug that could cause this. It seems to be happening over my wireless and my wired connection.

(I fail to see what a dist-upgrade would do to fix my networking issues.)

Thanks,

---

### Post by superprash2003 on 2009-07-04
post output of **route -n**. you could bring down wlan0 and wmaster0 if you are not using it.. you can do that by typing the following command
sudo ifdown wlan0
sudo ifdown wmaster0

---

### Post by statistic on 2009-07-04
> **superprash2003 said:**
> post output of **route -n**. you could bring down wlan0 and wmaster0 if you are not using it.. you can do that by typing the following command
sudo ifdown wlan0
sudo ifdown wmaster0


Thanks for the reply. I can get you that info when I get back to work on Monday. It's my laptop that I use at work that's doing it, and because my rather odd living situation at the moment (being that the wireless router for the house is in a locked room) I don't have access to a wired connection. I'll post the results of that first thing Monday morning.

Thanks again.

---

### Post by statistic on 2009-07-06
Well here's the output, it didn't seem happy to try to ifdown the interfaces, I suppose it's because they're not connected to anything at the moment.

```
mlindsay@portApotty:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
mlindsay@portApotty:~$ sudo ifdown wmaster0
ifdown: interface wmaster0 not configured
mlindsay@portApotty:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.9.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.9.1     0.0.0.0         UG    0      0        0 eth0
```

---

### Post by statistic on 2009-07-13
Bump for much help please. I do pretty much all my work over an ssh connection, the 5 second hang every couple of minutes is driving me absolutely insane.

It's not just the ssh either, if accessing a website while it's having one of it's "moments" it will tell me the server is not found, then I retry 5 seconds later and it's fine. I'm sure it's not a laggy connection, since I'm currently the only one on this network, and the machine I'm accessing is within spitting distance. I actually get a more reliable connection to it from my home PC.

---

