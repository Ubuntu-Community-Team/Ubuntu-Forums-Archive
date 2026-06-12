---
title: "Intrepid/VirtualBox 2.0.6 Host Interface Networking Problem"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by jrobbo on 2008-12-17
Hey all,

Desperately looking for some help, i've been battling with this for the past few days and am getting nowhere. 

I have a fresh install of Intrepid on my Lenovo T61 laptop, and i've installed VirtualBox 2.0.6. I have 2 VM's, one is Windows XP, and the other is Red Hat 5.3 Linux. Everything works just fine and dandy if I stick to NAT networking, except that I have one application that uses Active FTP and won't work over NAT, so I need to configure Host Interface Sharing, and this is where my troubles began.

I've tried the methods outlined in the VirtualBox manual, first the permanent bridge, and then the dynamic bridge, neither of them worked, with either of my VM's. Basically, the problem is that my guest VM cannot contact the DHCP server to get an IP address. If I check the network status, I can see that many packets were sent, but none were received. I have disabled all of my firewalls, all to no effect, I always get the same problem. I've also tried setting static IP's, with the same effect. 

On top of trying the methods outlined in the VB manual, i've also tried 10 or so variations of those methods that i've found on the net, some from the Ubuntu forums, and the effect is always the same, without fail. 

To summarise the steps that I took to get permanent HIF interfaces set up:

1) Install bridge-utils and uml-utilities
2) Changed the group of /dev/net/tun to "vboxusers", of which I am a member
3) Changed the permissions of /dev/net/tun to 666
4) Modified my /etc/network/interfaces file so that it now looks like this:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
	bridge_ports eth0 vbox0

```

(I've also tried it without the vbox0 on the end)

5) Restarted networking (/etc/init.d/networking restart)
6) Executed "VBoxAddIF vbox0 jrobbo br0"
7) Entered the settings in VirtualBox for my VM's, changed networking type to Host Interface Networking, and added "vbox0" as the interface name

Here is the output of ifconfig after the changes:
```

br0       Link encap:Ethernet  HWaddr 00:1a:6b:d0:7e:9c  
          inet addr:192.168.0.61  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:6bff:fed0:7e9c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26430 (26.4 KB)  TX bytes:6099 (6.0 KB)

eth0      Link encap:Ethernet  HWaddr 00:1a:6b:d0:7e:9c  
          inet6 addr: fe80::21a:6bff:fed0:7e9c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22736 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9097 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:10654832 (10.6 MB)  TX bytes:1594993 (1.5 MB)
          Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:660 (660.0 B)  TX bytes:660 (660.0 B)

vbox0     Link encap:Ethernet  HWaddr a6:66:dd:c0:13:b5  
          inet6 addr: fe80::a466:ddff:fec0:13b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:33 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

his is just one of the methods that i've tried, but i've tried about 10 or so and they all have the same effect, that is that the guest cant connect to the network. 

Can anyone give me some tips please? i've really run out of ideas.

Many thanks

John

---

### Post by The Cog on 2008-12-17
This script did the trick for me, last time I used it:
> #!/bin/sh
brctl addbr br0
ifconfig eth0 0.0.0.0
brctl addif br0 eth0
ifconfig br0 192.168.1.2 netmask 255.255.255.0
route add default gw 192.168.1.1
VBoxAddIF vbox0 steve br0
chgrp vboxusers /dev/net/tun


---

### Post by jrobbo on 2008-12-18
Thanks,

As it happens, VirtualBox 2.1.0 was release this morning, and it totally automates setting up Host Interface Networking. Problem solved! :)

John

---

