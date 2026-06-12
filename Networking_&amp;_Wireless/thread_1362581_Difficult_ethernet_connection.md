---
title: "Difficult ethernet connection"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by nico@nc on 2009-12-23
Hello,

My Dell Inspiron 530 computer is connected to internet using an ethernet modem, but since I updated to Karmic, it hardly never directly succeeds to connect on start up.

Nearly all the time after login, network-manager is trying to connect to the network and finally indicates that the computer is off-line. Some ways I found to fix this (working 9 times out of 10) are rebooting the computer, or unchecking "enable network" and checking it again in network manager context menu, then clicking on the connection name in NM "left-click" menu and waiting a few seconds.

Thanks for you help.

PS: Here is some information about my connection and configuration:
> [FONT="Courier New"]nicolas@dell-bureau:~$ **sudo lshw -C network**
  *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:21:70:10:25:92
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.1-2 ip=192.168.0.1 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:26 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:ff00(size=32)

nicolas@dell-bureau:~$ **ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:21:70:10:25:92  
          inet adr:192.168.0.1  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: 2a01:e35:2eb6:dd60:221:70ff:fe10:2592/64 Scope:Global
          adr inet6: fe80::221:70ff:fe10:2592/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:2384 erreurs:0 :0 overruns:0 frame:0
          TX packets:2249 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:100 
          Octets reçus:2476711 (2.4 MB) Octets transmis:471171 (471.1 KB)
          Mémoire:fdfc0000-fdfe0000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:113 erreurs:0 :0 overruns:0 frame:0
          TX packets:113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:15684 (15.6 KB) Octets transmis:15684 (15.6 KB)

nicolas@dell-bureau:~$ **cat /etc/network/interfaces**
auto lo
iface lo inet loopback[/FONT]

---

### Post by doas777 on 2009-12-23
sounds like your cable/port is dying. have you tried swapping the cable out? also if you haven't rebooted the cablemodem in a while, unplug it for 5-10 minutes and try again.

---

### Post by nico@nc on 2009-12-23
The modem has been rebooted a few hours ago, and the problem is the same with a new ethernet cable.

I also tried to plug the cable into my notebook, and it connects without problem in 3-5 seconds, whereas I am writing this message in "offline" mode on the Dell desktop, waiting for a connection. (for both of computers I removed the connection details in NM "edit connections" window before testing)

Could it be a problem with the computer's ethernet port or network card?

---

### Post by iponeverything on 2009-12-23
have a terminal open while it's trying to connect with this command running:

```
sudo tail -vf /var/log/messages /var/log/syslog

```

It might give some clues as to what is going on.

---

### Post by nico@nc on 2009-12-23
Here it is :
> *[ethernet connection disconnected]*
[FONT="Courier New"]nicolas@dell-bureau:~$ sudo tail -vf /var/log/messages /var/log/syslog
==> /var/log/messages <==
Dec 23 16:51:29 dell-bureau kernel: [ 2990.252764] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
Dec 23 16:51:29 dell-bureau kernel: [ 2990.253015] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 23 17:07:06 dell-bureau kernel: [ 3927.021101] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 23 17:07:08 dell-bureau kernel: [ 3928.396756] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Dec 23 17:07:08 dell-bureau kernel: [ 3928.396760] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
Dec 23 17:07:08 dell-bureau kernel: [ 3928.397012] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 23 17:09:35 dell-bureau kernel: [ 4075.864880] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 23 17:09:37 dell-bureau kernel: [ 4077.376756] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Dec 23 17:09:37 dell-bureau kernel: [ 4077.376761] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
Dec 23 17:09:37 dell-bureau kernel: [ 4077.377017] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

==> /var/log/syslog <==
Dec 23 17:09:35 dell-bureau NetworkManager: <info>  (eth0): preparing device.
Dec 23 17:09:35 dell-bureau NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Dec 23 17:09:35 dell-bureau kernel: [ 4075.864567] e1000e 0000:00:19.0: irq 26 for MSI/MSI-X
Dec 23 17:09:35 dell-bureau kernel: [ 4075.864880] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 23 17:09:37 dell-bureau NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Dec 23 17:09:37 dell-bureau NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Dec 23 17:09:37 dell-bureau kernel: [ 4077.376756] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Dec 23 17:09:37 dell-bureau kernel: [ 4077.376761] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
Dec 23 17:09:37 dell-bureau kernel: [ 4077.377017] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 23 17:09:38 dell-bureau avahi-daemon[866]: Registering new address record for fe80::221:70ff:fe10:2592 on eth0.*.
[/font]*[I click on the connection name in NM to try connection]*
[FONT="Courier New"]Dec 23 17:09:44 dell-bureau NetworkManager: <info>  Activation (eth0) starting connection 'Ethernet automatique'
Dec 23 17:09:44 dell-bureau NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Dec 23 17:09:44 dell-bureau NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 23 17:09:44 dell-bureau NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Dec 23 17:09:44 dell-bureau NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Dec 23 17:09:44 dell-bureau NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Dec 23 17:09:44 dell-bureau NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Dec 23 17:09:44 dell-bureau NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Dec 23 17:09:44 dell-bureau NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Dec 23 17:09:44 dell-bureau NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 23 17:09:44 dell-bureau NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Dec 23 17:09:44 dell-bureau NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Dec 23 17:09:44 dell-bureau NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Dec 23 17:09:44 dell-bureau NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Dec 23 17:09:44 dell-bureau dhclient: Internet Systems Consortium DHCP Client V3.1.2
Dec 23 17:09:44 dell-bureau dhclient: Copyright 2004-2008 Internet Systems Consortium.
Dec 23 17:09:44 dell-bureau dhclient: All rights reserved.
Dec 23 17:09:44 dell-bureau dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Dec 23 17:09:44 dell-bureau dhclient: 
Dec 23 17:09:44 dell-bureau NetworkManager: <info>  dhclient started with pid 5589
Dec 23 17:09:44 dell-bureau NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Dec 23 17:09:44 dell-bureau NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec 23 17:09:44 dell-bureau NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Dec 23 17:09:44 dell-bureau NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Dec 23 17:09:44 dell-bureau NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Dec 23 17:09:44 dell-bureau dhclient: Listening on LPF/eth0/00:21:70:10:25:92
Dec 23 17:09:44 dell-bureau dhclient: Sending on   LPF/eth0/00:21:70:10:25:92
Dec 23 17:09:44 dell-bureau dhclient: Sending on   Socket/fallback
Dec 23 17:09:47 dell-bureau kernel: [ 4087.852006] eth0: no IPv6 routers present
Dec 23 17:09:48 dell-bureau dhclient: DHCPREQUEST of 192.168.0.1 on eth0 to 255.255.255.255 port 67
Dec 23 17:09:56 dell-bureau dhclient: DHCPREQUEST of 192.168.0.1 on eth0 to 255.255.255.255 port 67
Dec 23 17:10:06 dell-bureau dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Dec 23 17:10:12 dell-bureau dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Dec 23 17:10:27 dell-bureau dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 23 17:10:29 dell-bureau NetworkManager: <info>  (eth0): DHCP transaction took too long, stopping it.
Dec 23 17:10:30 dell-bureau NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 5589
Dec 23 17:10:30 dell-bureau NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Dec 23 17:10:30 dell-bureau NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Dec 23 17:10:30 dell-bureau NetworkManager: <info>  (eth0): device state change: 7 -> 9 (reason 5)
Dec 23 17:10:30 dell-bureau NetworkManager: <info>  Marking connection 'Ethernet automatique' invalid.
Dec 23 17:10:30 dell-bureau NetworkManager: <info>  Activation (eth0) failed.
Dec 23 17:10:30 dell-bureau NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Dec 23 17:10:30 dell-bureau NetworkManager: <info>  (eth0): device state change: 9 -> 3 (reason 0)
Dec 23 17:10:30 dell-bureau NetworkManager: <info>  (eth0): deactivating device (reason: 0).
[/font]*[NM announce "disconnected, you are now offline"]*

It seems that it can't retrieve any IP address, am I right?

---

### Post by doas777 on 2009-12-23
> **nico@nc said:**
> 
Could it be a problem with the computer's ethernet port or network card?

very possibly. nics don;t usually just go bad, but it does happen, especially on the port itself.

if the laptop works fine, on the same cable with the same modem, then yes, the problem is definitely with the PC itself, whether it be software or hardware.

---

### Post by iponeverything on 2009-12-24
```
Dec 23 17:07:06 dell-bureau kernel: [ 3927.021101] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 23 17:07:08 dell-bureau kernel: [ 3928.396756] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Dec 23 17:07:08 dell-bureau kernel: [ 3928.396760] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
Dec 23 17:07:08 dell-bureau kernel: [ 3928.397012] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 23 17:09:35 dell-bureau kernel: [ 4075.864880] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 23 17:09:37 dell-bureau kernel: [ 4077.376756] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Dec 23 17:09:37 dell-bureau kernel: [ 4077.376761] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
Dec 23 17:09:37 dell-bureau kernel: [ 4077.377017] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```

This is disturbing. Maybe something flaky with e1000e module.. Google around a bit with: e1000e "link becomes ready" "disabling TSO" Ubuntu etc.

---

