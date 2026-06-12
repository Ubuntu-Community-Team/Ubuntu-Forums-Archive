---
title: "How to install driver"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by f.sivas on 2009-02-19
I want to install a driver for my network card. I got the cd with the drivers, i think. I just don't now what to do next.
This is a Lan Adapter FNC-0109TX.
Inside the cd-rom i got:
```

# ls -la /media/cdrom0
total 716
dr-xr-xr-x 1 root root   2048 2006-08-15 02:55 .
drwxr-xr-x 5 root root   4096 2009-02-19 15:06 ..
-r-xr-xr-x 1 root root 557791 2006-08-08 09:19 autorun.exe
-r-xr-xr-x 1 root root     47 2006-08-08 09:19 autorun.inf
-r-xr-xr-x 1 root root    625 2000-08-14 11:54 FILEPATH.LST
-r-xr-xr-x 1 root root  69268 2006-08-09 09:58 FNC-0109TX_Manual-v5.0.pdf
dr-xr-xr-x 1 root root   2048 2006-08-08 09:19 LINUX
dr-xr-xr-x 1 root root   2048 2006-08-08 09:19 NDIS2DOS
-r-xr-xr-x 1 root root  13792 2000-01-31 08:58 NETRTS5.___
-r-xr-xr-x 1 root root   7569 2000-01-31 09:00 NETRTS_A.___
-r-xr-xr-x 1 root root   6698 2000-01-31 08:50 NETRTS.INF
dr-xr-xr-x 1 root root   2048 2006-08-08 09:19 NTRPL
dr-xr-xr-x 1 root root   2048 2006-08-08 09:19 NWCLIENT
dr-xr-xr-x 1 root root   2048 2006-08-08 09:19 NWSERVER
-r-xr-xr-x 1 root root  48447 1999-07-26 06:55 OEMSETUP.INF
dr-xr-xr-x 1 root root   2048 2006-08-08 09:19 Win2000
dr-xr-xr-x 1 root root   2048 2006-08-08 09:19 WIN98
dr-xr-xr-x 1 root root   2048 2006-08-08 09:19 WindowsXP
dr-xr-xr-x 1 root root   2048 2006-08-08 09:19 WinMe
dr-xr-xr-x 1 root root   2048 2006-08-08 09:19 WINNT4

```
 
```

# ls -la /media/cdrom0/linux
total 91
dr-xr-xr-x 1 root root  2048 2006-08-08 09:19 .
dr-xr-xr-x 1 root root  2048 2006-08-15 02:55 ..
-r-xr-xr-x 1 root root 86107 2001-11-21 06:06 8139too.c
-r-xr-xr-x 1 root root   328 2002-06-26 14:49 Makefile
-r-xr-xr-x 1 root root  1447 2001-11-21 05:57 readme.txt

```

This is the readme.txt
```

Comments for 8139too.c version 1.0.0

2001/10/31 by ShuChen Shao



1.This driver was originally based on 8139too.c version "0.9.15".

	

2.It has been enhanced to support RTL8139C+ PCI ethernet chips and tested in 2.4.2 kernel.



3.RTL8139C+ PCI ethernet chips is set to support C+ mode by default.

  If FORCE_C_Mode below is enabled, the RTL8139C+ chip will be forced to support C mode 

  after reboot.



4.This program can be compiled using the attached Makefile.

  And the object file named 8139too.o should be moved to the directory 

  /lib/modules/2.4.2-2/kernel/drivers/net/



5.It can support Auto-Negotiation ability,that is

	10-half	 0x01

	10-full	 0x02

	100-half 0x04

	100-full 0x08

  If 10-half mode is expected, it can be achieved by the following steps:

	#ifconfig eth0 down

	#rmmod 8139too

	#insmod 8139too media=0x01



6.If the "Install Type", selected during the Linux install procedure, is "laptop",

  this driver can work normally for CardBus application without any modification.

  Otherwise, reinstall Linux and select "Install Type" as "laptop". 

  Then this driver can also work.

```
 I move the file 8139too.c to /lib/modules/2.6.27-7-server/kernel/drivers/net but when i run:
```

# /media/cdrom0/LINUX/Makefile
/media/cdrom0/LINUX/Makefile: line 4: MODCFLAGS: command not found
/media/cdrom0/LINUX/Makefile: line 5: /usr/src/linux-2.4.18-3/include/: No such file or directory
/media/cdrom0/LINUX/Makefile: line 7: 8139too.o:: command not found
/media/cdrom0/LINUX/Makefile: line 8: CC: command not found
/media/cdrom0/LINUX/Makefile: line 8: MODCFLAGS: command not found
/media/cdrom0/LINUX/Makefile: line 8: NEW_INCLUDE_PATH: command not found
/media/cdrom0/LINUX/Makefile: line 8: -c: command not found

```
What should i do next?
Thanks for your help

---

### Post by puppywhacker on 2009-02-19
linux already comes with the driver for the realtek rtl8139. good chance it is already loaded

lsmod will list the modules, grep will only show the lines containing 8139, dmesg are the kernel messages and ifconfig shows the network configuration
```
lsmod | grep 8139
dmesg | grep 8139
ifconfig
```

if it is not loaded you can load the module like this
```
modprobe 8139too
```

You can then configure your network using the network manager icon in the left top of the windows

The driver disk you can completely ignore

---

### Post by EvinK on 2009-02-19
Copy the whole linux folder to your home directory (or at least the 8139too.c and MAKEFILE).   These 2 files need to be in the same directory.

Start up terminal and get into the directory you put these 2 files and type make.  At that point it should genereate the 8139too.o file for you to copy.

NOTE: Did not realize the driver was already available.  Try puppywhacker's advice first.

---

### Post by f.sivas on 2009-02-19
```

# dmesg | grep 8139
[    3.026783] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.553168] 8139cp 0000:03:00.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    4.553632] 8139cp 0000:03:00.0: Try the "8139too" driver instead.
[    4.580325] 8139too Fast Ethernet driver 0.9.28
[    4.580393] 8139too 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.581523] eth1: RealTek RTL8139 at 0xe800, 00:11:6b:95:e1:f0, IRQ 16
[    4.581529] eth1:  Identified 8139 chip type 'RTL-8100B/8139D'
root@localhost:~# lsmod | grep 8139
8139too                31744  0 
8139cp                 27904  0 
mii                    13440  2 8139too,8139cp
root@localhost:~# lsmod | grep 8139
8139too                31744  0 
8139cp                 27904  0 
mii                    13440  2 8139too,8139cp


```

```

# dmesg | grep 8139
[    3.026783] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.553168] 8139cp 0000:03:00.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    4.553632] 8139cp 0000:03:00.0: Try the "8139too" driver instead.
[    4.580325] 8139too Fast Ethernet driver 0.9.28
[    4.580393] 8139too 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.581523] eth1: RealTek RTL8139 at 0xe800, 00:11:6b:95:e1:f0, IRQ 16
[    4.581529] eth1:  Identified 8139 chip type 'RTL-8100B/8139D'


```

```

# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:15:be:df  
          inet addr:213.22.213.69  Bcast:213.22.213.255  Mask:255.255.254.0
          inet6 addr: fe80::221:85ff:fe15:bedf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23952 errors:0 dropped:0 overruns:0 frame:0
          TX packets:878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1996669 (1.9 MB)  TX bytes:192168 (192.1 KB)
          Interrupt:221 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3928 (3.9 KB)  TX bytes:3928 (3.9 KB)


```

Then i run:
```

modprobe 8139too

```

Reboot the pc and run
```

# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:15:be:df  
          inet addr:213.22.213.69  Bcast:213.22.213.255  Mask:255.255.254.0
          inet6 addr: fe80::221:85ff:fe15:bedf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23952 errors:0 dropped:0 overruns:0 frame:0
          TX packets:878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1996669 (1.9 MB)  TX bytes:192168 (192.1 KB)
          Interrupt:221 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3928 (3.9 KB)  TX bytes:3928 (3.9 KB)


```

Doesn't show eth1 and always show the message
```

[    4.553168] 8139cp 0000:03:00.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip

```

I'm using Ubuntu server and i don't have the network manager icon in the left top of the windows

---

### Post by puppywhacker on 2009-02-19
No need to modprobe, the driver is already loaded. Also the warning that it is not an 8139C+ compatible chip is followed by more good news. I think it's trying the 8139cp driver first and changes to 8139too when it recognizes that another driver should be used. Below is my output.

```
[    5.346676] 8139cp 0000:04:06.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    5.346679] 8139cp 0000:04:06.0: Try the "8139too" driver instead.
[    5.353192] 8139too Fast Ethernet driver 0.9.28
```

The interface could be in an unconfigured and down, so look at
```
ifconfig -a
```

The rtl8139 is mii capable, so to check the link status run 
```
mii-tool eth1
```

To configure the network interfaces edit the interfaces file.
1. Add eth1 to the auto line
2. Create a new iface eth1 stanza
3. run "ifup eth1"

/etc/network/interfaces
```
auto lo eth0 eth1
iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet static
        address 192.168.1.9
        netmask 255.255.255.0
```

---

### Post by f.sivas on 2009-02-19
Thanks. I think i got it, but i need i litle help to conect a windows pc to the network with the switch.
The windows pc only show the localhost page. Can't connect to internet, i think that only connects to localnetwork. I've installed dhcp server in ubuntu.

```

# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:15:be:df  
          inet addr:83.132.192.129  Bcast:83.132.193.255  Mask:255.255.254.0
          inet6 addr: fe80::221:85ff:fe15:bedf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:283346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8789 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23240257 (23.2 MB)  TX bytes:3427513 (3.4 MB)
          Interrupt:221 

eth2      Link encap:Ethernet  HWaddr 00:11:6b:95:e1:f0  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:6bff:fe95:e1f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:428 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59416 (59.4 KB)  TX bytes:48089 (48.0 KB)
          Interrupt:16 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1448430 (1.4 MB)  TX bytes:1448430 (1.4 MB)

```

# vi /etc/network/interfaces
```

# The loopback network interface
auto lo
iface lo inet loopback
#
# The primary network interface
auto eth0
iface eth0 inet dhcp
#
# The secondary network interface
auto eth2
iface eth2 inet static
      address 192.168.1.1
      netmask 255.255.255.0
      network 192.168.1.0
      broadcast 192.168.1.255

```

# vi /etc/default/dhcp3-server
```

# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#	Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth2"

```

# vi /etc/dhcp3/dhcpd.conf
```

ddns-update-style none;
option domain-name "localhost";

option domain-name-servers 150.161.6.1;

default-lease-time 3600;
max-lease-time 7200;

log-facility local7;

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.100 192.168.1.250;
  option routers 192.168.1.1;
}

```


Thanks

---

### Post by puppywhacker on 2009-02-19
Ok, so you want to use your linux server as a NAT for a dhcpclient in a local network?

```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sysctl -w net.ipv4.conf.all.forwarding=1
iptables-save
```

And change your domain-name-server from 150.161.6.1 (university of Recife Brasil) to a portuguese one, the dns-servers from you internet provider is in /etc/resolv.conf

---

### Post by f.sivas on 2009-02-19
Thank you very much!! :D

---

### Post by f.sivas on 2009-02-21
I don't now why but it don't work anymore!
from the DHCP server i can ping the client pc but from the client pc i can't do that and i don't have access to the internet...

an someone tell me if this is Ok?

```

# cat /var/lib/dhcp3/dhcpd.leases
# The format of this file is documented in the dhcpd.leases(5) manual page.
# This lease file was written by isc-dhcp-V3.1.1

lease 192.168.1.101 {
  starts 5 2009/02/20 10:47:21;
  ends 5 2009/02/20 11:47:21;
  tstp 5 2009/02/20 11:47:21;
  cltt 5 2009/02/20 10:47:21;
  binding state free;
  hardware ethernet 00:0e:a6:5b:21:6f;
  uid "\001\000\016\246[!o";
}
lease 192.168.1.102 {
  starts 6 2009/02/21 14:40:10;
  ends 6 2009/02/21 14:44:27;
  tstp 6 2009/02/21 14:44:27;
  cltt 6 2009/02/21 14:40:10;
  binding state free;
  hardware ethernet 00:50:da:3a:ec:90;
}
lease 192.168.1.100 {
  starts 6 2009/02/21 19:41:58;
  ends 6 2009/02/21 20:41:58;
  cltt 6 2009/02/21 19:41:58;
  binding state active;
  next binding state free;
  hardware ethernet 00:22:15:95:d9:2c;
  uid "\001\000\"\025\225\331,";
  client-hostname "MY_EEE_PC";
}


```

From the DHCP Server
```

root@localhost:~# ping 192.168.1.100
PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_seq=1 ttl=128 time=9.02 ms
64 bytes from 192.168.1.100: icmp_seq=2 ttl=128 time=0.201 ms
64 bytes from 192.168.1.100: icmp_seq=3 ttl=128 time=0.211 ms
64 bytes from 192.168.1.100: icmp_seq=4 ttl=128 time=0.208 ms
64 bytes from 192.168.1.100: icmp_seq=5 ttl=128 time=0.207 ms
64 bytes from 192.168.1.100: icmp_seq=6 ttl=128 time=0.208 ms
--- 192.168.1.100 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5017ms
rtt min/avg/max/mdev = 0.201/1.676/9.024/3.286 m

```

```

# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:15:be:df  
          inet addr:213.22.148.6  Bcast:213.22.149.255  Mask:255.255.254.0
          inet6 addr: fe80::221:85ff:fe15:bedf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1495289 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16458 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:98684261 (98.6 MB)  TX bytes:8080436 (8.0 MB)
          Interrupt:221 Base address:0x2000 

eth2      Link encap:Ethernet  HWaddr 00:11:6b:95:e1:f0  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:6bff:fe95:e1f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26365 (26.3 KB)  TX bytes:12621 (12.6 KB)
          Interrupt:16 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:765 errors:0 dropped:0 overruns:0 frame:0
          TX packets:765 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:217617 (217.6 KB)  TX bytes:217617 (217.6 KB)


```

```

# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

```
The configuration files are the same, i didn't change anything. I just disconnected the network cable and i never got back the internet connection...

---

