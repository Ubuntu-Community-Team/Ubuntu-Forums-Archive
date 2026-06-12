---
title: "dead network"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by smitty96 on 2009-07-11
As the title suggests, my computer`s networking has died for some reason. The  network and router are fine, and my computer IS connected to the network, but I can`t access anything. I can`t go on the local network or online. In firefox, there is literally no load time, as soon as I press enter or refresh it`s not able to find the server. If I reinstall, it works at first, but once I reboot, its dead again. I think it may have been caused by an update, because this didn`t happen before.Any help is appreciated. If you need more details, just tell me.
Thanks,
-Tim

---

### Post by philcamlin on 2009-07-11
sudo /etc/init.d/networking restart
try that :)

---

### Post by gombadi on 2009-07-11
smitty96 can you give us some more information about your setup.

The output of the following commands would be good -

```

cat /etc/network/interfaces
ifconfig -a

```

You say it works after a reinstall but not after a reboot. What networking is different between these times?

---

### Post by smitty96 on 2009-07-13
Well, its working after I reboot now, probably because I am ignoring all updates. I'll try updating and rebooting, but right now, the codes say:
cat /etc/network/interfaces:
```
auto lo
iface lo inet loopback
```
ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr 00:a0:cc:62:27:b8  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:ccff:fe62:27b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25826 errors:1 dropped:0 overruns:0 frame:0
          TX packets:33820 errors:4 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000 
          RX bytes:16800505 (16.8 MB)  TX bytes:35853988 (35.8 MB)
          Interrupt:21 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr f2:ec:19:03:94:58  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0f:66:ed:7e:07  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0F-66-ED-7E-07-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
I'm using a wired connection right now. I'll try sudo /etc/init.d/networking restart after it dies again. Thanks!

Edit: it seems my system auto-updated itself. Well, I'll try rebooting now.

---

### Post by smitty96 on 2009-07-13
Hmmmmm, I restarted, the update manager says I'm up-to-date, but my computer still works! This is a strange sensation... Have there been any updates in the past few days? Maybe its fixed...

---

### Post by smitty96 on 2009-07-16
Never mind, I disabled package downloads, so the update manager said i was up to date when i really wasnt. I guess I'll just live without updates until this is fixed, then... :popcorn:

---

