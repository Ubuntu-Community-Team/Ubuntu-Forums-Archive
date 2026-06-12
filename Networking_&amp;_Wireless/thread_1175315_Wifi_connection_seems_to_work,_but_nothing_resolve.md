---
title: "Wifi connection seems to work, but nothing resolves"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by parkerhiggins on 2009-06-01
Hello!  I'm having something of a complex problem.  I don't know how many of these things are related:

About two weeks ago, after experiencing a number of wifi issues, I installed linux-backport-modules-jaunty, which seemed to cure all of the problems I was having with WPA2 networks.  That worked great for about a week.

Last week, I started to notice that sometimes, even though my wifi was connected and showed signal, no internet traffic would resolve.  It seems like it's a DNS issue, but all of my DNS information is good!  A few times I could get it to fix itself by manually turning disabling and re-enabling wireless in the Network Manager, but that seems to work less and less often.

When I restart networking with /etc/init.d/networking restart, I sometimes (but not always!) get the message "Ignoring unknown interface wlan0=wlan0."  That started at the same time as my other wifi issues.

Finally, the same day I first started experiencing those issues, my system also started to occasionally hang.  When it does that, the capslock LED blinks, and nothing short of holding the power button can fix it.  Sometimes it happens after a lot of usage, sometimes just a minute, sometimes when I haven't been using it for a while, seems random.

Anyway, I know these are a lot of issues, but I'm hoping it's a pattern somebody else has noticed.

I'm including the results of lshw -C network, in case they're of use to somebody:

>   *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1f:16:02:f5:c0
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=1.8-3 ip=192.168.1.112 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:5d:7f:12:fc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.108 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fa:6d:87:9d:95:92
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by t0mppa on 2009-06-01
You should check your system logs (/var/log/syslog) after you get these freezes to see if some module crashed. I had my wireless drivers work for a few weeks as well and then they started crashing, causing a system freeze, where the lock leds kept blinking and power off, power on was the only course of action to proceed.

There was also a bug report of Network Manager causing crashes like this. If it's either of the following, simply swapping to another module that does the same thing (and posting/updating a bug report to help get it fixed) could solve all your problems.

---

### Post by superprash2003 on 2009-06-01
post output of ifconfig and contents of /etc/network/interfaces file

---

### Post by parkerhiggins on 2009-06-04
Thanks already for the help so far!

t0mppa, it sounds like your fix might do it for me.  How do I go about switching modules?

Just in case, superprash2003, I'm posting the results of ifconfig and interfaces, with the caveat that my sometimes-working wireless is working right now.  I'll check again if it stops working.

ifconfig:
> eth0      Link encap:Ethernet  HWaddr 00:1f:16:02:f5:c0  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:f2600000-f2620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26160 (26.1 KB)  TX bytes:26160 (26.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:5d:7f:12:fc  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5dff:fe7f:12fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19042 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20876797 (20.8 MB)  TX bytes:3453615 (3.4 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-5D-7F-12-FC-32-66-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


/etc/network/interfaces:
> auto lo
iface lo inet loopback

---

### Post by superprash2003 on 2009-06-04
you could try disabling ipv6 [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4) .. also try opendns servers - 208.67.222.222 and 208.67.220.220

---

### Post by t0mppa on 2009-06-04
> **parkerhiggins said:**
> t0mppa, it sounds like your fix might do it for me.  How do I go about switching modules?

Point simply was that if you find your driver module always causing a crash, swap to another driver. And if it's Network Manager module, there are other GUI's out there for managing connections (WiFi Radar, WICD & RutilT for instance). But just switching modules at random won't be very effective, you first need to find out what is causing the crashes and that info is easiest to find from syslogs.

---

