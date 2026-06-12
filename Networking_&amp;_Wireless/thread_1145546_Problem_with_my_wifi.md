---
title: "Problem with my wifi"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by dearingj on 2009-05-01
(using a friend's account since registering caused some kind of php error)

Hi,

I just recently decided to install ubuntu over my windows installation and so-far everything has been really great, except my wifi has been acting odd.

In windows my wifi would usually disconnect randomly around twice and hour but would automatically reconnect within 10 seconds or so - so I barely noticed it. Now, in ubuntu, it seems to be disconnecting every few minutes and will stay disconnected until I manually reconnect it. Then, it typically takes more like 30-60 seconds for it to connect. Around once a day it becomes impossible to reconnect (and it keeps asking for my password each time for some reason, even though its saved right there) and I end up rebooting to reconnect.

Its been getting worse and worse. When I first installed early this week it worked perfectly and now I can hardly keep the wifi going for more than 5 minutes without disconnecting.

A few details: when its connected its fast and responsive, it always says that I have a strong connection, my computer can find 21 other wifi networks in my immediate area (maybe some kind of radio interference, if that's possible?).

I would love to be able to solve the disconnecting problem altogether, but if that turns out impossible, is there at least any way to get ubuntu to automatically reconnect quickly when I get disconnected?

Thanks, I appreciate any help you can offer!

---

### Post by pastalavista on 2009-05-01
The details that would help the most would be the output of these commands in terminal
```
sudo lshw -c network
```and also ```
ifconfig
```

---

### Post by dearingj on 2009-05-01
Thanks for the help, here are the restuls:

------

thomas@thomas-laptop:~$ sudo lshw -c network
[sudo] password for thomas: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:26:f1:c8
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.10.199 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:15:30:44
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6e:0e:e6:c2:f7:af
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

-------

thomas@thomas-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:15:30:44  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27763 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27763 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4900494 (4.9 MB)  TX bytes:4900494 (4.9 MB)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:26:f1:c8  
          inet addr:192.168.10.199  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe26:f1c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:370986 errors:0 dropped:0 overruns:0 frame:0
          TX packets:315307 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:386922564 (386.9 MB)  TX bytes:197738287 (197.7 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-26-F1-C8-31-63-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Hobgoblin on 2009-05-01
> **dearingj said:**
> my computer can find 21 other wifi networks in my immediate area (maybe some kind of radio interference, if that's possible?).

Yes.

Try to choose a channel away from those used by the closest networks.

---

### Post by dearingj on 2009-05-01
Ok thanks. How can I figure out what channels they're on?

---

### Post by dearingj on 2009-05-01
Even if that's what is causing the disconnects, why doesn't ubuntu say that i've gone offline, or automatically reconnect?

---

### Post by pastalavista on 2009-05-01
I found this [on this post]("http://ubuntuforums.org/showthread.php?t=1139386&highlight=inet6"):

1. IPv6 is supported by default in Ubuntu and can sometimes cause problems.
2. To disable it, open a Terminal (Applications &#9656; Accessories &#9656; Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
4. Reboot Ubuntu.

From your lshw, it seems like this might fix your problem. Hope it helps.

If that doesn't work, try [this page]("http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html") and if that won't do it, maybe [this will]("http://ubuntuforums.org/showpost.php?p=2810501&postcount=17"). That's what I like most about Ubuntu... the programming is open and easy to fiddle with. I'm still an awe-struck noob at heart.

btw, the command for linux is ifconfig... not ipconfig.. that was for Windows

---

