---
title: "Completely lost with ndiswrapper...please help"
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by VTBuc on 2009-01-08
Okay, so this has been a nightmare. I tried everything I could with fwcutter but couldn't get that to work, so I'm trying ndiswrapper now and having just as much trouble.

I got the drivers from my laptop's recovery disk so I know that they're the correct drivers. Everything with ndiswrapper appears to have installed properly, except still no wireless. When I click Network Manager, it even has a place for "Wireless Networks" but no networks listed, despite the fact that I'm in range of about 10 wireless networks.

I've restarted, I've made sure my wireless card is physically on(function+f2) and still can't figure anything out. Please help!

---

### Post by cdtech on 2009-01-08
Could you post the output of both:
```
ifconfig
```
And:
```
ndiswrapper -l
```
And what version are you running?

---

### Post by VTBuc on 2009-01-08
```
sean@sean-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:1a:93:7a  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe1a:937a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7745 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7298 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7952508 (7.9 MB)  TX bytes:1207853 (1.2 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:31:78:d9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Memory:c0206000-c0208000
```

```
sean@sean-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: ssb)
```

And this is 8.10. Thanks!

---

### Post by cdtech on 2009-01-08
OK, try this. Open your modules file:
```
sudo gedit /etc/modules
```
and be sure your ndiswrapper module is listed "ndiswrapper"
Then open your blacklist file:
```
sudo gedit /etc/modprobe.d/blacklist
```
and comment everything to do with the b43:
```
# everything to do with wireless
blacklist b44
blacklist ipv6
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist agpgart
blacklist intel_agp
```

**UPDATE::.**
The b43 has been revised for the Intrepid release and works fine with my Broadcom BCM4311. I had to use the ndiswrapper for the Gutsy only. I just had to enable the b43 through "System > Admin > Hardware drivers"

---

### Post by VTBuc on 2009-01-08
> **cdtech said:**
> OK, try this. Open your modules file:
```
sudo gedit /etc/modules
```
and be sure your ndiswrapper module is listed "ndiswrapper"
Then open your blacklist file:
```
sudo gedit /etc/modprobe.d/blacklist
```
and comment everything to do with the b43:
```
# everything to do with wireless
blacklist b44
blacklist ipv6
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist agpgart
blacklist intel_agp
```

ndiswrapper was listed in modules.

In the blacklist file I #'d these lines:
blacklist bcm43xx
blacklist bcm43xx

Now what? :)

---

### Post by cdtech on 2009-01-08
reboot...........:D

Are you still there? Add this to your /etc/network/interfaces file:
```
auto wlan0
```

---

### Post by VTBuc on 2009-01-08
> **cdtech said:**
> reboot...........:D

Are you still there? Add this to your /etc/network/interfaces file:
```
auto wlan0
```

Rebooted and still nothing. I went ahead and added the "auto wlan0" line. Shall I reboot again or is there more? :)

---

### Post by cdtech on 2009-01-08
No just do a :
```
sudo /etc/init.d/networking restart
```
It should be listed within your "Network Manager" (enable wireless)

---

### Post by VTBuc on 2009-01-08
> **cdtech said:**
> No just do a :
```
sudo /etc/init.d/networking restart
```

Okay did that. Still no networks :(

---

### Post by cdtech on 2009-01-08
What do you get with :
```
sudo ifup wlan0
```

---

### Post by VTBuc on 2009-01-08
```
sean@sean-laptop:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
```

---

### Post by cdtech on 2009-01-08
Your almost there. Your driver is working its the network interfaces file. You need to add this:
```
iface wlan0 inet dhcp
auto wlan0
```
I'm trying to rush, my battery is low and I'm traveling. Need to go for now, hope this works for ya.........It sees it, just a configuration issue I believe now.........

---

### Post by VTBuc on 2009-01-08
> **cdtech said:**
> Your almost there. Your driver is working its the network interfaces file. You need to add this:
```
iface wlan0 inet dhcp
auto wlan0
```
I'm trying to rush, my battery is low and I'm traveling. Need to go for now, hope this works for ya.........It sees it, just a configuration issue I believe now.........

Okay...that definitely did something! I tried "sudo ifup wlan0" and here's what I got after adding that to the networks file.

```
sean@sean-laptop:~$ sudo ifup wlan0
ifup: interface wlan0 already configured
```

Also, now when I click Network Manager it says

Wireless Networks
device is unmanaged

Still no networks though. Whenever you get a chance I'd love to hear some advice. It's greatly appreciated. :)

---

