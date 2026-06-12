---
title: "Need help configuring DHCP server to work"
date: 2010-11-23
forum: Networking &amp; Wireless
---

### Post by greengunboat on 2010-11-23
Hello,
I have an extra desktop with Ubuntu 10.04, so I decided to turn it into a router (so I can connect to the internet with my laptop).  I was using the network manager to create a wireless network, but it was ungodly slow (when it decided to work), so I decided to setup something a little more professional. I have the net hooked up through my ethernet port, and I wanted to share the net using my wifi card.

I decided to use webmin to help set things up, and I have it installed successfully. I began to configure my computer using the tutorial found here:

[http://coroketon.wordpress.com/2008/01/20/setup-your-computer-to-be-a-router/](http://coroketon.wordpress.com/2008/01/20/setup-your-computer-to-be-a-router/)

It went sorta smoothly, except for the bootup command script and setting up my DHCP server. The bootup script didn't quite work, so I googled a bit, and instead of using this:
/bin/echo 1 > /proc/sys/net/ipv4/ip_forward
/sbin/iptables-restore /etc/webmin/firewall/iptables.save

I used this instead:
/bin/echo 1 > /proc/sys/net/ipv4/ip_forward
/sbin/iptables-restore /etc/iptables.up.rules

**I am not sure what that really does... could be jacked up.

Now when I go to the part where I had to startup my DHCP server, I get:
 * Starting DHCP server dhcpd3
 * check syslog for diagnostics.
   ...fail!

So my question is, where is the syslog, and what do I do next to get this thing to work.

Here is the output of ifconfig -a:
eth1      Link encap:Ethernet  HWaddr 00:21:85:1c:a5:3f  
          inet addr:174.49.139.148  Bcast:174.49.139.255  Mask:255.255.254.0
          inet6 addr: fe80::221:85ff:fe1c:a53f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21091 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4561411 (4.5 MB)  TX bytes:1006319 (1.0 MB)
          Interrupt:26 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1236966 (1.2 MB)  TX bytes:1236966 (1.2 MB)

wlan1     Link encap:Ethernet  HWaddr d8:5d:4c:d6:75:ef  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::da5d:4cff:fed6:75ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30729 (30.7 KB)  TX bytes:93486 (93.4 KB)

I do most of my work on my laptop, and I really need to get it hooked back up to the net, any thoughts or suggestions would be greatly appreciated... thanks!

---

### Post by greengunboat on 2010-11-24
Ok, that first tutorial sucked. If anyone has the same problems, definitely use this tutorial:

[http://ubuntuforums.org/showthread.php?t=926001](http://ubuntuforums.org/showthread.php?t=926001)

It uses webmin, but it is explained in so much more detail. Of course once I updated ubuntu, it broke my network connection settings... and I had to redo it... but I am use to that with ubuntu by now....errr.

---

