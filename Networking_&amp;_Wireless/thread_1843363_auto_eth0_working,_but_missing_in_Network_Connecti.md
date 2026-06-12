---
title: "auto eth0 working, but missing in Network Connections"
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by robot1125 on 2011-09-13
I installed Natty Server on an iMac, and it works perfectly, including my wired ethernet connection.

I then installed ubuntu-desktop, and ran Network Connections in order to convert the default connection from DHCP to static.  However, there are no entries at all, "auto ethX" or otherwise, in Network Connections.  I know I can edit /etc/network/interfaces manually, but I prefer the GUI tools.

Here is /etc/network/interfaces:

[INDENT]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp[/INDENT]

Here is output of ifconfig:

[INDENT]eth0      Link encap:Ethernet  HWaddr 00:16:cb:9a:cd:57  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cbff:fe9a:cd57/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13022 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11288045 (11.2 MB)  TX bytes:1205106 (1.2 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1888 (1.8 KB)  TX bytes:1888 (1.8 KB)[/INDENT]

And here is what I see in Network Connections:

[IMG]http://i.imgur.com/d1Qn3.png[/IMG]

Any ideas on how to fix this?

---

### Post by praseodym on 2011-09-13
Hi,

wireless and wired interfaces defined in the "interfaces" file are ignored by the NM. Try to remove eth0 from the file or try Wicd instead, it can handle it. You need to deactivate the network-manager in autostart if using wicd.

---

### Post by robot1125 on 2011-09-13
If I remove the eth0 entry from interfaces and reboot, I can see an entry in NM now, but oddly, if I edit it and select Manual, the save button is grayed out so I can't save the changes.  Very odd.

---

### Post by praseodym on 2011-09-13
Try it via

```
gksu nm-connection-editor
```

---

