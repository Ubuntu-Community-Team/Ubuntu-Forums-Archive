---
title: "Static IP broke after updates"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by backdoc on 2008-12-23
Up until an update a couple of days ago, I had no problems with my static IP and accessing the WAN (Internet).  Now, after reboot, the only way that I have found to get networking working again is to run dhclient.  I need a static IP.  So, I reset my IP with: ifconfig eth0 192.168.1.5 followed by /etc/init.d/networking restart.  This maintains the IP I want to use.  I have uninstalled gnome-network-manager and rebooted.  But, this did not help.  My /etc/network/interfaces file seems to be unchanged.  

This is desktop running 8.10.  In case you're interested, here's the contents of /etc/network/interfaces.

[INDENT]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
# name Main Ethernet Card
address 192.168.1.5
netmask 255.255.255.0
broadcast 192.168.0.255
network 192.168.1.0
gateway 192.168.1.1[/INDENT]

Any suggestions?

---

### Post by superprash2003 on 2008-12-23
post ifconfig output.. are you able to ping gateway ? 192.168.1.1

---

### Post by backdoc on 2008-12-23
> **superprash2003 said:**
> post ifconfig output.. are you able to ping gateway ? 192.168.1.1

Yeah, I can ping it now.  Everything works after I run dhclient.  I'll have to double check if I can ping it on fresh reboot, though.  I'll try it and post back.

My current ifconfig looks like this (I'll reboot and post a fresh ifconfig):

Note:  I'm running VirtualBox.  I think that's where pan0 comes from.

eth0      Link encap:Ethernet  HWaddr 00:15:f2:30:e4:28  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe50:e428/64 Scope:Link             
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1             
          RX packets:10652 errors:0 dropped:0 overruns:0 frame:0         
          TX packets:5789 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7225132 (7.2 MB)  TX bytes:1031377 (1.0 MB)
          Interrupt:21

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4788 (4.7 KB)  TX bytes:4788 (4.7 KB)

pan0      Link encap:Ethernet  HWaddr fa:37:23:35:da:5c

---

### Post by backdoc on 2008-12-23
> **superprash2003 said:**
> post ifconfig output.. are you able to ping gateway ? 192.168.1.1

Here are lots of more particulars, after a clean reboot.

ifconfig
[INDENT]eth0      Link encap:Ethernet  HWaddr 00:15:f2:50:e4:28
          inet addr:192.168.1.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe50:e428/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:575 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:179569 (179.5 KB)  TX bytes:92677 (92.6 KB)
          Interrupt:21

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:968 (968.0 B)  TX bytes:968 (968.0 B)
[/INDENT]

ping [www.yahoo.com](www.yahoo.com)
[INDENT]ping: unknown host [www.yahoo.com](www.yahoo.com)[/INDENT]

ifup eth0
[INDENT]ifup: interface eth0 already configured[/INDENT]

ping 192.168.1.1 (my gateway)
[INDENT]PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=150 time=0.692 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=150 time=0.658 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=150 time=0.650 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.650/0.666/0.692/0.034 ms[/INDENT]

ping laptop (a box on my LAN)
[INDENT]PING laptop (192.168.1.20) 56(84) bytes of data.
64 bytes from laptop (192.168.1.20): icmp_seq=1 ttl=64 time=1.34 ms
64 bytes from laptop (192.168.1.20): icmp_seq=2 ttl=64 time=1.20 ms
64 bytes from laptop (192.168.1.20): icmp_seq=3 ttl=64 time=1.36 ms

--- laptop ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2009ms
rtt min/avg/max/mdev = 1.207/1.303/1.363/0.080 ms[/INDENT]


netstat -rn
[INDENT]This output is a little hard to read inline, so I've attached the output.[/INDENT]

---

### Post by s3gfault on 2008-12-23
it looks like the problem is your dns.  Make sure you have everything disabled that may be messing with your /etc/resolv.conf file.  You should write this file by hand when you set a static ip address.  If something is messing with it, just take the w bit off of it, (chmod u-w /etc/resolv.conf) and that will lock it.

---

### Post by backdoc on 2008-12-23
> **s3gfault said:**
> it looks like the problem is your dns.  Make sure you have everything disabled that may be messing with your /etc/resolv.conf file.  You should write this file by hand when you set a static ip address.  If something is messing with it, just take the w bit off of it, (chmod u-w /etc/resolv.conf) and that will lock it.
I wonder what has changed.  This was working prior to the updates.

Looking at the /etc/resolv.conf file, it now tells you not to hand edit it.  There's a /etc/resolvconf directory.  Guess I'll dig around in there or google it.

root@xubuntu:/home/backdoc# cat /etc/resolv.conf
[INDENT]
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 999.999.999.99
nameserver 999.999.999.99
search mydomain_name.com[/INDENT]

---

### Post by backdoc on 2008-12-23
> **s3gfault said:**
> it looks like the problem is your dns.  Make sure you have everything disabled that may be messing with your /etc/resolv.conf file.  You should write this file by hand when you set a static ip address.  If something is messing with it, just take the w bit off of it, (chmod u-w /etc/resolv.conf) and that will lock it.

Fixed it.

I had to remove network-manager and then restart networking.  I removed the network-manager-gnome.  But, I missed the network-manager.  I haven't tried rebooting yet.  But, this is the first time that restarting networking has set my IP back to what I want my private IP to be.  So, I'm pretty sure this will fix it.

Here's a [link to the site]("http://shibuvarkala.blogspot.com/2008/12/howto-solve-static-ip-problem-in-ubuntu.html") that tipped me off.

Much thanks.

---

### Post by backdoc on 2008-12-27
I guess I spoke too soon.  Not only is my IP not static anymore, it spontaneously changed on me.

I'm back to square one.  I guess I can look at the resolv.conf file (which I haven't done yet).  But, I'm not thinking that's the problem because of the way it spontaneously changed addresses on me last night.  There seems to be an application running that thinks it's knows how my networking should be setup better than I do.

---

### Post by andguent on 2008-12-27
```
ps -ef|grep dhc
killall dhclient
ifdown -a;ifup -a
ps -ef|grep dhc
```

These commands will kill off any dhclient processes (DHCP client). If everything truely is set to static, then it really shouldn't be running, but it can cause this type of issue.

---

### Post by backdoc on 2008-12-29
You are right.  dhclient should not be running.  I tried to remove it with apt.  But, it's part of the ubuntu-minimal package and aptitude says that avahi depends on it.  I don't think I need avahi running either.  I might could remove it.  But, I don't want to use an axe when a scalpal will do.  I noticed there's an avahi-autoipd process running.  I wouldn't think I want any "autoipd" daemons running.

My question is, "What has changed between updates?"  I wasn't having a problem before updating.

---

