---
title: "No Internet/Ethernet connection"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by JustGus on 2010-07-09
I've just returned home with a new media pc with Lucid installed and am going through configuration. I needed to assign a static IP and found a link that recommended uninstalling the network manager and rewriting settings  directly to the /etc/network/interfaces file. I did this and rebooted, but I've now totally lost my internet connection. I noticed that if I connect the pc directly to the modem the Ethernet led doesn't light up and I can't go into the network manager as it's no longer installed...and can't reinstall it as I can't get online!

Can anyone suggest how to fix this. I'm going nuts trying to fix this!

Cheers!

---

### Post by JustGus on 2010-07-09
> **JustGus said:**
> I've just returned home with a new media pc with Lucid installed and am going through configuration. I needed to assign a static IP and found a link that recommended uninstalling the network manager and rewriting settings  directly to the /etc/network/interfaces file. I did this and rebooted, but I've now totally lost my internet connection. I noticed that if I connect the pc directly to the modem the Ethernet led doesn't light up and I can't go into the network manager as it's no longer installed...

Cheers!
Ah - have got the Ethernet LED to light on the modem, but still can't get online. Have tried to ping google.com using network tools but get a msg saying it can't be found.

---

### Post by Iowan on 2010-07-09
Verify that the machine (interface) has an IP address with **ifconfig -a** If there is one (not avahi - 169.254.X.X), can you ping the modem? If that works, can you reach (ping) internet by IP address (74.125.95.99)?

---

### Post by JustGus on 2010-07-09
> **Iowan said:**
> Verify that the machine (interface) has an IP address with **ifconfig -a** If there is one (not avahi - 169.254.X.X), can you ping the modem? If that works, can you reach (ping) internet by IP address (74.125.95.99)?


Hmm.  When I run ifconfig, I get the following:
> zoom@zoom-desktop:~$ ``ifconfig -a
eth1      Link encap:Ethernet  HWaddr 90:e9:ba:de:a1:bb  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

zoom@zoom-desktop:~$ 


And when I try to ping 74.125.95.99 I get no packets transmitted or received.

What shd I do next?  Thanks for the advice.

---

### Post by Iowan on 2010-07-09
**ifconfig -a** is showing no IP address (and no eth0, either). I'd almost bet your */etc/network/interfaces* file is configured for eth0.
You can check **sudo lshw -C network** for more information on your interfaces. 

There are other threads about the interface number (ethX) climbing. That information is kept in */etc/udev/rules.d/70-persistent-net.rules* - which can be edited. I don't remember if cleaning up that file fixed the problem permanently.

---

