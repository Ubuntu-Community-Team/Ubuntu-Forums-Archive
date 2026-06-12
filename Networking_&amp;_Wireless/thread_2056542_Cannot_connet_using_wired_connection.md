---
title: "Cannot connet using wired connection"
date: 2012-09-11
forum: Networking &amp; Wireless
---

### Post by wanichan on 2012-09-11
This is for ubuntu 10.04LTS. I am using a desktop that when connected previously to a wireless router connected online, but when I connect it using an ethernet cable to a modem it no longer connects to the internet. 

It seems the problem is the dhcp is not assigning me an IP address. It's supposed to be a static IP address. I've also tried manually entering the information in /etc/network/interfaces and get nothing.

I've spent several hours on the forums and googling for an answer but haven't found anything that works. I've also tried restarting the network several times, reconfiguring stuff and rebooting etc.. but nothing helps.

The modem seems to work fine on a windows box. I can't figure out at all what is going on.

Here are the specifications.

[PHP]

## /etc/network/interfaces
------
auto eth1
iface eth1 inet dhcp

##
####################################

route -n
------
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth1

####################################
ifconfig
------
eth1      Link encap:Ethernet  HWaddr MY_MAC_ADDRESS 
          inet6 addr: fe80::214:22ff:fe56:ed9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:904 errors:0 dropped:0 overruns:0 carrier:0
          collisions:9 txqueuelen:10 
          RX bytes:5420832 (5.4 MB)  TX bytes:172583 (172.5 KB)


####################################
contents of /etc/resolve.conf
------
nameserver xxx.x.xxx.x
nameserver yyy.y.y.yyy
(these numbers were supplied by provider as DNS)

####################################
contents of /etc/NetworkManager/nm-system-settings.conf 
------
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

#no-auto-default=MY_MAC_ADDRESS,

[ifupdown]
managed=false

####################################
sudo lshw -C network
------
 *-network               
       description: Ethernet interface
       product: 82545GM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: e
       bus info: pci@0000:03:0e.0
       logical name: eth1
       version: 04
       serial: MY_MAC_ADDRESS
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k5-NAPI duplex=half firmware=N/A latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=10MB/s
       resources: irq:48 memory:dfce0000-dfcfffff ioport:ccc0(size=64)

####################################
lspci -nn | grep -e 0200 -e 0280
------
03:0e.0 Ethernet controller [0200]: Intel Corporation 82545GM Gigabit Ethernet Controller [8086:1026] (rev 04)

####################################
sudo ifdown eth1
------
There is already a pid file /var/run/dhclient.eth1.pid with pid 4086
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth1/MY_MAC_ADDRESS
Sending on   LPF/eth1/MY_MAC_ADDRESS
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

####################################
sudo ifup eth1
------
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth1/MY_MAC_ADDRESS
Sending on   LPF/eth1/MY_MAC_ADDRESS
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ssh stop/waiting
ssh start/running, process 4471




####################################
contents of /etc/dhcp3/dhclient.conf
------
# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

#option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";

#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu,
        ntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}[/PHP]

---

