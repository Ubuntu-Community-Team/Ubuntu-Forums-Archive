---
title: "strange/broken ifconfig"
date: 2006-02-08
forum: Networking &amp; Wireless
---

### Post by dmonty on 2006-02-08
My work laptop is displaying very strange ifconfig output.  Namely both eth0 (wired), eth1(wireless) are showing 169.254.x.x addresses no matter which one is plugged in.  At work I connect to eth0(cat5), at home eth1(wireless).  Below is all at home on my wireless.  My IP is 192.168.0.5 as seen by netstat output, but my ifconfig shows 169.254.50.141.  Network works fine even with the 169.254.x.x address, which makes no sence to me.  Only thing I can think of is that the kernel was recently upgraded. I'm runing Ubuntu Breezy with the kubuntu-desktop.

dmonty@khebron:~$ uname -a
Linux khebron 2.6.12-10-686 #1 Mon Jan 16 17:58:04 UTC 2006 i686 GNU/Linux
dmonty@khebron:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:A6:61:EA:5D
          inet addr:169.254.156.46  Bcast:0.0.0.0  Mask:255.255.0.0
          inet6 addr: fe80::20e:a6ff:fe61:ea5d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:0E:35:6F:73:07
          inet addr:169.254.50.141  Bcast:0.0.0.0  Mask:255.255.0.0
          inet6 addr: fe80::20e:35ff:fe6f:7307/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:697 errors:0 dropped:0 overruns:0 frame:0
          TX packets:641 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13261519 (12.6 MiB)  TX bytes:1142811 (1.0 MiB)
          Interrupt:17 Base address:0x8000 Memory:e4000000-e4000fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:19186 (18.7 KiB)  TX bytes:19186 (18.7 KiB)
dmonty@khebron:~$ netstat -an | grep EST
tcp        0      0 192.168.0.5:43798       64.12.25.177:5190       ESTABLISHED
tcp        0      0 192.168.0.5:45902       205.188.176.105:5190    ESTABLISHED
tcp        0      0 127.0.0.1:32770         127.0.0.1:55011         ESTABLISHED
tcp        0      0 192.168.0.5:45360       207.46.4.31:1863        ESTABLISHED
tcp        0      0 192.168.0.5:38190       216.155.193.176:5050    ESTABLISHED
tcp        0      0 192.168.0.5:55633       142.24.13.141:143       ESTABLISHED
tcp        0      0 192.168.0.5:57264       205.188.7.204:5190      ESTABLISHED
tcp        0      0 127.0.0.1:55011         127.0.0.1:32770         ESTABLISHED
dmonty@khebron:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
iface eth1 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid any

auto eth1

iface eth0 inet dhcp

auto eth0

dmonty@khebron:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1

---

### Post by dickohead on 2006-02-08
perhaps DHCP has a masking option for security reasons, this may be implemented at your work? Or it's just acting out...

---

### Post by dmonty on 2006-02-09
[QUOTE=dickohead]perhaps DHCP has a masking option for security reasons, this may be implemented at your work? Or it's just acting out...[/QUOTE]

It is just acting strange.  It is not the dhcp servers because they have both remained unchanged for several years now.

---

### Post by bscbrit on 2006-02-09
If your home network has also been configured for 169.254.x.x then it will work - it is simply that such values shouldn't be used for private networks. But they will still work.

How is your DHCP served on your home network?  Can you ping between different computers on your home network using the 169.254.x.x. addresses?

Are you using NetworkManager and nm-applet to manage your networks? (I recommend not - but that is your decision).

---

### Post by mips on 2006-02-09
[http://www.answers.com/topic/link-local-address](http://www.answers.com/topic/link-local-address)

> An IP address in the range from 169.254.1.0 to 169.254.254.255 is a link-local address. It is used to automatically assign an IP address to a device in an IP network when there is no other assignment method available, such as a DHCP server. After an address is chosen, the link-local process sends an ARP query with that IP onto the network to see if it exists. If there is no response, the IP is assigned to the device, otherwise another IP is selected, and the ARP is repeated.

Which basically means your DHCP/Network is not working...

I have not seen this happen on my PC but seen it lots on windows machines.

---

### Post by bscbrit on 2006-02-09
mips to my rescue again! Thanks mips.

---

### Post by dmonty on 2006-02-10
Both work and home lan's serve up dhcp addresses in the 192.168.0.0/24 range.  ALL of the other computers(windows/linux) on both networks work just fine.  Only my Ubuntu Laptop has a messed up `ifconfig` even though it has recieved and uses its assigned 192.168.x.x address.  ifconfig shows 169.254.x.x address which usually means no network ip offered.  I haven't had much time to figure out exactly why it shows this because my network works, it just reports back wrong numbers with ifconfig.

---

### Post by mips on 2006-02-10
What does your routers arp table display ?

---

### Post by dmonty on 2006-02-13
Here is my ifconfig at work. Then ssh into another machine to list the arp table.  Notice MAC is the same as eth0.  ifconfig is just not showing the correct ip.

dmonty@khebron:~$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:A6:61:EA:5D
          inet addr:169.254.156.46  Bcast:0.0.0.0  Mask:255.255.0.0
          inet6 addr: fe80::20e:a6ff:fe61:ea5d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14475 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7430423 (7.0 MiB)  TX bytes:2081008 (1.9 MiB)
          Interrupt:19 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:0E:35:6F:73:07
          inet addr:169.254.50.141  Bcast:0.0.0.0  Mask:255.255.0.0
          inet6 addr: fe80::20e:35ff:fe6f:7307/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:123 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7931 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xa000 Memory:e4000000-e4000fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:694 errors:0 dropped:0 overruns:0 frame:0
          TX packets:694 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:69949 (68.3 KiB)  TX bytes:69949 (68.3 KiB)
dmonty@khebron:~$ ssh tux-2002
...
[root@tux-2002 dmonty]# arp -n
Address                 HWtype  HWaddress           Flags Mask            Iface
...
192.168.0.202           ether   00:0E:A6:61:EA:5D   CM                    eth0
...

---

### Post by mips on 2006-02-13
Very weird. Dunno what to say right now, will get back to you.

---

### Post by dmonty on 2006-02-15
SOLUTION:

[http://lists.debian.org/debian-user/2005/07/msg01195.html](http://lists.debian.org/debian-user/2005/07/msg01195.html)

removing the package:

zeroconf

> 
root@khebron:~# aptitude show zeroconf
Package: zeroconf
New: yes
State: not installed (configuration files remain)
Version: 0.3-1
Priority: optional
Section: universe/net
Maintainer: Anand Kumria <wildfire@progsoc.org>
Uncompressed Size: 73.7k
Depends: libc6 (>= 2.3.4-1), ifupdown, iproute
Description: IPv4 link-local address allocator
 zeroconf is an implementation of IPv4 link-local addresses (RFC3927) which can be used for ad-hoc networks.  Addresses are allocated from the 169.254.0.0/16 range semi-randomly.

 That means making it possible to take two laptop computers, and connect them with a crossover Ethernet cable, and have them communicate usefully using IP, without needing a man in a white lab coat
 to set it all up for you. (from [www.zeroconf.org](www.zeroconf.org))


The people at zeroconf should ensure that their programmer wearing the white coat has arms buckled behind his back at all times.  ](*,)

---

### Post by bscbrit on 2006-02-15
That's another one on my list of programs to look out for....... and avoid :)

---

