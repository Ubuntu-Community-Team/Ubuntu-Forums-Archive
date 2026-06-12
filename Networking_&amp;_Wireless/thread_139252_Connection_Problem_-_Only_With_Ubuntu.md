---
title: "Connection Problem - Only With Ubuntu"
date: 2006-03-03
forum: Networking &amp; Wireless
---

### Post by deniro0311 on 2006-03-03
I am fairly new to Ubuntu, which I love.  However, I have a weird connection problem that I have never faced before, and I can't figure it out.  Basically, I can't connect with a static IP, and I have everything configured as I always do.  I have a nForce 4 chipset with dual gigabit ethernet.  It has a nvidia ethernet controller and a marvell yukon controller.  My network is behind an IPcop firewall/router which provides me dhcp (which I don't use) and dns.  IPcop is not the problem.  My server is online, my windows box is online, and when I use one of my live cd's I can get online (dhcp and static).  If I use the dhclient command I can get online.  Just now I was able to get online by configuring for dhcp in the gui network tool, which didn't work before.  With all this being said I still can't connect statically.  I can ping myself, my router, and thats it.  I know it sounds like a missconfiguration on my behalf, but I have checked them about twenty times.  Maybe it is a driver issue, or does Ubuntu require some special settings I am not aware of.  I also disabled ipv6.  I believe this might be what fixed the dhcp problem.  Any help would be greatly appreciated.

---

### Post by jamesr on 2006-03-03
How did you disable ipv6?

Did I understand that you said you need only to use the sudo dhclient get on-line
> If I use the dhclient command 

Post the output of 
```
sudo ifconfig -a
```
before and after activating dhcp

---

### Post by deniro0311 on 2006-03-03
I can't remember for the life of me how I disabled it.  I found the instructions by doing a search in the forum for ipv6.  As fas as dhclient goes, I no longer need to do that.  I can set up dhcp normally, but I still can't get a static address.  The following is the output for dhcp first (which works) and static second (which doesn't).  I hope it helps.  Thanks for the help by the way.

eth0      Link encap:Ethernet  HWaddr 00:01:29:D2:DE:81
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:01:29:D2:DE:E5
          inet addr:192.168.1.189  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6008 (5.8 KiB)  TX bytes:2742 (2.6 KiB)
          Interrupt:5

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:936 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:84034 (82.0 KiB)  TX bytes:84034 (82.0 KiB)

eth0      Link encap:Ethernet  HWaddr 00:01:29:D2:DE:81
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:9 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:01:29:D2:DE:E5
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:562 (562.0 b)  TX bytes:362 (362.0 b)
          Interrupt:5

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3652 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3652 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:332170 (324.3 KiB)  TX bytes:332170 (324.3 KiB)

---

