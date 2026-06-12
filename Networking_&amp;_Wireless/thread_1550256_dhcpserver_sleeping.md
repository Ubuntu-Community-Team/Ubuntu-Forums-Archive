---
title: "dhcpserver sleeping"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by Sjoerd Mulder on 2010-08-10
Hi all,

Last week I installed ubuntu 10.4 (64bit)on a desktop pc. At first the wired internet ran fine, but I cannot connect anymore since my router had a reboot. My laptop with windows works however. 

I tried it with DHCP enabled AND manual configuration but still no luck. Doing **sudo dhclient** makes several attempts for **DHCPDISCOVER on eth0 to 255.255.255.255 port 67**, and then says **No working leases in persistent database - sleeping**

My setup is as follows: 
ADSL -- router w/dhcp (ip range 10.0.0.5-10) -- 2nd router w/dhcp (range 192.168.1.100-150) --ubuntu desktop
I can edit the settings in the second router, not in the first. Other (windows) desktops on the network work fine and as I said, also my Ubuntu desktop worked for three days. Things stopped working at once, after one time when a guest was using the internet (not the first time).

If I plug in the lan cable in my windows laptop, these are the auto-configured values: 
```

 Ethernet NIC
 Physical Address. . . . . . . . . : 00-26-22-44-A6-42
 Dhcp Enabled. . . . . . . . . . . : Yes
 Autoconfiguration Enabled . . . . : Yes
 IP Address. . . . . . . . . . . . : 192.168.1.101
 Subnet Mask . . . . . . . . . . . : 255.255.255.0
 Default Gateway . . . . . . . . . : 192.168.1.1
 DHCP Server . . . . . . . . . . . : 192.168.1.1
 DNS Servers . . . . . . . . . . . : 10.0.0.2

```

But when I enter these values in my network manager applet, it doesn't help. With dhcp enabled, ifconfig gives: 
```
eth0      Link encap:Ethernet  HWaddr 00:21:85:6f:5d:ef  
          inet 6 addr: 2002:a00:3:0:221:85ff:fe6f:5def/64 Scope:Global
          inet 6 addr: fe80::221:85ff:fe6f:5def/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16693 (16.6 KB) TX bytes: 15290 (15.2 KB)
          Interrupt:28 Base address:0x8000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scopte:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:26984 (26.9 KB) TX bytes: 26984 (26.9 KB)

```

My /etc/network/interfaces gives:
```
auto lo
iface lo inet loopback
```

I tried adding - to no avail:
```
auto eth0
iface eth0 inet dhcp
```

And also:
```
auto eth0
iface eth0 inet static
address 192.168.1.104
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

What can I do to make it work?

---

### Post by Sjoerd Mulder on 2010-08-10
Update: I uninstalled network-manager by doing sudo aptitude remove network-manager. This didn't solve it. But after doing sudo aptitude install network-manager I could not find the program on the taskbar anymore. So if you think that I should use it, please also tell me how to bring it back...
Installing it, it says 'Err [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid/main network-manager 0.8-0ubuntu3   Could not resolve nl.archive.ubuntu.com'.

---

### Post by dcollier on 2010-08-10
Should your dhcp and default gateway use the same ip address? It also looks as if you are trying to use ipv6, try ipv4

---

### Post by Sjoerd Mulder on 2010-08-10
Could you explain that a little bit more? How should I use ipv4? 

My dhcp server is my router, and my router is my gateway so yes, they are the same address. Or is that strange? It works in windows...

---

### Post by dcollier on 2010-08-10
check out this link, it show you how to disable ipv6

[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

---

### Post by Iowan on 2010-08-10
*/etc/network/interfaces* and Network Manager generally don't play well together - NM ordinarily doesn't manage interfaces defined in */etc/network/interfaces* (although this *can* be changed). If you re-installed NM, you may need to add a "Notification Area" to the top panel.
 A couple more threads that might be helpful:
[http://ubuntuforums.org/showthread.php?t=1484913]("http://ubuntuforums.org/showthread.php?t=1484913").
[http://ubuntuforums.org/showthread.php?t=1505217]("http://ubuntuforums.org/showthread.php?t=1505217").

[This]("http://ubuntuforums.org/showthread.php?t=1156441") is a similar problem/solution I had with a previous version.

---

### Post by Sjoerd Mulder on 2010-08-11
Ok I was stupid. Of course I cannot reinstall NetworkManager without online access..

But.... I did not manage to disable IP6 (and I still don't see why it would help).

And the last thread's solution didn't work for me either. 

Please note: I don't just have a DHCP problem, but cannot connect manually either.

Any solutions?

---

### Post by Sjoerd Mulder on 2010-08-11
Ok thank you all.

I solved it by installing another network card. I figure it was either a corrupt driver or a broken onboard network card. But hey, as long as I have a drawer full of spare network cards, I don't care.

---

