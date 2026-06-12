---
title: "WIred connection drops sporadically. Multiple mac-addresses?"
date: 2012-04-16
forum: Networking &amp; Wireless
---

### Post by svansen on 2012-04-16
HI.

I am currently setting up a new machine to work as a workstation as well as a rsync backup server.

I am running ubuntu 11.10. The machine has 2 network interfaces eth0 and eth1 but only one of them is plugged in. The machine is on a large network, and I have understood that it is behind a switch that has port-security.

My problem is that the connection gets dropped from time to time. When talking to the IT support they say my machine is sometimes sending out two mac-addresses on the same cable, which causes the switch to block me. I'm not sure how this could hapen, but perhaps you guys can help me.

Here are some stats and logs from my system

```

$ ifconfig 

eth0      Link encap:Ethernet  HWaddr 00:25:90:36:60:3c  
          inet addr:193.171.167.18  Bcast:193.171.167.255  Mask:255.255.255.0
          inet6 addr: fe80::225:90ff:fe36:603c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21971 (21.9 KB)  TX bytes:11291 (11.2 KB)
          Interrupt:16 Memory:fbce0000-fbd00000 

eth1      Link encap:Ethernet  HWaddr 00:25:90:36:60:3d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:fbde0000-fbe00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


```It doesn't seem to mather if I disable the eth1 device with
$ sudo ifconfig eth1 down

Here are my network card stats:

```

$ sudo lshw -class network

  *-network               
       description: Ethernet interface
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 00
       serial: 00:25:90:36:60:3c
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 firmware=1.9-0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:fbce0000-fbcfffff ioport:cc00(size=32) memory:fbcdc000-fbcdffff
  *-network
       description: Ethernet interface
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 00
       serial: 00:25:90:36:60:3d
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 firmware=1.9-0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:17 memory:fbde0000-fbdfffff ioport:dc00(size=32) memory:fbddc000-fbddffff



```output from syslog at the time the connection drops:

```

$ tail -f /var/log/syslog

Apr 16 17:36:02 moose kernel: [  109.912893] eth0: no IPv6 routers present
Apr 16 17:36:04 moose ntpdate[2198]: step time server 91.189.94.4 offset 0.919015 sec
Apr 16 17:36:12 moose NetworkManager[1154]: <info> (eth0): IP6 addrconf timed out or failed.
Apr 16 17:36:12 moose NetworkManager[1154]: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Apr 16 17:36:12 moose NetworkManager[1154]: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Timeout) started...
Apr 16 17:36:12 moose NetworkManager[1154]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Apr 16 17:36:12 moose NetworkManager[1154]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Apr 16 17:36:12 moose NetworkManager[1154]: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Timeout) complete.
Apr 16 17:37:15 moose kernel: [  181.531331] NET: Registered protocol family 24
Apr 16 17:37:31 moose kernel: [  197.669139] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 16 17:40:35 moose AptDaemon: INFO: Quitting due to inactivity
Apr 16 17:40:35 moose AptDaemon: INFO: Quitting was requested
Apr 16 17:47:29 moose NetworkManager[1154]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Apr 16 17:47:29 moose kernel: [  794.949308] e1000e: eth0 NIC Link is Down
Apr 16 17:47:33 moose NetworkManager[1154]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Apr 16 17:47:33 moose NetworkManager[1154]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
Apr 16 17:47:34 moose NetworkManager[1154]: <info> (eth0): canceled DHCP transaction, DHCP client pid 2158
Apr 16 17:47:34 moose avahi-daemon[1135]: Withdrawing address record for 193.171.167.18 on eth0.
Apr 16 17:47:34 moose avahi-daemon[1135]: Leaving mDNS multicast group on interface eth0.IPv4 with address 193.171.167.18.
Apr 16 17:47:34 moose avahi-daemon[1135]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 16 17:47:34 moose dbus[1124]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Apr 16 17:47:34 moose dbus[1124]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'

```

lastly I can say that my /etc/network/interfaces only has these two lines:

auto lo
iface lo inet loopback

Any ideas on how to make this stable??

Thanx

---

### Post by roelforg on 2012-04-16
> **svansen said:**
> HI.

I am currently setting up a new machine to work as a workstation as well as a rsync backup server.

I am running ubuntu 11.10. The machine has 2 network interfaces eth0 and eth1 but only one of them is plugged in. The machine is on a large network, and I have understood that it is behind a switch that has port-security.

My problem is that the connection gets dropped from time to time. When talking to the IT support they say my machine is sometimes sending out two mac-addresses on the same cable, which causes the switch to block me. I'm not sure how this could hapen, but perhaps you guys can help me.

Here are some stats and logs from my system

```

$ ifconfig 

eth0      Link encap:Ethernet  HWaddr 00:25:90:36:60:3c  
          inet addr:193.171.167.18  Bcast:193.171.167.255  Mask:255.255.255.0
          inet6 addr: fe80::225:90ff:fe36:603c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21971 (21.9 KB)  TX bytes:11291 (11.2 KB)
          Interrupt:16 Memory:fbce0000-fbd00000 

eth1      Link encap:Ethernet  HWaddr 00:25:90:36:60:3d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:fbde0000-fbe00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


```It doesn't seem to mather if I disable the eth1 device with
$ sudo ifconfig eth1 down

Here are my network card stats:

```

$ sudo lshw -class network

  *-network               
       description: Ethernet interface
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 00
       serial: 00:25:90:36:60:3c
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 firmware=1.9-0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:fbce0000-fbcfffff ioport:cc00(size=32) memory:fbcdc000-fbcdffff
  *-network
       description: Ethernet interface
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 00
       serial: 00:25:90:36:60:3d
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 firmware=1.9-0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:17 memory:fbde0000-fbdfffff ioport:dc00(size=32) memory:fbddc000-fbddffff



```output from syslog at the time the connection drops:

```

$ tail -f /var/log/syslog

Apr 16 17:36:02 moose kernel: [  109.912893] eth0: no IPv6 routers present
Apr 16 17:36:04 moose ntpdate[2198]: step time server 91.189.94.4 offset 0.919015 sec
Apr 16 17:36:12 moose NetworkManager[1154]: <info> (eth0): IP6 addrconf timed out or failed.
Apr 16 17:36:12 moose NetworkManager[1154]: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Apr 16 17:36:12 moose NetworkManager[1154]: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Timeout) started...
Apr 16 17:36:12 moose NetworkManager[1154]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Apr 16 17:36:12 moose NetworkManager[1154]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Apr 16 17:36:12 moose NetworkManager[1154]: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Timeout) complete.
Apr 16 17:37:15 moose kernel: [  181.531331] NET: Registered protocol family 24
Apr 16 17:37:31 moose kernel: [  197.669139] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 16 17:40:35 moose AptDaemon: INFO: Quitting due to inactivity
Apr 16 17:40:35 moose AptDaemon: INFO: Quitting was requested
Apr 16 17:47:29 moose NetworkManager[1154]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Apr 16 17:47:29 moose kernel: [  794.949308] e1000e: eth0 NIC Link is Down
Apr 16 17:47:33 moose NetworkManager[1154]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Apr 16 17:47:33 moose NetworkManager[1154]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
Apr 16 17:47:34 moose NetworkManager[1154]: <info> (eth0): canceled DHCP transaction, DHCP client pid 2158
Apr 16 17:47:34 moose avahi-daemon[1135]: Withdrawing address record for 193.171.167.18 on eth0.
Apr 16 17:47:34 moose avahi-daemon[1135]: Leaving mDNS multicast group on interface eth0.IPv4 with address 193.171.167.18.
Apr 16 17:47:34 moose avahi-daemon[1135]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 16 17:47:34 moose dbus[1124]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Apr 16 17:47:34 moose dbus[1124]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'

```lastly I can say that my /etc/network/interfaces only has these two lines:

auto lo
iface lo inet loopback

Any ideas on how to make this stable??

Thanx

Idea, only connect one of the network cards?

---

### Post by svansen on 2012-04-16
There is only one connected.

---

### Post by svansen on 2012-04-17
Was able to solve the problem.

The issue was the motherboard BMC IPMI feature. This has it own MAC address that causes problems for switches with port-security.

There is a dedicated LAN-port for the IPMI, but if only one cable is plugged in, the IPMI will "hijack" this one and send out ocasional arp requests on the same IP = problems.

Turning these off using openipm should solve the problem.

---

