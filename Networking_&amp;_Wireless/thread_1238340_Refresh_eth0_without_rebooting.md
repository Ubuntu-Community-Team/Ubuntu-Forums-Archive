---
title: "Refresh eth0 without rebooting"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by legendbb on 2009-08-12
How to restart eth0 without rebooting the machine?

After making changes to networking settings (or just sometime, after enable/disable wireless)in uBuntu, I'll have to reboot the machine otherwise the ethernet connection will not show up on the system bar.

Is there a way to "refresh" the eth0 without rebooting?

Tried, $sudo /etc/init.d/networking restart
won't do.

Thanks,

---

### Post by arch0njw on 2009-08-12
From the command line:
```
sudo ifdown eth0
sudo ifup eth0

```Let me know if that works for you.

---

### Post by legendbb on 2009-08-12
Thank you very much for you reply, I guess I'm step away from ifdown/up

msg: ifdown: interface eth0 not configured

right click the network icon on the system bar, Enable Networking is checked.

I got have to reboot then the Wired Networks will show up in the system bar icon.

after reboot, both wireless and wired will show up as eth0 & eth1
Before reboot, I can see eth0 in /sbin/ifconfig. But no ipaddr assigned, I assume that's mapped with wirless, no wired.

Thanks,

---

### Post by arch0njw on 2009-08-12
> **legendbb said:**
> Thank you very much for you reply, I guess I'm step away from ifdown/up

msg: ifdown: interface eth0 not configured

right click the network icon on the system bar, Enable Networking is checked.

I got have to reboot then the Wired Networks will show up in the system bar icon.

after reboot, both wireless and wired will show up as eth0 & eth1
Before reboot, I can see eth0 in /sbin/ifconfig. But no ipaddr assigned, I assume that's mapped with wirless, no wired.

Thanks,

Can you post the output of the following command?

```
ifconfig -a
```Also, please post the contents of your [FONT=Courier New]/etc/network/interfaces[/FONT] file.

---

### Post by legendbb on 2009-08-13
[COLOR=DarkGreen][COLOR=Red]ifconfig -a before reboot, no wired connection[/COLOR]

eth1      Link encap:Ethernet  HWaddr 00:23:4e:04:0f:4b  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr d6:51:98:e0:8f:ce  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[COLOR=Red]
ifconfig -a after reboot, Ethernet connection good[/COLOR]

eth0      Link encap:Ethernet  HWaddr 00:22:64:69:84:d3  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:64ff:fe69:84d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:817 (817.0 B)  TX bytes:4319 (4.3 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:23:4e:04:0f:4b  
          inet6 addr: fe80::223:4eff:fe04:f4b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr a6:11:d8:da:8c:0c  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[COLOR=Red]interfaces has only:[/COLOR]
auto lo
iface to inet loopback


[COLOR=Red]Great thanks,[/COLOR]

[/COLOR]

---

### Post by arch0njw on 2009-08-13
Uh... huh.  I have to admit to a limit to my knowledge here.  I'm not sure why eth0 isn't showing up for you and then, magically it does after a reboot...

---

