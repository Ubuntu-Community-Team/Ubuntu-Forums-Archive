---
title: "One network card not recognized."
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by shoguevara on 2010-01-10
Hi everybody. I have a simillar trouble, but as I see there is a driver module for network card in my system. I have 2 identical network cards in my system - the 1st one works well, but the second one.. My system refuses to create interface on it....
 lspci
```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 Ethernet controller: D-Link System Inc DGE-530T Gigabit Ethernet Adapter (rev 11) (rev 11)
01:02.0 Ethernet controller: D-Link System Inc DGE-530T Gigabit Ethernet Adapter (rev 11) (rev 11)

```
As we can see in last 2 rows both cards installed and working...
```
root@inetserv:~# lshw -c network
  *-network:0
       description: Ethernet interface
       product: DGE-530T Gigabit Ethernet Adapter (rev 11)
       vendor: D-Link System Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 11
       serial: 00:21:91:8d:18:92
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.69 latency=32 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:18 memory:f9000000-f9003fff ioport:b000(size=256) memory:40000000-4001ffff(prefetchable)
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: DGE-530T Gigabit Ethernet Adapter (rev 11)
       vendor: D-Link System Inc
       physical id: 2
       bus info: pci@0000:01:02.0
       version: 11
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd cap_list
       configuration: latency=32 maxlatency=31 mingnt=23
       resources: memory:f8000000-f8003fff ioport:b400(size=256) memory:40020000-4003ffff(prefetchable)

```
Koala didn't see the 2nd one, so I decided to install Lucid (in server rev. i386)

```
Linux inetserv 2.6.32-7-generic-pae #10-Ubuntu SMP Sun Dec 6 15:05:08 UTC 2009 i686 GNU/Linux
```
```
root@inetserv:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu lucid (development branch)
Release:        10.04
Codename:       lucid
```

My /etc/network/interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.69
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.3
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.3
        dns-search soglasie-npf
auto eth1
iface eth1 inet static
        address 192.168.17.1
        netmask 255.255.255.0
        network 192.168.17.0
        broadcast 192.168.17.255

```

When I'm restarting the daemon I get:
```
root@inetserv:~# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                                                                                         
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Failed to bring up eth1.
```

The same happens when I run the command "ifup eth1"

So, I decided to edit /etc/udev/rules.d/70-persistent-net.rules adding the last line:
```
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x1186:0x4b01 (skge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:21:91:8d:18:92", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:21:91:8d:19:8a", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
```
Changing ATTR{dev_id}=="0x0" to ATTR{dev_id}=="0x2" does nothing...

I have no any idea where to digg now... Any suggestions? Please?)
PS eth0 works fine
 ifconfig -a
```
root@inetserv:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:21:91:8d:18:92
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:91ff:fe8d:1892/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5699 (5.6 KB)  TX bytes:7515 (7.5 KB)
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:94 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:12639 (12.6 KB)  TX bytes:12639 (12.6 KB)

```
Don't pay attention to errors - I've retrieved conf's through SSH client, so the network on et0 is fine.

---

### Post by bapoumba on 2010-01-10
Moved to its own thread.

---

### Post by gombadi on 2010-01-10
It looks like the kernal module is not seeing the second card.

Have a look in the /var/log/syslog and /var/log/dmesg files to see if they show any errors related to the eth ports.

---

### Post by Iowan on 2010-01-11
Lucid takes it into the Developer's realm, but...
Did any of your posted information change since Lucid?

---

