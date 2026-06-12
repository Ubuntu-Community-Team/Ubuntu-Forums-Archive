---
title: "Swaped to identical laptop and no network"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by Micalo on 2009-12-27
I have multiple identical laptops, I installed Ubuntu Studio 9.10. I removed the hard drive from this laptop and put it in another laptop that has identical HW and etc... everything works just fine with the exception of the network interface.
 
At boot ifconfig there are no devices up, so I run the following: 
sudo su 
ifconfig eth1 up
 
not picking up DHCP, but does show different MAC from other pc.
 
in Sys>Admin>Net Tools 
(eth1) shows up. not eth0. it has a IPv6 but no IPv4, however it does show that there are packets RX/TX
When I try to configure this adapter I get the error: 
"Interface does not exist" 
Check that it is correctly typed and that it is correctly supported by your system.
 
i have already put cmd into /etc/network/interfaces:
 
iface eth1 inet dhcp
 
I had read in an older forum about /etc/iftab and changing something there, but no such file or dir exists.
 
Thanks!

---

### Post by Iowan on 2009-12-27
Post **lshw -C network**. *Probably* got another interface assigned in 
/etc/udev/rules.d/70-persistent-net.rules since eth1(?) was tied to "old" MAC.

---

### Post by lswb on 2009-12-27
Every ethernet adapter has a unique 6 byte ID (ethernet address). Very likely your problem is related to some configuration file somewhere storing the ID from the original laptop. One place I know of on 9.04 and some earlier systems a udev rule will store this address in another rule. I would check /etc/udev/rules.d and/or /lib/udev/rules.d and look for a rule that sets the name eth0 for a particular ethernet address. On 9.04 for instance /etc/udev/70-persistent-net.rules can just be deleted and it will be created at next boot (or restart of udev) with correct values. I cannot say if this would be the correct procedure for 9.10 but hopefully the info will get you started towards finding a solution. There may be other config files where the ethernet address also needs to be changed.

---

### Post by Micalo on 2009-12-27
description: Ethernet interface
product: netXtreme BCM5755M Gigabit Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: [EMAIL="pci@0000:09:00.0"]pci@0000:09:00.0[/EMAIL]
logical name: eth1
version: 02
serial: 00:02:70:87:3c:24
size: 100MB/s
capacity: 1GB/s
width: 64 bits
clock: 33 MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5755m-v3.29 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
resources: irq:28 memory:fldf0000-fldfffff
 
This is all that shows up.

---

### Post by lswb on 2009-12-27
Also a rebuild of your initrd may also be required but this is always a good idea anyway when moving a hard drive from one machine to another. (The command "sudo update-initramfs -u -k all" should do it)

---

### Post by Micalo on 2009-12-30
[SIZE=4][COLOR=Blue]So I tried everything you suggested....and it still wasn't working....

So i kept messing with it just trying commands:[/COLOR][/SIZE] 

root@micalostudio:/home/michael# ifdown eth0
/etc/network/interfaces:17: interface wlan0 declared allow-auto twice
ifdown: couldn't read interfaces file "/etc/network/interfaces"
root@micalostudio:/home/michael# ifup eth0
/etc/network/interfaces:17: interface wlan0 declared allow-auto twice
ifup: couldn't read interfaces file "/etc/network/interfaces"

[COLOR=Blue][SIZE=4]Wasn't sure what this was, so I went to edit the interfaces and delete any duplicate entries for wlan0...[/SIZE][/COLOR]

root@micalostudio:/home/michael# gedit /etc/network/interfaces


root@micalostudio:/home/michael# ifdown eth0
ifdown: interface eth0 not configured
root@micalostudio:/home/michael# gedit /etc/network/interfaces
root@micalostudio:/home/michael# iface eth0 inet dhcp
iface: command not found
root@micalostudio:/home/michael# ifconfig iface eth0 inet dhcp
eth0: Unknown host
ifconfig: `--help' gives usage information.
root@micalostudio:/home/michael# ifconfig iface eth1 inet dhcp
eth1: Unknown host
ifconfig: `--help' gives usage information.
root@micalostudio:/home/michael# [COLOR=Red]/etc/init.d/networking restart[/COLOR]
 * Reconfiguring network interfaces...                                          Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
wlan0: ERROR while getting interface flags: No such device
Failed to bring up wlan0.
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:21:70:87:3c:24
Sending on   LPF/eth0/00:21:70:87:3c:24
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 10.10.10.130 from 10.10.10.46
DHCPREQUEST of 10.10.10.130 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.10.10.130 from 10.10.10.46
bound to 10.10.10.130 -- renewal in 138413 seconds.
                                                                         [ OK ]
root@micalostudio:/home/michael# ping google.com
PING google.com (74.125.67.103) 56(84) bytes of data.
64 bytes from gw-in-f103.1e100.net (74.125.67.103): icmp_seq=1 ttl=55 time=15.3 ms
64 bytes from gw-in-f103.1e100.net (74.125.67.103): icmp_seq=2 ttl=55 time=14.9 ms
64 bytes from gw-in-f103.1e100.net (74.125.67.103): icmp_seq=3 ttl=55 time=15.3 ms
64 bytes from gw-in-f103.1e100.net (74.125.67.103): icmp_seq=4 ttl=55 time=15.3 ms
64 bytes from gw-in-f103.1e100.net (74.125.67.103): icmp_seq=5 ttl=55 time=15.4 ms
64 bytes from gw-in-f103.1e100.net (74.125.67.103): icmp_seq=6 ttl=55 time=14.9 ms
^C
--- google.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5003ms
rtt min/avg/max/mdev = 14.940/15.233/15.453/0.205 ms

[SIZE=4][COLOR=Blue] Thank you for all your help! I'm still a noob....[/COLOR][/SIZE]

---

