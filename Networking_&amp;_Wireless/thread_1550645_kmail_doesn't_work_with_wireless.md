---
title: "kmail doesn't work with wireless"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by pastro on 2010-08-11
Hi all,

I use kmail in kubuntu 8.04. Whenever I have a wired connection, kmail checks email and sends messages just fine. However, any time I switch to wireless, kmail just says "No new messages," without even checking. I am also unable to send email over wireless.

I've tried searching the internet for people with similar problems, but to no avail. Any help would be greatly appreciated.

Thanks!

---

### Post by McNils on 2010-08-11
Strange. I've never had a problem like that. What version of kmail are you using?

Does the network work for other programs when you use the wireless connection, like a browser?

---

### Post by pastro on 2010-08-11
Here's the output of kmail -v
Qt: 3.3.8b
KDE: 3.5.10
KMail: 1.9.10

Pidgin also does not work when I connect to wireless.

Maybe this clue is helpful: when I open firefox, it first thinks I am in offline mode, and I have to check File->WorkOffline before I can use the internet. After that, internet works.

Thanks!

---

### Post by McNils on 2010-08-12
I think this is a network problem rather than a kmail problem.

Check status of the network interfaces with **ifconfig**.

Check that there is a route to your gateway. **route -n**

---

### Post by pastro on 2010-08-14
These seem normal to me, right?

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:91:58:4b
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:75:d0:d7
          inet addr:192.168.1.45  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe75:d0d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4628 (4.5 KB)  TX bytes:5551 (5.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-75-D0-D7-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0

---

### Post by McNils on 2010-08-15
I dont think so. you seem to be missing the gateway. look at the last line. This is from my computer.

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
```

---

