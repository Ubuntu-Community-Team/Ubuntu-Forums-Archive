---
title: "Ltsp 8.10 2 nic"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by RandallHamm on 2009-01-19
Installed 8.10 LTSP from Alternate cd to HD1.  Server has two NICs-one on motherboard and one PCI slot.
Upon install I can attach client with PXE, but the other NIC to the router / Internet will not connect.

The same hardware connects correctly to both NICs (router switch and thin client switch) with LTSP 8.04 on HD0 so I do not suspect a hardware issue for now.

ETH0 and ETH1 are set to Automatic even after changing interfaces and dhcpd.conf files.  And now neither NIC connects.

[http://ubuntuforums.org/showthread.php?t=599166&highlight=ltsp](http://ubuntuforums.org/showthread.php?t=599166&highlight=ltsp)

<<<>>> gksudo "gedit /etc/network/interfaces"

# The loopback network interface

auto lo

iface lo inet loopback



# The primary network interface

auto eth0

iface eth0 inet static

address 192.168.0.140

netmask 255.255.255.0

network 192.168.0.0

broadcast 192.168.0.255

gateway 192.168.0.1

# dns-* options are implemented by the resolvconf package, if installed

dns-nameservers 192.168.0.1



# The secondary network interface

auto eth1

iface eth1 inet static

address 192.168.1.1

netmask 255.255.255.0

network 192.168.1.0

broadcast 192.168.1.255

# dns-* options are implemented by the resolvconf package, if installed

dns-nameservers 192.168.0.1
<<<>>>

also

<<<>>> gksudo "gedit /etc/ltsp/dhcpd.conf"
#

# Default LTSP dhcpd.conf config file.

#



authoritative;



subnet 192.168.1.0 netmask 255.255.255.0 {

range 192.168.1.5 192.168.1.20;

option domain-name "*";

option domain-name-servers 192.168.1.1;

option broadcast-address 192.168.1.255;

option routers 192.168.1.1;

# next-server 192.168.0.254;

# get-lease-hostnames true;

option subnet-mask 255.255.255.0;

option root-path "/opt/ltsp/i386";

if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {

filename "/ltsp/i386/pxelinux.0";

} else {

filename "/ltsp/i386/nbi.img";

}

}
<<>>

Also, is the a way to get Windows command "ipconfig /all" data in Ubuntu?

How can one determine which NIC is eth0 or eth1?

Nu2U,
Randall

---

### Post by RandallHamm on 2009-01-19
Reinstalled 810 LTSP and have connectivity with thin client again, but still no connection to router/Internet.

The "Wired Network" icon in panel displays:
Wired Network (Intel 82562EZ 10/100 Ethernet Controller
[birdeye filled] ifupdown (eth0)
Wired Network (Linksys Gigabit Network Adapter
device is unmanaged

The Intel is connected to router and was selected during inital install of 8.10.

file: /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
#iface eth1 inet dhcp

auto eth0
iface eth0 inet static
    address 192.168.0.254
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255



file: /etc/ltsp/dhcpd.conf#

# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.20 192.168.0.250;
    option domain-name "example.com";
    option domain-name-servers 192.168.0.1;
    option broadcast-address 192.168.0.255;
    option routers 192.168.0.1;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}



file:  /var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default

DEFAULT vmlinuz ro initrd=initrd.img quiet splash








Commands data:

randall@LTSP810:~$ grep tftp /etc/inetd.conf
tftp           dgram   udp     wait    root  /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /var/lib/tftpboot



randall@LTSP810:~$ pgrep -l dhcp
5283 dhcpd3




randall@LTSP810:~$ grep dhcp /var/log/daemon.log
Jan 19 09:23:44 LTSP810 dhcpd: Internet Systems Consortium DHCP Server V3.1.1
Jan 19 09:23:44 LTSP810 dhcpd: Copyright 2004-2008 Internet Systems Consortium.
Jan 19 09:23:44 LTSP810 dhcpd: All rights reserved.
Jan 19 09:23:44 LTSP810 dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan 19 09:23:44 LTSP810 dhcpd: Wrote 0 leases to leases file.
Jan 19 09:39:49 LTSP810 dhcpd: DHCPDISCOVER from 00:06:5b:d8:14:0c via eth0
Jan 19 09:39:50 LTSP810 dhcpd: DHCPOFFER on 192.168.0.20 to 00:06:5b:d8:14:0c via eth0
Jan 19 09:39:51 LTSP810 dhcpd: DHCPREQUEST for 192.168.0.20 (192.168.0.254) from 00:06:5b:d8:14:0c via eth0
Jan 19 09:39:51 LTSP810 dhcpd: DHCPACK on 192.168.0.20 to 00:06:5b:d8:14:0c via eth0
Jan 19 09:40:02 LTSP810 dhcpd: DHCPDISCOVER from 00:06:5b:d8:14:0c via eth0
Jan 19 09:40:02 LTSP810 dhcpd: DHCPOFFER on 192.168.0.20 to 00:06:5b:d8:14:0c via eth0
Jan 19 09:40:02 LTSP810 dhcpd: DHCPREQUEST for 192.168.0.20 (192.168.0.254) from 00:06:5b:d8:14:0c via eth0
Jan 19 09:40:02 LTSP810 dhcpd: DHCPACK on 192.168.0.20 to 00:06:5b:d8:14:0c via eth0
Jan 19 09:40:03 LTSP810 dhcpd: DHCPREQUEST for 192.168.0.20 (192.168.0.254) from 00:06:5b:d8:14:0c via eth0
Jan 19 09:40:03 LTSP810 dhcpd: DHCPACK on 192.168.0.20 to 00:06:5b:d8:14:0c via eth0



randall@LTSP810:~$ grep ftp /var/log/daemon.log
[no response]

randall@LTSP810:~$ ls /opt/ltsp/i386
bin   cdrom  etc   lib    mnt  proc  sbin  sys  usr
boot  dev    home  media  opt  root  srv   tmp  var



randall@LTSP810:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:e5:d7:42:5c  
          inet addr:192.168.0.254  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:e5ff:fed7:425c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19388 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:849023 (849.0 KB)  TX bytes:28490073 (28.4 MB)
          Interrupt:22 Base address:0x4c00 

eth1      Link encap:Ethernet  HWaddr 00:0c:f1:af:33:6f  
          inet addr:192.168.0.254  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:feaf:336f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2174 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:627972 (627.9 KB)  TX bytes:4188 (4.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23032 (23.0 KB)  TX bytes:23032 (23.0 KB)


randall@LTSP810:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     1      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         LTSP810.local   0.0.0.0         UG    0      0        0 eth1

---

