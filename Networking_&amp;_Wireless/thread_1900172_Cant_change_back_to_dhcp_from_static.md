---
title: "Cant change back to dhcp from static"
date: 2011-12-25
forum: Networking &amp; Wireless
---

### Post by silly35 on 2011-12-25
Hi 
 
I am very new to the linux world so please go easy on me. I have installed ubuntu a while ago and I was making into a server on my network. I gave it a static IP address. Since then my network has changed abit. Not i cant get any internet on my ubuntu computer. I am having troubles getting the computer back on dhcp instead of static. when i go to system - preferences - network connections there are no wired connections to be seen. My ethernet card has a solid green light on so i know its not a cabling issue. 
 
someone please help. this is very fustrating. 
 
I am running ubuntu 10.04. Im trying to update when i get internet again.

---

### Post by gareththered on 2011-12-25
Check if your hardware is still recognised.  In a terminal, type 'ip link' and check is you have a line beginning with 'eth0' (or a number greater than '0', e.g. eth1 or eth2).  Post the results here.  While you're at it, type 'sudo lshw -class net' and post the results.

---

### Post by silly35 on 2011-12-25
It appears to be fine... I think. See below
 
[EMAIL="jeremy@FileServer:~$"]jeremy@FileServer:~$[/EMAIL] ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether 00:11:11:97:74:7f brd ff:ff:ff:ff:ff:ff
3: virbr0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN 
    link/ether 4e:77:3b:05:2b:25 brd ff:ff:ff:ff:ff:ff
5: vboxnet0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 0a:00:27:00:00:00 brd ff:ff:ff:ff:ff:ff
[EMAIL="jeremy@FileServer:~$"]jeremy@FileServer:~$[/EMAIL] sudo lshw -class net
[sudo] password for jeremy: 
  *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: [EMAIL="pci@0000:06:08.0"]pci@0000:06:08.0[/EMAIL]
       logical name: eth0
       version: 01
       serial: 00:11:11:97:74:7f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A ip=192.168.2.10 latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:ff500000-ff500fff ioport:bc00(size=64)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
[EMAIL="jeremy@FileServer:~$"]jeremy@FileServer:~$[/EMAIL]

---

### Post by gareththered on 2011-12-25
You have NO-CARRIER for eth0 and the 'lshw' results also says you have no link.  I believe that it shows this if the Ethernet port cannot see anything on the end - i.e. disconnected or broken cable.  Have you checked your wiring?

I did find a post that suggested this issue could also be due to power management issues.  Have a read of:-
[https://bbs.archlinux.org/viewtopic.php?id=118810](https://bbs.archlinux.org/viewtopic.php?id=118810)

Did you configure the static IP using the GUI or by editing /etc/network/interfaces?

---

### Post by silly35 on 2011-12-25
Sorry my mistake. My ethernet cable was in a different computer when i ran the commands. 
 
See below
 
[EMAIL="jeremy@FileServer:~$"]jeremy@FileServer:~$[/EMAIL] ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:11:11:97:74:7f brd ff:ff:ff:ff:ff:ff
3: virbr0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN 
    link/ether 4e:77:3b:05:2b:25 brd ff:ff:ff:ff:ff:ff
5: vboxnet0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 0a:00:27:00:00:00 brd ff:ff:ff:ff:ff:ff
[EMAIL="jeremy@FileServer:~$"]jeremy@FileServer:~$[/EMAIL] sudo lshw -class net
[sudo] password for jeremy: 
  *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: [EMAIL="pci@0000:06:08.0"]pci@0000:06:08.0[/EMAIL]
       logical name: eth0
       version: 01
       serial: 00:11:11:97:74:7f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.2.10 latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:ff500000-ff500fff ioport:bc00(size=64)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
[EMAIL="jeremy@FileServer:~$"]jeremy@FileServer:~$[/EMAIL]

---

### Post by gareththered on 2011-12-26
Sorry about the delayed response, but I eat too much yesterday and had an early night!!

What does the file '/etc/network/interfaces' show (type 'cat /etc/network/interfaces' at the terminal)?

Do you have any reference to 'eth0' in there?

Mine is as simple as this:-
> auto lo
iface lo inet loopback
Note that there is no reference to any of my real networking devices - eth0, wlan0 etc.  If there are, then remove them.

---

