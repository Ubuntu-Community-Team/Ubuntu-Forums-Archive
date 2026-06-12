---
title: "My Buggy PPPOE Connection in Jaunty"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by ZhuaSD on 2009-07-28
I have a regular problem, where I have to manually 'pon' to get my connection going when I start up, actually I first 'poff' then 'pon'.  When I 'plog' I get nothing at all at some times, like on startup.

But the bigger problem is sometimes the connection will just drop, and will not come back by itself.  It is really weird, existing connections will continue while new ones will not be successfully created, and finally all the connections will be dropped.

Before, in 8.04, I had to re-start each time.  It was a pain but I turn off my comp in the evenings, so it only bugged me once or maybe twice a day.

Now with 9.04, I have to poff and pon, and it works again.  This happens maybe once or at most twice a day, better than it was before.

So, could anyone take a look at my logs and give me some advice?  I started it up and this is what happened to get the connection started up (IP addy changed randomly:

```
Z68887@Z68887-desktop:~$ plog
Z68887@Z68887-desktop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1d:0f:1e:f3:fe  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:fff:fe1e:f3fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13966 (13.9 KB)  TX bytes:43591 (43.5 KB)
          Interrupt:16 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:916 (916.0 B)  TX bytes:916 (916.0 B)

Z68887@Z68887-desktop:~$ plog
Z68887@Z68887-desktop:~$ sudo poff dsl-provider
[sudo] password for Z68887: 
/usr/bin/poff: No pppd is running.  None stopped.
Z68887@Z68887-desktop:~$ sudo pon dsl-provider
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
Z68887@Z68887-desktop:~$ plog
Jul 28 20:45:53 Z68887-desktop pppd[4148]: Connect: ppp0 <--> eth1
Jul 28 20:45:53 Z68887-desktop pppd[4148]: PAP authentication succeeded
Jul 28 20:45:53 Z68887-desktop pppd[4148]: peer from calling number 00:03:42:8C:80:48 authorized
Jul 28 20:45:53 Z68887-desktop pppd[4148]: replacing old default route to eth1 [192.168.1.1]
Jul 28 20:45:53 Z68887-desktop pppd[4148]: Cannot determine ethernet address for proxy ARP
Jul 28 20:45:53 Z68887-desktop pppd[4148]: local  IP address 22.21.6.64
Jul 28 20:45:53 Z68887-desktop pppd[4148]: remote IP address 748.7.20.431
Jul 28 20:45:53 Z68887-desktop pppd[4148]: primary   DNS address 2XX.1XX.XX.X
Jul 28 20:45:53 Z68887-desktop pppd[4148]: secondary DNS address XXX.7X.XXX.XX
Z68887@Z68887-desktop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1d:0f:1e:f3:fe  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:fff:fe1e:f3fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:672 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19315 (19.3 KB)  TX bytes:58557 (58.5 KB)
          Interrupt:16 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:916 (916.0 B)  TX bytes:916 (916.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:22.21.6.64  P-t-P:748.7.20.431  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:429 (429.0 B)  TX bytes:2134 (2.1 KB)

Z68887@Z68887-desktop:~$ plog
Jul 28 20:45:53 Z68887-desktop pppd[4148]: PAP authentication succeeded
Jul 28 20:45:53 Z68887-desktop pppd[4148]: peer from calling number 00:03:42:8C:80:48 authorized
Jul 28 20:45:53 Z68887-desktop pppd[4148]: replacing old default route to eth1 [192.168.1.1]
Jul 28 20:45:53 Z68887-desktop pppd[4148]: Cannot determine ethernet address for proxy ARP
Jul 28 20:45:53 Z68887-desktop pppd[4148]: local  IP address 22.21.6.64
Jul 28 20:45:53 Z68887-desktop pppd[4148]: remote IP address 748.7.20.431
Jul 28 20:45:53 Z68887-desktop pppd[4148]: primary   DNS address 2XX.1XX.XX.X
Jul 28 20:45:53 Z68887-desktop pppd[4148]: secondary DNS address XXX.7X.XXX.XX
Z68887@Z68887-desktop:~$ 
Z68887@Z68887-desktop:~$ 
```

---

### Post by ZhuaSD on 2009-07-28
And my /etc/network/interfaces:

```

auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

auto eth1
iface eth1 inet dhcp
```

Just in case that helps

---

### Post by superprash2003 on 2009-07-28
is this through a wired or wireless connection??

---

### Post by ZhuaSD on 2009-07-28
Wired.

Because I had so many problems, when I was preparing to upgrade to 9.04, I installed a realtek ethernet card and turned off the on-board one in bios.

So that realtek card is eth1.

---

### Post by superprash2003 on 2009-07-29
could it be your DSL line , have you tried it with windows?

---

### Post by ZhuaSD on 2009-07-29
Hmm I wonder if this is related to network stability.

[Edit] To be more clear, this has been a problem across two locations, both with good connections on Windows.

The network itself might have some weaknesses, however, that I do not know about.

---

### Post by ZhuaSD on 2009-08-27
On a tip, I installed wicd, which uninstalls nm and nm-gnome.

Then just go through pppoeconf once and that was it. A restart and the icon is there.

Its only been six hours, but so far so good. its got its own icon up there, but I do have to manually start it up with pon dsl-provider.

I am going on a trip so it will be a good chance to see if it really works.

Apparently there is some bug between nm and pppoeconf.

---

### Post by ZhuaSD on 2009-08-27
Annndd...

no change.  It was stable until I went out for the night...

---

