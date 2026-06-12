---
title: "DHCP issue, netword card"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by SatishP on 2009-11-03
Hello All,
This is my third attempt to get my Davicom card working in Ubuntu. I am hoping there would be some progress ;)

I am running Windows 7 RC and Ubuntu alongside. My ethernet connection (wired) goes to my router (Pronet Wireless Router 54Mbps) and then to my ISP-supplied modem. My internet connects fine in Win 7 and all is fine there. I (and my friends)can connect to the internet through my router over wifi too. But in Ubuntu, I do not have a network. Infact I am posting in this forum using my work laptop accessing internet through my router as my Ubuntu sits without a network in my home pc.

Windows 7 is configured to get an IP address from the router and it does. Here's the ipconfig output from Win 7
```
Windows IP Configuration

   Host Name . . . . . . . . . . . . : SatishPC
   Primary Dns Suffix  . . . . . . . : 
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection 2:

   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : DAVICOM 9102/A PCI Fast Ethernet Adapter 
   Physical Address. . . . . . . . . : 00-80-AD-84-F2-F8
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::bd36:e1ad:5573:3ebb%13(Preferred) 
   IPv4 Address. . . . . . . . . . . : 192.168.10.101(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Tuesday, November 03, 2009 1:47:24 PM
   Lease Expires . . . . . . . . . . : Tuesday, November 03, 2009 7:47:31 PM
   Default Gateway . . . . . . . . . : 192.168.10.1
   DHCP Server . . . . . . . . . . . : 192.168.10.1
   DHCPv6 IAID . . . . . . . . . . . : 218136749
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-11-97-A3-FE-00-13-D3-08-4B-46
   DNS Servers . . . . . . . . . . . : 59.144.127.16
                                       59.144.127.17
   NetBIOS over Tcpip. . . . . . . . : Enabled
```

And here's the ifconfig output from Ubuntu:
```
eth0     Link encap:Ethernet   HWaddr 00:80:ad:84:f2:f8
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)   TX bytes (0.0 B)
         Interrupt:17 Base address:0xd000

eth0:avahi Link encap:Ethernet   HWaddr 00:80:ad:84:f2:f8
         inet addr:169.254.12.7   Bcast:169.254.255.255  Mask:255.255.0.0
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         Interrupt:17 Base address:0xd000
```

The /etc/network/interfaces file:-
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

The /etc/resolv.conf file:-
```

pdns 59.144.127.16
sdns 59.144.127.17
```

I can ping my ethernet card using   [FONT="Courier New"]**ping 169.254.12.7**[/FONT]   and this confirms (I guess) that my card is ok.
But when I try   [FONT="Courier New"]**ping 192.168.10.1**[/FONT]   I get a 'Destination Host Unreachable. So the router is not accessible.

Here's the routing information:
```
satish@ubuntu:-$ route -n
KERNEL IP routing table
Destination     Gateway        Genmask      Flags  Metric  Ref    Use  Iface
169.254.0.0     0.0.0.0        255.255.0.0  U      0       0      0    eth0
0.0.0.0         0.0.0.0        0.0.0.0      U      0       0      0    eth0
```

I added my router's IP as the default gateway
```
sudo route add default gw 192.168.10.1 dev eth0
```

Here's the new route info
```
satish@ubuntu:-$ route -n
KERNEL IP routing table
Destination     Gateway        Genmask      Flags  Metric  Ref    Use  Iface
169.254.0.0     0.0.0.0        255.255.0.0  U      0       0      0    eth0
0.0.0.0         192.168.10.1   0.0.0.0      UG     0       0      0    eth0
0.0.0.0         0.0.0.0        0.0.0.0      U      0       0      0    eth0
```
but to no effect. 

Can anyone help me out?

---

### Post by Iowan on 2009-11-03
The 169.254.X.X address is an avahi address - which usually means DHCP failed. Unless you're intentionally using **avahi**, it also means that your machine is probably in a subnet by itself... not too useful. Check **lshw -C network** to see if interface gets an alias (like eth0) and has a driver associated.

---

### Post by lswb on 2009-11-03
So you are using /etc/network/interfaces to configure your network rather than Network Manager, is that correct?

How did your /etc/resolv.conf get those lines in it. I'm not familiar with the terms 'pdns' or 'sdns' in the context of /etc/resolv.conf and don't see them mentioned in the man page. Shouldn't that be

```

nameserver 59.144.127.16
nameserver 59.144.127.17

```

---

### Post by SatishP on 2009-11-04
> **Iowan said:**
> The 169.254.X.X address is an avahi address - which usually means DHCP failed. Unless you're intentionally using **avahi**, it also means that your machine is probably in a subnet by itself... not too useful. Check **lshw -C network** to see if interface gets an alias (like eth0) and has a driver associated.

Here's the output from **lshw -C network**
```

 *-network
    description: Ethernet interface
    product: 21x4x DEC-Tulip compatible 10/100 Ethernet
    vendor: Davicom Semiconductor, Inc
    physical id: 2
    bus info: pci@0000:01:02.0
    logical name: eth0
    version: 31
    serial: 00:80:ad:84:f2:f8
    width: 32 bits
    clock: 33MHz
    capabilities: bus_master cap_list ethernet physical
    configuration: broadcast=yes driver=dmfe driverversion=1.36.4 latency=32 maxlatency=40 mingnt=20 module=dmfe multicast=yes
 *-network DISABLED
    description: Ethernet interface
    physical id: 3
    logical name: pan0
    serial: c6:6a:35:9d:e6:a5
    capabilities: ethernet physical
    configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

Does this make any sense; where the problem could be?

---

### Post by SatishP on 2009-11-04
> **lswb said:**
> So you are using /etc/network/interfaces to configure your network rather than Network Manager, is that correct?

How did your /etc/resolv.conf get those lines in it. I'm not familiar with the terms 'pdns' or 'sdns' in the context of /etc/resolv.conf and don't see them mentioned in the man page. Shouldn't that be

```

nameserver 59.144.127.16
nameserver 59.144.127.17

```

I checked again and saw that it is 'nameserver' now. I removed network-manager and tried 'wicd'. As that didn't help too, I reverted to 'network-manager'. So this might have set the DNS values right in the resolv.conf. In any case, the network is still down and I can't figure out what's wrong.

---

### Post by Iowan on 2009-11-04
Same issues - no "real" DHCP address?

---

### Post by mpokrywka on 2009-11-04
Because you use NetworkManager, remove lines:
```
auto eth0
iface eth0 inet dhcp
```
form /etc/network/interfaces

Reboot and check if internet connection works.

Of not, paste here log of NetworkManager attempts:
```

tail -n 200 /var/log/daemon.log

```

---

### Post by SatishP on 2009-11-05
> **mpokrywka said:**
> Because you use NetworkManager, remove lines:
```
auto eth0
iface eth0 inet dhcp
```
form /etc/network/interfaces
Reboot and check if internet connection works.
Of not, paste here log of NetworkManager attempts:
```

tail -n 200 /var/log/daemon.log

```

Removing the 'eth0' lines in /etc/network/interfaces and subsequent reboot did not help.

Here's the daemon.log (apologies for the huge text)
```
Nov  4 21:48:08 ubuntu ntpdate[9667]: can't find host ntp.ubuntu.com 
Nov  4 21:48:08 ubuntu ntpdate[9667]: no servers can be used, exiting
Nov  4 21:51:14 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov  4 21:51:19 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov  4 21:51:30 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Nov  4 21:51:44 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Nov  4 21:52:00 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Nov  4 21:52:12 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Nov  4 21:52:15 ubuntu dhclient: No DHCPOFFERS received.
Nov  4 21:52:15 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov  4 21:54:48 ubuntu console-kit-daemon[2398]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Nov  4 21:54:48 ubuntu last message repeated 4 times
Nov  4 21:54:48 ubuntu init: tty4 main process (2186) killed by TERM signal
Nov  4 21:54:48 ubuntu init: tty5 main process (2187) killed by TERM signal
Nov  4 21:54:48 ubuntu init: tty2 main process (2193) killed by TERM signal
Nov  4 21:54:48 ubuntu init: tty3 main process (2196) killed by TERM signal
Nov  4 21:54:48 ubuntu init: tty6 main process (2197) killed by TERM signal
Nov  4 21:54:48 ubuntu init: tty1 main process (2898) killed by TERM signal
Nov  4 21:54:48 ubuntu console-kit-daemon[2398]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Nov  4 21:54:48 ubuntu last message repeated 3 times
Nov  4 21:54:48 ubuntu x-session-manager[2938]: WARNING: Failed to get protocol version from GDM 
Nov  4 21:54:48 ubuntu console-kit-daemon[2398]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Nov  4 21:54:49 ubuntu console-kit-daemon[2398]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `(null)' 
Nov  4 21:54:49 ubuntu console-kit-daemon[2398]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
Nov  4 21:54:49 ubuntu console-kit-daemon[2398]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
Nov  4 21:54:53 ubuntu bluetoothd[2556]: bridge pan0 removed
Nov  4 21:54:53 ubuntu bluetoothd[2556]: Stopping SDP server
Nov  4 21:54:53 ubuntu bluetoothd[2556]: Exit
Nov  5 18:14:27 ubuntu dhclient: Listening on LPF/eth0/00:80:ad:84:f2:f8
Nov  5 18:14:27 ubuntu dhclient: Sending on   LPF/eth0/00:80:ad:84:f2:f8
Nov  5 18:14:27 ubuntu dhclient: Sending on   Socket/fallback
Nov  5 18:14:27 ubuntu acpid: client connected from 2500[111:120] 
Nov  5 18:14:27 ubuntu bluetoothd[2507]: Bluetooth daemon
Nov  5 18:14:27 ubuntu bluetoothd[2507]: Starting SDP server
Nov  5 18:14:27 ubuntu bluetoothd[2507]: bridge pan0 created
Nov  5 18:14:27 ubuntu bluetoothd[2507]: Registered interface org.bluez.Service on path /org/bluez/2507/any
Nov  5 18:14:27 ubuntu bluetoothd[2507]: Starting experimental netlink support
Nov  5 18:14:27 ubuntu bluetoothd[2507]: Failed to find Bluetooth netlink family
Nov  5 18:14:28 ubuntu NetworkManager: <info>  starting... 
Nov  5 18:14:28 ubuntu NetworkManager: <info>  (eth0): new Ethernet device (driver: 'dmfe') 
Nov  5 18:14:28 ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_80_ad_84_f2_f8 
Nov  5 18:14:28 ubuntu NetworkManager: <info>  (ttyS1): ignoring due to lack of mobile broadband capabilties 
Nov  5 18:14:28 ubuntu NetworkManager: <info>  (ttyS0): ignoring due to lack of mobile broadband capabilties 
Nov  5 18:14:28 ubuntu NetworkManager: <info>  Trying to start the supplicant... 
Nov  5 18:14:28 ubuntu NetworkManager: <info>  Trying to start the system settings daemon... 
Nov  5 18:14:28 ubuntu avahi-daemon[2588]: Found user 'avahi' (UID 110) and group 'avahi' (GID 119).
Nov  5 18:14:28 ubuntu avahi-daemon[2588]: Successfully dropped root privileges.
Nov  5 18:14:28 ubuntu avahi-daemon[2588]: avahi-daemon 0.6.23 starting up.
Nov  5 18:14:28 ubuntu avahi-daemon[2588]: Successfully called chroot().
Nov  5 18:14:28 ubuntu avahi-daemon[2588]: Successfully dropped remaining capabilities.
Nov  5 18:14:28 ubuntu nm-system-settings:    SCPlugin-Ifupdown: init!
Nov  5 18:14:28 ubuntu nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Nov  5 18:14:28 ubuntu nm-system-settings:    SCPluginIfupdown: guessed connection type (eth0) = 802-3-ethernet
Nov  5 18:14:28 ubuntu avahi-daemon[2588]: No service file found in /etc/avahi/services.
Nov  5 18:14:28 ubuntu avahi-daemon[2588]: Network interface enumeration completed.
Nov  5 18:14:28 ubuntu avahi-daemon[2588]: Registering HINFO record with values 'I686'/'LINUX'.
Nov  5 18:14:28 ubuntu avahi-daemon[2588]: Server startup complete. Host name is ubuntu.local. Local service cookie is 1378932578.
Nov  5 18:14:28 ubuntu nm-system-settings:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, autoconnect:0, id:Ifupdown (eth0), uuid: 681b428f-0000-0000-0000-000039000000
Nov  5 18:14:28 ubuntu nm-system-settings:    SCPlugin-Ifupdown: autoconnect
Nov  5 18:14:28 ubuntu nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Nov  5 18:14:28 ubuntu nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_80_ad_84_f2_f8, iface: eth0): well known
Nov  5 18:14:28 ubuntu nm-system-settings:    Ifupdown: get unmanaged devices count: 1
Nov  5 18:14:28 ubuntu nm-system-settings:    SCPlugin-Ifupdown: (156616448) ... get_connections.
Nov  5 18:14:28 ubuntu nm-system-settings:    SCPlugin-Ifupdown: (156616448) ... get_connections (managed=false): return empty list.
Nov  5 18:14:28 ubuntu nm-system-settings:    Ifupdown: get unmanaged devices count: 1
Nov  5 18:14:28 ubuntu nm-system-settings:    SCPlugin-Ifupdown: end _init.
Nov  5 18:14:28 ubuntu nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Nov  5 18:14:28 ubuntu nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Nov  5 18:14:28 ubuntu NetworkManager: <info>  (eth0): now unmanaged 
Nov  5 18:14:28 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov  5 18:14:29 ubuntu acpid: client connected from 2562[0:0] 
Nov  5 18:14:37 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Nov  5 18:14:54 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
Nov  5 18:15:14 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Nov  5 18:15:14 ubuntu console-kit-daemon[2350]: WARNING: Couldn't read /proc/2349/environ: Failed to open file '/proc/2349/environ': No such file or directory 
Nov  5 18:15:22 ubuntu x-session-manager[2876]: WARNING: Could not launch application 'wicd-tray.desktop': Unable to start application: Failed to execute child process "wicd-client" (No such file or directory) 
Nov  5 18:15:23 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Nov  5 18:15:23 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Nov  5 18:15:30 ubuntu dhclient: No DHCPOFFERS received.
Nov  5 18:15:30 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov  5 18:15:30 ubuntu avahi-autoipd(eth0)[3224]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Nov  5 18:15:30 ubuntu avahi-autoipd(eth0)[3224]: Successfully called chroot().
Nov  5 18:15:30 ubuntu avahi-autoipd(eth0)[3224]: Successfully dropped root privileges.
Nov  5 18:15:30 ubuntu avahi-autoipd(eth0)[3224]: Starting with address 169.254.12.7
Nov  5 18:15:35 ubuntu avahi-autoipd(eth0)[3224]: Callout BIND, address 169.254.12.7 on interface eth0
Nov  5 18:15:35 ubuntu avahi-daemon[2588]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.12.7.
Nov  5 18:15:35 ubuntu avahi-daemon[2588]: New relevant interface eth0.IPv4 for mDNS.
Nov  5 18:15:35 ubuntu avahi-daemon[2588]: Registering new address record for 169.254.12.7 on eth0.IPv4.
Nov  5 18:15:39 ubuntu avahi-autoipd(eth0)[3224]: Successfully claimed IP address 169.254.12.7
Nov  5 18:16:31 ubuntu ntpdate[3310]: can't find host ntp.ubuntu.com 
Nov  5 18:16:31 ubuntu ntpdate[3310]: no servers can be used, exiting
Nov  5 18:17:00 ubuntu console-kit-daemon[2350]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Nov  5 18:17:00 ubuntu last message repeated 4 times
Nov  5 18:17:00 ubuntu init: tty4 main process (2149) killed by TERM signal
Nov  5 18:17:00 ubuntu init: tty5 main process (2150) killed by TERM signal
Nov  5 18:17:00 ubuntu init: tty2 main process (2153) killed by TERM signal
Nov  5 18:17:00 ubuntu init: tty3 main process (2154) killed by TERM signal
Nov  5 18:17:00 ubuntu init: tty6 main process (2155) killed by TERM signal
Nov  5 18:17:00 ubuntu init: tty1 main process (2836) killed by TERM signal
Nov  5 18:17:00 ubuntu console-kit-daemon[2350]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Nov  5 18:17:00 ubuntu console-kit-daemon[2350]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Nov  5 18:17:05 ubuntu bluetoothd[2507]: bridge pan0 removed
Nov  5 18:17:05 ubuntu bluetoothd[2507]: Stopping SDP server
Nov  5 18:17:05 ubuntu bluetoothd[2507]: Exit
Nov  5 18:18:19 ubuntu acpid: client connected from 2399[111:120] 
Nov  5 18:18:19 ubuntu bluetoothd[2413]: Bluetooth daemon
Nov  5 18:18:19 ubuntu bluetoothd[2413]: Starting SDP server
Nov  5 18:18:19 ubuntu bluetoothd[2413]: bridge pan0 created
Nov  5 18:18:19 ubuntu bluetoothd[2413]: Registered interface org.bluez.Service on path /org/bluez/2413/any
Nov  5 18:18:19 ubuntu bluetoothd[2413]: Starting experimental netlink support
Nov  5 18:18:19 ubuntu bluetoothd[2413]: Failed to find Bluetooth netlink family
Nov  5 18:18:20 ubuntu NetworkManager: <info>  starting... 
Nov  5 18:18:20 ubuntu NetworkManager: <info>  (eth0): new Ethernet device (driver: 'dmfe') 
Nov  5 18:18:20 ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_80_ad_84_f2_f8 
Nov  5 18:18:20 ubuntu NetworkManager: <info>  (ttyS1): ignoring due to lack of mobile broadband capabilties 
Nov  5 18:18:20 ubuntu NetworkManager: <info>  (ttyS0): ignoring due to lack of mobile broadband capabilties 
Nov  5 18:18:20 ubuntu NetworkManager: <info>  Trying to start the supplicant... 
Nov  5 18:18:20 ubuntu NetworkManager: <info>  Trying to start the system settings daemon... 
Nov  5 18:18:20 ubuntu nm-system-settings:    SCPlugin-Ifupdown: init!
Nov  5 18:18:20 ubuntu nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Nov  5 18:18:20 ubuntu nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Nov  5 18:18:20 ubuntu nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_80_ad_84_f2_f8, iface: eth0): not well known
Nov  5 18:18:20 ubuntu nm-system-settings:    SCPlugin-Ifupdown: end _init.
Nov  5 18:18:20 ubuntu nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Nov  5 18:18:20 ubuntu nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Nov  5 18:18:20 ubuntu nm-system-settings:    SCPlugin-Ifupdown: (144500480) ... get_connections.
Nov  5 18:18:20 ubuntu nm-system-settings:    SCPlugin-Ifupdown: (144500480) ... get_connections (managed=false): return empty list.
Nov  5 18:18:20 ubuntu avahi-daemon[2494]: Found user 'avahi' (UID 110) and group 'avahi' (GID 119).
Nov  5 18:18:20 ubuntu avahi-daemon[2494]: Successfully dropped root privileges.
Nov  5 18:18:20 ubuntu avahi-daemon[2494]: avahi-daemon 0.6.23 starting up.
Nov  5 18:18:20 ubuntu avahi-daemon[2494]: Successfully called chroot().
Nov  5 18:18:20 ubuntu avahi-daemon[2494]: Successfully dropped remaining capabilities.
Nov  5 18:18:20 ubuntu nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Nov  5 18:18:20 ubuntu avahi-daemon[2494]: No service file found in /etc/avahi/services.
Nov  5 18:18:20 ubuntu avahi-daemon[2494]: Network interface enumeration completed.
Nov  5 18:18:20 ubuntu avahi-daemon[2494]: Registering HINFO record with values 'I686'/'LINUX'.
Nov  5 18:18:20 ubuntu avahi-daemon[2494]: Server startup complete. Host name is ubuntu.local. Local service cookie is 2992128924.
Nov  5 18:18:20 ubuntu acpid: client connected from 2468[0:0] 
Nov  5 18:18:24 ubuntu NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Nov  5 18:18:24 ubuntu NetworkManager: <info>  (eth0): bringing up device. 
Nov  5 18:18:24 ubuntu NetworkManager: <info>  (eth0): preparing device. 
Nov  5 18:18:24 ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Nov  5 18:18:31 ubuntu console-kit-daemon[2257]: WARNING: Couldn't read /proc/2256/environ: Failed to open file '/proc/2256/environ': No such file or directory 
Nov  5 18:18:38 ubuntu x-session-manager[2780]: WARNING: Could not launch application 'wicd-tray.desktop': Unable to start application: Failed to execute child process "wicd-client" (No such file or directory) 
Nov  5 18:21:49 ubuntu console-kit-daemon[2257]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Nov  5 18:21:50 ubuntu last message repeated 3 times
Nov  5 18:21:50 ubuntu init: tty4 main process (2058) killed by TERM signal
Nov  5 18:21:50 ubuntu init: tty5 main process (2059) killed by TERM signal
Nov  5 18:21:50 ubuntu init: tty2 main process (2065) killed by TERM signal
Nov  5 18:21:50 ubuntu init: tty3 main process (2069) killed by TERM signal
Nov  5 18:21:50 ubuntu init: tty6 main process (2070) killed by TERM signal
Nov  5 18:21:50 ubuntu init: tty1 main process (2742) killed by TERM signal
Nov  5 18:21:50 ubuntu console-kit-daemon[2257]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Nov  5 18:21:50 ubuntu console-kit-daemon[2257]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `<invalid>' 
Nov  5 18:21:50 ubuntu console-kit-daemon[2257]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
Nov  5 18:21:50 ubuntu console-kit-daemon[2257]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
Nov  5 18:21:54 ubuntu bluetoothd[2413]: bridge pan0 removed
Nov  5 18:21:54 ubuntu bluetoothd[2413]: Stopping SDP server
Nov  5 18:21:54 ubuntu bluetoothd[2413]: Exit
Nov  5 18:23:07 ubuntu acpid: client connected from 2398[111:120] 
Nov  5 18:23:07 ubuntu bluetoothd[2412]: Bluetooth daemon
Nov  5 18:23:07 ubuntu bluetoothd[2412]: Starting SDP server
Nov  5 18:23:07 ubuntu bluetoothd[2412]: bridge pan0 created
Nov  5 18:23:07 ubuntu bluetoothd[2412]: Registered interface org.bluez.Service on path /org/bluez/2412/any
Nov  5 18:23:07 ubuntu bluetoothd[2412]: Starting experimental netlink support
Nov  5 18:23:07 ubuntu bluetoothd[2412]: Failed to find Bluetooth netlink family
Nov  5 18:23:08 ubuntu NetworkManager: <info>  starting... 
Nov  5 18:23:08 ubuntu NetworkManager: <info>  (eth0): new Ethernet device (driver: 'dmfe') 
Nov  5 18:23:08 ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_80_ad_84_f2_f8 
Nov  5 18:23:08 ubuntu NetworkManager: <info>  (ttyS1): ignoring due to lack of mobile broadband capabilties 
Nov  5 18:23:08 ubuntu NetworkManager: <info>  (ttyS0): ignoring due to lack of mobile broadband capabilties 
Nov  5 18:23:08 ubuntu NetworkManager: <info>  Trying to start the supplicant... 
Nov  5 18:23:08 ubuntu NetworkManager: <info>  Trying to start the system settings daemon... 
Nov  5 18:23:08 ubuntu nm-system-settings:    SCPlugin-Ifupdown: init!
Nov  5 18:23:08 ubuntu nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Nov  5 18:23:08 ubuntu nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Nov  5 18:23:08 ubuntu nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_80_ad_84_f2_f8, iface: eth0): not well known
Nov  5 18:23:08 ubuntu nm-system-settings:    SCPlugin-Ifupdown: end _init.
Nov  5 18:23:08 ubuntu nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Nov  5 18:23:08 ubuntu nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Nov  5 18:23:08 ubuntu nm-system-settings:    SCPlugin-Ifupdown: (159999744) ... get_connections.
Nov  5 18:23:08 ubuntu nm-system-settings:    SCPlugin-Ifupdown: (159999744) ... get_connections (managed=false): return empty list.
Nov  5 18:23:08 ubuntu avahi-daemon[2493]: Found user 'avahi' (UID 110) and group 'avahi' (GID 119).
Nov  5 18:23:08 ubuntu avahi-daemon[2493]: Successfully dropped root privileges.
Nov  5 18:23:08 ubuntu avahi-daemon[2493]: avahi-daemon 0.6.23 starting up.
Nov  5 18:23:08 ubuntu avahi-daemon[2493]: Successfully called chroot().
Nov  5 18:23:08 ubuntu avahi-daemon[2493]: Successfully dropped remaining capabilities.
Nov  5 18:23:08 ubuntu nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Nov  5 18:23:08 ubuntu avahi-daemon[2493]: No service file found in /etc/avahi/services.
Nov  5 18:23:08 ubuntu avahi-daemon[2493]: Network interface enumeration completed.
Nov  5 18:23:08 ubuntu avahi-daemon[2493]: Registering HINFO record with values 'I686'/'LINUX'.
Nov  5 18:23:08 ubuntu avahi-daemon[2493]: Server startup complete. Host name is ubuntu.local. Local service cookie is 413707526.
Nov  5 18:23:08 ubuntu acpid: client connected from 2466[0:0] 
Nov  5 18:23:12 ubuntu NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Nov  5 18:23:12 ubuntu NetworkManager: <info>  (eth0): bringing up device. 
Nov  5 18:23:12 ubuntu NetworkManager: <info>  (eth0): preparing device. 
Nov  5 18:23:12 ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Nov  5 18:23:28 ubuntu console-kit-daemon[2256]: WARNING: Couldn't read /proc/2255/environ: Failed to open file '/proc/2255/environ': No such file or directory 
Nov  5 18:23:36 ubuntu x-session-manager[2781]: WARNING: Could not launch application 'wicd-tray.desktop': Unable to start application: Failed to execute child process "wicd-client" (No such file or directory) 
Nov  5 18:23:58 ubuntu hald: mounted /dev/sdb1 on behalf of uid 1000

```

---

### Post by mpokrywka on 2009-11-05
Log shows that network card tries to send packets, but doesn't seem to receive any.

This could be similar problem to:
[http://ubuntuforums.org/archive/index.php/t-186430.html](http://ubuntuforums.org/archive/index.php/t-186430.html)

Quick test - unload *dmfe* and *tulip* drivers, load only *dmfe* driver:
```
sudo rmmod dmfe
sudo rmmod tulip
sudo modprobe dmfe
```

If network is working after this operation (wait some time for NetworkManager to catch up), update initramfs so that 'tulip' driver will be permanently blacklisted:
```
sudo sh -c 'echo blacklist tulip >> /etc/modprobe.d/blacklist-local'
sudo update-initramfs -u -k all
```

---

### Post by SatishP on 2009-11-05
> **mpokrywka said:**
> Log shows that network card tries to send packets, but doesn't seem to receive any.

This could be similar problem to:
[http://ubuntuforums.org/archive/index.php/t-186430.html](http://ubuntuforums.org/archive/index.php/t-186430.html)

I tried the steps mentioned in that thread long back (infact in my first attempt) but none worked. I scoured the web for more than six months and tried everything I came across but nothing worked.

> **mpokrywka said:**
> Quick test - unload *dmfe* and *tulip* drivers, load only *dmfe* driver:
```
sudo rmmod dmfe
sudo rmmod tulip
sudo modprobe dmfe
```


I tried this but it seems that the *tulip* module was never loaded. Here's what I get:
```
satish@ubuntu:-$ sudo rmmod dmfe
satish@ubuntu:-$ sudo rmmod tulip
ERROR: Module tulip does not exist in /proc/modules
satish@ubuntu:-$ sudo modprobe dmfe
```

My network is still down. ](*,)

**Can my router be the culprit?** It isn't a branded one and I can't vouch for its support. Nevertheless, I have been happily using it in Windows for more than 2 years now.

Can it happen that my router is offering an IP when I boot in Windows but not when I boot in Ubuntu? I know it sounds lame, but I am open to anything and suspect everything :roll:

---

### Post by SatishP on 2009-11-05
Just in case someone can see what's missing, here's my router page:

<snip>

---

### Post by mpokrywka on 2009-11-05
To check if packets are received, run from terminal:
**sudo tcpdump -ni eth0**
and click on "Auto eth0" in NetworkManager to try to get connection.

But I suspect there won't be any replies because NetworkManager would log something - even invalid packets...

Maybe I am boring, but have you tried *tulip* driver instead of *dmfe*?
**sudo rmmod dmfe**
**sudo modprobe tulip**

---

### Post by SatishP on 2009-11-05
> **mpokrywka said:**
> Maybe I am boring, but have you tried *tulip* driver instead of *dmfe*?
**sudo rmmod dmfe**
**sudo modprobe tulip**

I tried this earlier too but no luck. Nevertheless I did it again.
Bringing up tulip does not bring the interface up. Network Manager shows 'No devices found'.

> **mpokrywka said:**
> To check if packets are received, run from terminal:
**sudo tcpdump -ni eth0**
and click on "Auto eth0" in NetworkManager to try to get connection.

But I suspect there won't be any replies because NetworkManager would log something - even invalid packets...

There's no 'Auto eth0' for me. I remember I had it earlier (maybe in Hardy). Now it is **'Wired Connection 1'**. And beside the name there's a grayed **'never'** text. No checkboxes to select or unselect an interface.
In any case, after the 'tcpdump' command, I open Network Connections.. nothing happens. So I click 'Edit' and choose 'Apply' on the ensuing dialog (just to effect a save) but still nothing happens.

---

### Post by Iowan on 2009-11-05
> **SatishP said:**
>  And beside the name there's a grayed **'never'** text.
That indicates the last time the interface was used.

---

### Post by SatishP on 2009-11-06
> 
<snip>

Looks like the image hosting service is not reliable and loading 'other' :wink: images first before my actual image. I'll be damned if I use them again. Apologies to all for 'unexpected' results with the link and thanks to 'forestpiskie' for taking action.

Here are my router settings:
```
LAN:
   IP Address:      192.168.10.1
   Subnet:          255.255.255.0

WAN:
   IP Address:      192.168.1.2
   Subnet:          255.255.255.0
   Default Gateway: 192.168.1.1

Wireless:
   IP Address:      192.168.10.1
```

Based on this, do I have to set something in Ubuntu? Like, maybe the ***default gateway*** to be '192.168.10.1' (ip of the router). Everytime I start the system, I see the routing table empty. When I add the default gateway, sometimes I get a *'SIOCADDRT: No such process'* error and other times, it suceeds. But I never managed to get my network up.

---

### Post by mpokrywka on 2009-11-06
Let's try again with tcpdump to check if any packets are sent/received, this time also turn on driver debugging:

Run from terminal:
# Stop avahi/zeroconf to disable spamming network activity:
**sudo stop avahi-daemon**
# Load driver with debugging enabled:
**sudo rmmod dmfe**
**sudo modprobe dmfe debug=1**
# Capture packets:
**sudo tcpdump -ni eth0**

then LEFT click on NetwokManager (NM) icon, then LEFT click on bold "Auto eth0/Wired connection 1/etc" under grayed "Wired Network" and above "Disconnect" - do not go into connection setup, only click on NM applet.

Wait until NM finishes (unsuccessfully?) its magic, press Ctrl+C in terminal (stop tcpdump) and paste here what tcpdump catched. Also paste output of **dmesg | grep -A9999 dmfe:**

Your default gateway setup fails because gateway must be inside reachable network, but you probably have no valid IP address.

---

### Post by SatishP on 2009-11-06
> **mpokrywka said:**
> # Stop avahi/zeroconf to disable spamming network activity:
**sudo stop avahi-daemon**

I get an error on this
```
satish@ubuntu:~$ sudo stop avahi-daemon
stop: Unknown job: avahi-daemon
```

> 
# Load driver with debugging enabled:
**sudo rmmod dmfe**
**sudo modprobe dmfe debug=1**
# Capture packets:
**sudo tcpdump -ni eth0**

then LEFT click on NetwokManager (NM) icon, then LEFT click on bold "Auto eth0/Wired connection 1/etc" under grayed "Wired Network" and above "Disconnect" - do not go into connection setup, only click on NM applet.

Wait until NM finishes (unsuccessfully?) its magic, press Ctrl+C in terminal (stop tcpdump) and paste here what tcpdump catched.

I could not find any 'Disconnect' button (NM image attached) ahd hence could do nothing. As a result, nothing was caught by tcpdump.

```
satish@ubuntu:~$ sudo tcpdump -ni eth0
tcpdump: WARNING: eth0: no IPv4 address assigned
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
^C
0 packets captured
0 packets received by filter
0 packets dropped by kernel
```

> 
Also paste output of **dmesg | grep -A9999 dmfe:**

Your default gateway setup fails because gateway must be inside reachable network, but you probably have no valid IP address.

Here's the dmesg log
```
7] dmfe: dmfe_free_rxbuffer() 0
[  788.844061] dmfe: dmfe_init_dm910x() 0
[  788.844167] dmfe: dmfe_parse_srom()  0
[  788.845111] dmfe: dmfe_descriptor_init() 0
[  788.845142] dmfe: send_filter_frame() 0
[  789.844011] dmfe: dmfe_timer() 0
[  792.844012] dmfe: dmfe_timer() 0
[  792.844020] eth0: Tx timeout - resetting
[  792.844022] dmfe: Dynamic Reset device 1
[  792.844024] dmfe: dmfe_dynamic_reset() 0
[  792.844040] dmfe: dmfe_free_rxbuffer() 0
[  792.844061] dmfe: dmfe_init_dm910x() 0
[  792.844167] dmfe: dmfe_parse_srom()  0
[  792.845112] dmfe: dmfe_descriptor_init() 0
[  792.845141] dmfe: send_filter_frame() 0
[  793.844009] dmfe: dmfe_timer() 0
[  796.844009] dmfe: dmfe_timer() 0
[  796.844016] eth0: Tx timeout - resetting
[  796.844019] dmfe: Dynamic Reset device 1
[  796.844021] dmfe: dmfe_dynamic_reset() 0
[  796.844037] dmfe: dmfe_free_rxbuffer() 0
[  796.844060] dmfe: dmfe_init_dm910x() 0
[  796.844167] dmfe: dmfe_parse_srom()  0
[  796.845111] dmfe: dmfe_descriptor_init() 0
[  796.845141] dmfe: send_filter_frame() 0
[  797.844009] dmfe: dmfe_timer() 0
[  800.844008] dmfe: dmfe_timer() 0
[  800.844015] eth0: Tx timeout - resetting
[  800.844017] dmfe: Dynamic Reset device 1
[  800.844019] dmfe: dmfe_dynamic_reset() 0
[  800.844035] dmfe: dmfe_free_rxbuffer() 0
[  800.844055] dmfe: dmfe_init_dm910x() 0
[  800.844162] dmfe: dmfe_parse_srom()  0
[  800.845106] dmfe: dmfe_descriptor_init() 0
[  800.845134] dmfe: send_filter_frame() 0
[  801.844007] dmfe: dmfe_timer() 0
[  804.844009] dmfe: dmfe_timer() 0
[  804.844017] eth0: Tx timeout - resetting
[  804.844019] dmfe: Dynamic Reset device 1
[  804.844021] dmfe: dmfe_dynamic_reset() 0
[  804.844037] dmfe: dmfe_free_rxbuffer() 0
[  804.844058] dmfe: dmfe_init_dm910x() 0
[  804.844165] dmfe: dmfe_parse_srom()  0
[  804.845108] dmfe: dmfe_descriptor_init() 0
[  804.845140] dmfe: send_filter_frame() 0
[  805.844009] dmfe: dmfe_timer() 0
[  808.844008] dmfe: dmfe_timer() 0
[  808.844016] eth0: Tx timeout - resetting
[  808.844018] dmfe: Dynamic Reset device 1
[  808.844020] dmfe: dmfe_dynamic_reset() 0
[  808.844036] dmfe: dmfe_free_rxbuffer() 0
[  808.844057] dmfe: dmfe_init_dm910x() 0
[  808.844163] dmfe: dmfe_parse_srom()  0
[  808.845106] dmfe: dmfe_descriptor_init() 0
[  808.845134] dmfe: send_filter_frame() 0
[  809.844007] dmfe: dmfe_timer() 0
[  812.844009] dmfe: dmfe_timer() 0
[  812.844017] eth0: Tx timeout - resetting
[  812.844019] dmfe: Dynamic Reset device 1
[  812.844021] dmfe: dmfe_dynamic_reset() 0
[  812.844037] dmfe: dmfe_free_rxbuffer() 0
[  812.844058] dmfe: dmfe_init_dm910x() 0
[  812.844165] dmfe: dmfe_parse_srom()  0
[  812.845110] dmfe: dmfe_descriptor_init() 0
[  812.845142] dmfe: send_filter_frame() 0
[  813.844009] dmfe: dmfe_timer() 0
[  816.844006] dmfe: dmfe_timer() 0
[  816.844013] eth0: Tx timeout - resetting
[  816.844015] dmfe: Dynamic Reset device 1
[  816.844017] dmfe: dmfe_dynamic_reset() 0
[  816.844033] dmfe: dmfe_free_rxbuffer() 0
[  816.844053] dmfe: dmfe_init_dm910x() 0
[  816.844160] dmfe: dmfe_parse_srom()  0
[  816.845106] dmfe: dmfe_descriptor_init() 0
[  816.845134] dmfe: send_filter_frame() 0
[  817.844008] dmfe: dmfe_timer() 0
[  820.844008] dmfe: dmfe_timer() 0
[  820.844016] eth0: Tx timeout - resetting
[  820.844018] dmfe: Dynamic Reset device 1
[  820.844020] dmfe: dmfe_dynamic_reset() 0
[  820.844036] dmfe: dmfe_free_rxbuffer() 0
[  820.844057] dmfe: dmfe_init_dm910x() 0
[  820.844163] dmfe: dmfe_parse_srom()  0
[  820.845106] dmfe: dmfe_descriptor_init() 0
[  820.845136] dmfe: send_filter_frame() 0
[  821.844007] dmfe: dmfe_timer() 0
[  824.844009] dmfe: dmfe_timer() 0
[  824.844017] eth0: Tx timeout - resetting
[  824.844019] dmfe: Dynamic Reset device 1
[  824.844021] dmfe: dmfe_dynamic_reset() 0
[  824.844037] dmfe: dmfe_free_rxbuffer() 0
[  824.844058] dmfe: dmfe_init_dm910x() 0
[  824.844164] dmfe: dmfe_parse_srom()  0
[  824.845109] dmfe: dmfe_descriptor_init() 0
[  824.845138] dmfe: send_filter_frame() 0
[  825.844007] dmfe: dmfe_timer() 0
[  828.844009] dmfe: dmfe_timer() 0
[  828.844016] eth0: Tx timeout - resetting
[  828.844018] dmfe: Dynamic Reset device 1
[  828.844020] dmfe: dmfe_dynamic_reset() 0
[  828.844036] dmfe: dmfe_free_rxbuffer() 0
[  828.844057] dmfe: dmfe_init_dm910x() 0
[  828.844164] dmfe: dmfe_parse_srom()  0
[  828.845106] dmfe: dmfe_descriptor_init() 0
[  828.845137] dmfe: send_filter_frame() 0
[  829.844008] dmfe: dmfe_timer() 0
[  832.844007] dmfe: dmfe_timer() 0
[  832.844014] eth0: Tx timeout - resetting
[  832.844016] dmfe: Dynamic Reset device 1
[  832.844019] dmfe: dmfe_dynamic_reset() 0
[  832.844035] dmfe: dmfe_free_rxbuffer() 0
[  832.844055] dmfe: dmfe_init_dm910x() 0
[  832.844162] dmfe: dmfe_parse_srom()  0
[  832.845106] dmfe: dmfe_descriptor_init() 0
[  832.845134] dmfe: send_filter_frame() 0
[  833.844007] dmfe: dmfe_timer() 0
[  836.844020] dmfe: dmfe_timer() 0
[  836.844028] eth0: Tx timeout - resetting
[  836.844030] dmfe: Dynamic Reset device 1
[  836.844032] dmfe: dmfe_dynamic_reset() 0
[  836.844048] dmfe: dmfe_free_rxbuffer() 0
[  836.844071] dmfe: dmfe_init_dm910x() 0
[  836.844178] dmfe: dmfe_parse_srom()  0
[  836.845121] dmfe: dmfe_descriptor_init() 0
[  836.845153] dmfe: send_filter_frame() 0
[  837.844010] dmfe: dmfe_timer() 0
[  838.721982] device eth0 left promiscuous mode
[  838.721988] dmfe: dmfe_set_filter_mode() 0
[  838.721992] dmfe: Set multicast address 2
[  838.721994] dmfe: send_filter_frame() 0
[  840.844008] dmfe: dmfe_timer() 0
[  840.844017] eth0: Tx timeout - resetting
[  840.844019] dmfe: Dynamic Reset device 1
[  840.844021] dmfe: dmfe_dynamic_reset() 0
[  840.844037] dmfe: dmfe_free_rxbuffer() 0
[  840.844059] dmfe: dmfe_init_dm910x() 0
[  840.844165] dmfe: dmfe_parse_srom()  0
[  840.845109] dmfe: dmfe_descriptor_init() 0
[  840.845136] dmfe: send_filter_frame() 0
[  841.844010] dmfe: dmfe_timer() 0
[  844.844014] dmfe: dmfe_timer() 0
[  844.844022] eth0: Tx timeout - resetting
[  844.844024] dmfe: Dynamic Reset device 1
[  844.844027] dmfe: dmfe_dynamic_reset() 0
[  844.844043] dmfe: dmfe_free_rxbuffer() 0
[  844.844064] dmfe: dmfe_init_dm910x() 0
[  844.844170] dmfe: dmfe_parse_srom()  0
[  844.845114] dmfe: dmfe_descriptor_init() 0
[  844.845143] dmfe: send_filter_frame() 0
[  845.844009] dmfe: dmfe_timer() 0
[  848.844007] dmfe: dmfe_timer() 0
[  848.844015] eth0: Tx timeout - resetting
[  848.844017] dmfe: Dynamic Reset device 1
[  848.844019] dmfe: dmfe_dynamic_reset() 0
[  848.844035] dmfe: dmfe_free_rxbuffer() 0
[  848.844054] dmfe: dmfe_init_dm910x() 0
[  848.844160] dmfe: dmfe_parse_srom()  0
[  848.845103] dmfe: dmfe_descriptor_init() 0
[  848.845131] dmfe: send_filter_frame() 0
[  849.844009] dmfe: dmfe_timer() 0
[  852.844008] dmfe: dmfe_timer() 0
[  852.844016] eth0: Tx timeout - resetting
[  852.844019] dmfe: Dynamic Reset device 1
[  852.844021] dmfe: dmfe_dynamic_reset() 0
[  852.844037] dmfe: dmfe_free_rxbuffer() 0
[  852.844060] dmfe: dmfe_init_dm910x() 0
[  852.844167] dmfe: dmfe_parse_srom()  0
[  852.845111] dmfe: dmfe_descriptor_init() 0
[  852.845143] dmfe: send_filter_frame() 0
[  853.844009] dmfe: dmfe_timer() 0
[  856.844008] dmfe: dmfe_timer() 0
[  856.844016] eth0: Tx timeout - resetting
[  856.844018] dmfe: Dynamic Reset device 1
[  856.844020] dmfe: dmfe_dynamic_reset() 0
[  856.844036] dmfe: dmfe_free_rxbuffer() 0
[  856.844055] dmfe: dmfe_init_dm910x() 0
[  856.844162] dmfe: dmfe_parse_srom()  0
[  856.845105] dmfe: dmfe_descriptor_init() 0
[  856.845134] dmfe: send_filter_frame() 0
[  857.844009] dmfe: dmfe_timer() 0
[  860.844008] dmfe: dmfe_timer() 0
[  860.844015] eth0: Tx timeout - resetting
[  860.844018] dmfe: Dynamic Reset device 1
[  860.844020] dmfe: dmfe_dynamic_reset() 0
[  860.844036] dmfe: dmfe_free_rxbuffer() 0
[  860.844057] dmfe: dmfe_init_dm910x() 0
[  860.844164] dmfe: dmfe_parse_srom()  0
[  860.845107] dmfe: dmfe_descriptor_init() 0
[  860.845137] dmfe: send_filter_frame() 0
[  861.844010] dmfe: dmfe_timer() 0
[  864.844008] dmfe: dmfe_timer() 0
[  864.844016] eth0: Tx timeout - resetting
[  864.844018] dmfe: Dynamic Reset device 1
[  864.844020] dmfe: dmfe_dynamic_reset() 0
[  864.844036] dmfe: dmfe_free_rxbuffer() 0
[  864.844055] dmfe: dmfe_init_dm910x() 0
[  864.844162] dmfe: dmfe_parse_srom()  0
[  864.845106] dmfe: dmfe_descriptor_init() 0
[  864.845134] dmfe: send_filter_frame() 0
[  865.844009] dmfe: dmfe_timer() 0
[  868.844013] dmfe: dmfe_timer() 0
[  868.844021] eth0: Tx timeout - resetting
[  868.844024] dmfe: Dynamic Reset device 1
[  868.844026] dmfe: dmfe_dynamic_reset() 0
[  868.844042] dmfe: dmfe_free_rxbuffer() 0
[  868.844064] dmfe: dmfe_init_dm910x() 0
[  868.844170] dmfe: dmfe_parse_srom()  0
[  868.845113] dmfe: dmfe_descriptor_init() 0
[  868.845143] dmfe: send_filter_frame() 0
[  869.844009] dmfe: dmfe_timer() 0
[  872.844009] dmfe: dmfe_timer() 0
[  872.844017] eth0: Tx timeout - resetting
[  872.844019] dmfe: Dynamic Reset device 1
[  872.844021] dmfe: dmfe_dynamic_reset() 0
[  872.844037] dmfe: dmfe_free_rxbuffer() 0
[  872.844057] dmfe: dmfe_init_dm910x() 0
[  872.844164] dmfe: dmfe_parse_srom()  0
[  872.845108] dmfe: dmfe_descriptor_init() 0
[  872.845137] dmfe: send_filter_frame() 0
[  873.844009] dmfe: dmfe_timer() 0
[  876.844009] dmfe: dmfe_timer() 0
[  876.844017] eth0: Tx timeout - resetting
[  876.844020] dmfe: Dynamic Reset device 1
[  876.844022] dmfe: dmfe_dynamic_reset() 0
[  876.844038] dmfe: dmfe_free_rxbuffer() 0
[  876.844058] dmfe: dmfe_init_dm910x() 0
[  876.844165] dmfe: dmfe_parse_srom()  0
[  876.845108] dmfe: dmfe_descriptor_init() 0
[  876.845138] dmfe: send_filter_frame() 0
[  877.844009] dmfe: dmfe_timer() 0
[  880.844008] dmfe: dmfe_timer() 0
[  880.844016] eth0: Tx timeout - resetting
[  880.844018] dmfe: Dynamic Reset device 1
[  880.844020] dmfe: dmfe_dynamic_reset() 0
[  880.844036] dmfe: dmfe_free_rxbuffer() 0
[  880.844056] dmfe: dmfe_init_dm910x() 0
[  880.844162] dmfe: dmfe_parse_srom()  0
[  880.845107] dmfe: dmfe_descriptor_init() 0
[  880.845135] dmfe: send_filter_frame() 0
[  881.844009] dmfe: dmfe_timer() 0
[  884.844008] dmfe: dmfe_timer() 0
[  884.844016] eth0: Tx timeout - resetting
[  884.844018] dmfe: Dynamic Reset device 1
[  884.844020] dmfe: dmfe_dynamic_reset() 0
[  884.844036] dmfe: dmfe_free_rxbuffer() 0
[  884.844056] dmfe: dmfe_init_dm910x() 0
[  884.844163] dmfe: dmfe_parse_srom()  0
[  884.845106] dmfe: dmfe_descriptor_init() 0
[  884.845135] dmfe: send_filter_frame() 0
[  885.844009] dmfe: dmfe_timer() 0
[  888.844008] dmfe: dmfe_timer() 0
[  888.844016] eth0: Tx timeout - resetting
[  888.844019] dmfe: Dynamic Reset device 1
[  888.844021] dmfe: dmfe_dynamic_reset() 0
[  888.844037] dmfe: dmfe_free_rxbuffer() 0
[  888.844056] dmfe: dmfe_init_dm910x() 0
[  888.844162] dmfe: dmfe_parse_srom()  0
[  888.845107] dmfe: dmfe_descriptor_init() 0
[  888.845135] dmfe: send_filter_frame() 0
[  889.844012] dmfe: dmfe_timer() 0
[  892.844014] dmfe: dmfe_timer() 0
[  892.844022] eth0: Tx timeout - resetting
[  892.844024] dmfe: Dynamic Reset device 1
[  892.844026] dmfe: dmfe_dynamic_reset() 0
[  892.844042] dmfe: dmfe_free_rxbuffer() 0
[  892.844062] dmfe: dmfe_init_dm910x() 0
[  892.844168] dmfe: dmfe_parse_srom()  0
[  892.845111] dmfe: dmfe_descriptor_init() 0
[  892.845142] dmfe: send_filter_frame() 0
[  893.844009] dmfe: dmfe_timer() 0
[  896.844022] dmfe: dmfe_timer() 0
[  896.844030] eth0: Tx timeout - resetting
[  896.844032] dmfe: Dynamic Reset device 1
[  896.844034] dmfe: dmfe_dynamic_reset() 0
[  896.844050] dmfe: dmfe_free_rxbuffer() 0
[  896.844070] dmfe: dmfe_init_dm910x() 0
[  896.844177] dmfe: dmfe_parse_srom()  0
[  896.845121] dmfe: dmfe_descriptor_init() 0
[  896.845150] dmfe: send_filter_frame() 0
[  897.844009] dmfe: dmfe_timer() 0
[  900.844008] dmfe: dmfe_timer() 0
[  900.844016] eth0: Tx timeout - resetting
[  900.844018] dmfe: Dynamic Reset device 1
[  900.844020] dmfe: dmfe_dynamic_reset() 0
[  900.844037] dmfe: dmfe_free_rxbuffer() 0
[  900.844057] dmfe: dmfe_init_dm910x() 0
[  900.844163] dmfe: dmfe_parse_srom()  0
[  900.845106] dmfe: dmfe_descriptor_init() 0
[  900.845135] dmfe: send_filter_frame() 0
[  901.844012] dmfe: dmfe_timer() 0
[  904.844013] dmfe: dmfe_timer() 0
[  904.844021] eth0: Tx timeout - resetting
[  904.844024] dmfe: Dynamic Reset device 1
[  904.844026] dmfe: dmfe_dynamic_reset() 0
[  904.844042] dmfe: dmfe_free_rxbuffer() 0
[  904.844061] dmfe: dmfe_init_dm910x() 0
[  904.844167] dmfe: dmfe_parse_srom()  0
[  904.845110] dmfe: dmfe_descriptor_init() 0
[  904.845138] dmfe: send_filter_frame() 0
[  905.844009] dmfe: dmfe_timer() 0
[  908.844007] dmfe: dmfe_timer() 0
[  908.844015] eth0: Tx timeout - resetting
[  908.844017] dmfe: Dynamic Reset device 1
[  908.844020] dmfe: dmfe_dynamic_reset() 0
[  908.844036] dmfe: dmfe_free_rxbuffer() 0
[  908.844057] dmfe: dmfe_init_dm910x() 0
[  908.844163] dmfe: dmfe_parse_srom()  0
[  908.845107] dmfe: dmfe_descriptor_init() 0
[  908.845138] dmfe: send_filter_frame() 0
[  909.844009] dmfe: dmfe_timer() 0
[  912.844008] dmfe: dmfe_timer() 0
[  912.844016] eth0: Tx timeout - resetting
[  912.844018] dmfe: Dynamic Reset device 1
[  912.844021] dmfe: dmfe_dynamic_reset() 0
[  912.844037] dmfe: dmfe_free_rxbuffer() 0
[  912.844057] dmfe: dmfe_init_dm910x() 0
[  912.844164] dmfe: dmfe_parse_srom()  0
[  912.845112] dmfe: dmfe_descriptor_init() 0
[  912.845140] dmfe: send_filter_frame() 0
[  913.844009] dmfe: dmfe_timer() 0
[  916.844013] dmfe: dmfe_timer() 0
[  916.844021] eth0: Tx timeout - resetting
[  916.844023] dmfe: Dynamic Reset device 1
[  916.844025] dmfe: dmfe_dynamic_reset() 0
[  916.844041] dmfe: dmfe_free_rxbuffer() 0
[  916.844063] dmfe: dmfe_init_dm910x() 0
[  916.844170] dmfe: dmfe_parse_srom()  0
[  916.845112] dmfe: dmfe_descriptor_init() 0
[  916.845142] dmfe: send_filter_frame() 0
[  917.844009] dmfe: dmfe_timer() 0
[  920.844008] dmfe: dmfe_timer() 0
[  920.844016] eth0: Tx timeout - resetting
[  920.844018] dmfe: Dynamic Reset device 1
[  920.844020] dmfe: dmfe_dynamic_reset() 0
[  920.844036] dmfe: dmfe_free_rxbuffer() 0
[  920.844055] dmfe: dmfe_init_dm910x() 0
[  920.844161] dmfe: dmfe_parse_srom()  0
[  920.845106] dmfe: dmfe_descriptor_init() 0
[  920.845134] dmfe: send_filter_frame() 0
[  921.844009] dmfe: dmfe_timer() 0
[  924.844008] dmfe: dmfe_timer() 0
[  924.844016] eth0: Tx timeout - resetting
[  924.844018] dmfe: Dynamic Reset device 1
[  924.844020] dmfe: dmfe_dynamic_reset() 0
[  924.844036] dmfe: dmfe_free_rxbuffer() 0
[  924.844058] dmfe: dmfe_init_dm910x() 0
[  924.844164] dmfe: dmfe_parse_srom()  0
[  924.845108] dmfe: dmfe_descriptor_init() 0
[  924.845139] dmfe: send_filter_frame() 0
[  925.844012] dmfe: dmfe_timer() 0
[  928.844012] dmfe: dmfe_timer() 0
[  928.844020] eth0: Tx timeout - resetting
[  928.844022] dmfe: Dynamic Reset device 1
[  928.844024] dmfe: dmfe_dynamic_reset() 0
[  928.844040] dmfe: dmfe_free_rxbuffer() 0
[  928.844060] dmfe: dmfe_init_dm910x() 0
[  928.844167] dmfe: dmfe_parse_srom()  0
[  928.845110] dmfe: dmfe_descriptor_init() 0
[  928.845138] dmfe: send_filter_frame() 0
[  929.844009] dmfe: dmfe_timer() 0
[  932.844009] dmfe: dmfe_timer() 0
[  932.844017] eth0: Tx timeout - resetting
[  932.844019] dmfe: Dynamic Reset device 1
[  932.844021] dmfe: dmfe_dynamic_reset() 0
[  932.844037] dmfe: dmfe_free_rxbuffer() 0
[  932.844059] dmfe: dmfe_init_dm910x() 0
[  932.844167] dmfe: dmfe_parse_srom()  0
[  932.845110] dmfe: dmfe_descriptor_init() 0
[  932.845141] dmfe: send_filter_frame() 0
[  933.844009] dmfe: dmfe_timer() 0
[  936.844010] dmfe: dmfe_timer() 0
[  936.844018] eth0: Tx timeout - resetting
[  936.844020] dmfe: Dynamic Reset device 1
[  936.844022] dmfe: dmfe_dynamic_reset() 0
[  936.844039] dmfe: dmfe_free_rxbuffer() 0
[  936.844058] dmfe: dmfe_init_dm910x() 0
[  936.844164] dmfe: dmfe_parse_srom()  0
[  936.845108] dmfe: dmfe_descriptor_init() 0
[  936.845135] dmfe: send_filter_frame() 0
[  937.844012] dmfe: dmfe_timer() 0
[  940.844007] dmfe: dmfe_timer() 0
[  940.844016] eth0: Tx timeout - resetting
[  940.844018] dmfe: Dynamic Reset device 1
[  940.844020] dmfe: dmfe_dynamic_reset() 0
[  940.844036] dmfe: dmfe_free_rxbuffer() 0
[  940.844058] dmfe: dmfe_init_dm910x() 0
[  940.844164] dmfe: dmfe_parse_srom()  0
[  940.845107] dmfe: dmfe_descriptor_init() 0
[  940.845137] dmfe: send_filter_frame() 0
[  941.844009] dmfe: dmfe_timer() 0
[  944.844008] dmfe: dmfe_timer() 0
[  944.844016] eth0: Tx timeout - resetting
[  944.844018] dmfe: Dynamic Reset device 1
[  944.844020] dmfe: dmfe_dynamic_reset() 0
[  944.844036] dmfe: dmfe_free_rxbuffer() 0
[  944.844056] dmfe: dmfe_init_dm910x() 0
[  944.844162] dmfe: dmfe_parse_srom()  0
[  944.845107] dmfe: dmfe_descriptor_init() 0
[  944.845135] dmfe: send_filter_frame() 0
[  945.844010] dmfe: dmfe_timer() 0
[  948.844008] dmfe: dmfe_timer() 0
[  948.844016] eth0: Tx timeout - resetting
[  948.844018] dmfe: Dynamic Reset device 1
[  948.844020] dmfe: dmfe_dynamic_reset() 0
[  948.844036] dmfe: dmfe_free_rxbuffer() 0
[  948.844058] dmfe: dmfe_init_dm910x() 0
[  948.844164] dmfe: dmfe_parse_srom()  0
[  948.845111] dmfe: dmfe_descriptor_init() 0
[  948.845141] dmfe: send_filter_frame() 0
[  949.844013] dmfe: dmfe_timer() 0
[  952.844013] dmfe: dmfe_timer() 0
[  952.844020] eth0: Tx timeout - resetting
[  952.844023] dmfe: Dynamic Reset device 1
[  952.844025] dmfe: dmfe_dynamic_reset() 0
[  952.844041] dmfe: dmfe_free_rxbuffer() 0
[  952.844060] dmfe: dmfe_init_dm910x() 0
[  952.844166] dmfe: dmfe_parse_srom()  0
[  952.845109] dmfe: dmfe_descriptor_init() 0
[  952.845137] dmfe: send_filter_frame() 0
[  953.844009] dmfe: dmfe_timer() 0
[  956.844022] dmfe: dmfe_timer() 0
[  956.844029] eth0: Tx timeout - resetting
[  956.844032] dmfe: Dynamic Reset device 1
[  956.844034] dmfe: dmfe_dynamic_reset() 0
[  956.844050] dmfe: dmfe_free_rxbuffer() 0
[  956.844073] dmfe: dmfe_init_dm910x() 0
[  956.844179] dmfe: dmfe_parse_srom()  0
[  956.845123] dmfe: dmfe_descriptor_init() 0
[  956.845155] dmfe: send_filter_frame() 0
[  957.844009] dmfe: dmfe_timer() 0
[  960.844008] dmfe: dmfe_timer() 0
[  960.844016] eth0: Tx timeout - resetting
[  960.844018] dmfe: Dynamic Reset device 1
[  960.844020] dmfe: dmfe_dynamic_reset() 0
[  960.844036] dmfe: dmfe_free_rxbuffer() 0
[  960.844056] dmfe: dmfe_init_dm910x() 0
[  960.844162] dmfe: dmfe_parse_srom()  0
[  960.845107] dmfe: dmfe_descriptor_init() 0
[  960.845135] dmfe: send_filter_frame() 0
[  961.844014] dmfe: dmfe_timer() 0
[  964.844010] dmfe: dmfe_timer() 0
[  964.844018] eth0: Tx timeout - resetting
[  964.844020] dmfe: Dynamic Reset device 1
[  964.844022] dmfe: dmfe_dynamic_reset() 0
[  964.844038] dmfe: dmfe_free_rxbuffer() 0
[  964.844059] dmfe: dmfe_init_dm910x() 0
[  964.844166] dmfe: dmfe_parse_srom()  0
[  964.845111] dmfe: dmfe_descriptor_init() 0
[  964.845141] dmfe: send_filter_frame() 0
[  965.844009] dmfe: dmfe_timer() 0
[  968.844009] dmfe: dmfe_timer() 0
[  968.844017] eth0: Tx timeout - resetting
[  968.844019] dmfe: Dynamic Reset device 1
[  968.844021] dmfe: dmfe_dynamic_reset() 0
[  968.844038] dmfe: dmfe_free_rxbuffer() 0
[  968.844057] dmfe: dmfe_init_dm910x() 0
[  968.844163] dmfe: dmfe_parse_srom()  0
[  968.845107] dmfe: dmfe_descriptor_init() 0
[  968.845135] dmfe: send_filter_frame() 0
[  969.844013] dmfe: dmfe_timer() 0
[  972.844008] dmfe: dmfe_timer() 0
[  972.844016] eth0: Tx timeout - resetting
[  972.844018] dmfe: Dynamic Reset device 1
[  972.844020] dmfe: dmfe_dynamic_reset() 0
[  972.844037] dmfe: dmfe_free_rxbuffer() 0
[  972.844058] dmfe: dmfe_init_dm910x() 0
[  972.844164] dmfe: dmfe_parse_srom()  0
[  972.845107] dmfe: dmfe_descriptor_init() 0
[  972.845137] dmfe: send_filter_frame() 0
[  973.844009] dmfe: dmfe_timer() 0
[  976.844008] dmfe: dmfe_timer() 0
[  976.844016] eth0: Tx timeout - resetting
[  976.844018] dmfe: Dynamic Reset device 1
[  976.844020] dmfe: dmfe_dynamic_reset() 0
[  976.844036] dmfe: dmfe_free_rxbuffer() 0
[  976.844056] dmfe: dmfe_init_dm910x() 0
[  976.844162] dmfe: dmfe_parse_srom()  0
[  976.845105] dmfe: dmfe_descriptor_init() 0
[  976.845133] dmfe: send_filter_frame() 0
[  977.844009] dmfe: dmfe_timer() 0
[  980.844008] dmfe: dmfe_timer() 0
[  980.844016] eth0: Tx timeout - resetting
[  980.844018] dmfe: Dynamic Reset device 1
[  980.844020] dmfe: dmfe_dynamic_reset() 0
[  980.844036] dmfe: dmfe_free_rxbuffer() 0
[  980.844057] dmfe: dmfe_init_dm910x() 0
[  980.844163] dmfe: dmfe_parse_srom()  0
[  980.845107] dmfe: dmfe_descriptor_init() 0
[  980.845137] dmfe: send_filter_frame() 0
[  981.844010] dmfe: dmfe_timer() 0
[  984.844008] dmfe: dmfe_timer() 0
[  984.844016] eth0: Tx timeout - resetting
[  984.844018] dmfe: Dynamic Reset device 1
[  984.844020] dmfe: dmfe_dynamic_reset() 0
[  984.844036] dmfe: dmfe_free_rxbuffer() 0
[  984.844055] dmfe: dmfe_init_dm910x() 0
[  984.844163] dmfe: dmfe_parse_srom()  0
[  984.845106] dmfe: dmfe_descriptor_init() 0
[  984.845134] dmfe: send_filter_frame() 0
[  985.844009] dmfe: dmfe_timer() 0
[  988.844008] dmfe: dmfe_timer() 0
[  988.844016] eth0: Tx timeout - resetting
[  988.844018] dmfe: Dynamic Reset device 1
[  988.844020] dmfe: dmfe_dynamic_reset() 0
[  988.844036] dmfe: dmfe_free_rxbuffer() 0
[  988.844057] dmfe: dmfe_init_dm910x() 0
[  988.844164] dmfe: dmfe_parse_srom()  0
[  988.845108] dmfe: dmfe_descriptor_init() 0
[  988.845138] dmfe: send_filter_frame() 0
[  989.844009] dmfe: dmfe_timer() 0
[  992.844009] dmfe: dmfe_timer() 0
[  992.844017] eth0: Tx timeout - resetting
[  992.844019] dmfe: Dynamic Reset device 1
[  992.844021] dmfe: dmfe_dynamic_reset() 0
[  992.844037] dmfe: dmfe_free_rxbuffer() 0
[  992.844057] dmfe: dmfe_init_dm910x() 0
[  992.844164] dmfe: dmfe_parse_srom()  0
[  992.845109] dmfe: dmfe_descriptor_init() 0
[  992.845138] dmfe: send_filter_frame() 0
[  993.844011] dmfe: dmfe_timer() 0
[  996.844009] dmfe: dmfe_timer() 0
[  996.844017] eth0: Tx timeout - resetting
[  996.844019] dmfe: Dynamic Reset device 1
[  996.844021] dmfe: dmfe_dynamic_reset() 0
[  996.844037] dmfe: dmfe_free_rxbuffer() 0
[  996.844059] dmfe: dmfe_init_dm910x() 0
[  996.844166] dmfe: dmfe_parse_srom()  0
[  996.845109] dmfe: dmfe_descriptor_init() 0
[  996.845139] dmfe: send_filter_frame() 0
[  997.844010] dmfe: dmfe_timer() 0
[ 1000.844008] dmfe: dmfe_timer() 0
[ 1000.844016] eth0: Tx timeout - resetting
[ 1000.844018] dmfe: Dynamic Reset device 1
[ 1000.844020] dmfe: dmfe_dynamic_reset() 0
[ 1000.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1000.844056] dmfe: dmfe_init_dm910x() 0
[ 1000.844163] dmfe: dmfe_parse_srom()  0
[ 1000.845106] dmfe: dmfe_descriptor_init() 0
[ 1000.845134] dmfe: send_filter_frame() 0
[ 1001.844009] dmfe: dmfe_timer() 0
[ 1004.844008] dmfe: dmfe_timer() 0
[ 1004.844016] eth0: Tx timeout - resetting
[ 1004.844018] dmfe: Dynamic Reset device 1
[ 1004.844020] dmfe: dmfe_dynamic_reset() 0
[ 1004.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1004.844058] dmfe: dmfe_init_dm910x() 0
[ 1004.844165] dmfe: dmfe_parse_srom()  0
[ 1004.845107] dmfe: dmfe_descriptor_init() 0
[ 1004.845138] dmfe: send_filter_frame() 0
[ 1005.844009] dmfe: dmfe_timer() 0
[ 1008.844008] dmfe: dmfe_timer() 0
[ 1008.844016] eth0: Tx timeout - resetting
[ 1008.844018] dmfe: Dynamic Reset device 1
[ 1008.844021] dmfe: dmfe_dynamic_reset() 0
[ 1008.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1008.844056] dmfe: dmfe_init_dm910x() 0
[ 1008.844163] dmfe: dmfe_parse_srom()  0
[ 1008.845108] dmfe: dmfe_descriptor_init() 0
[ 1008.845136] dmfe: send_filter_frame() 0
[ 1009.844009] dmfe: dmfe_timer() 0
[ 1012.844008] dmfe: dmfe_timer() 0
[ 1012.844016] eth0: Tx timeout - resetting
[ 1012.844018] dmfe: Dynamic Reset device 1
[ 1012.844020] dmfe: dmfe_dynamic_reset() 0
[ 1012.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1012.844060] dmfe: dmfe_init_dm910x() 0
[ 1012.844167] dmfe: dmfe_parse_srom()  0
[ 1012.845111] dmfe: dmfe_descriptor_init() 0
[ 1012.845141] dmfe: send_filter_frame() 0
[ 1013.844009] dmfe: dmfe_timer() 0
[ 1016.844022] dmfe: dmfe_timer() 0
[ 1016.844030] eth0: Tx timeout - resetting
[ 1016.844032] dmfe: Dynamic Reset device 1
[ 1016.844034] dmfe: dmfe_dynamic_reset() 0
[ 1016.844051] dmfe: dmfe_free_rxbuffer() 0
[ 1016.844071] dmfe: dmfe_init_dm910x() 0
[ 1016.844177] dmfe: dmfe_parse_srom()  0
[ 1016.845120] dmfe: dmfe_descriptor_init() 0
[ 1016.845149] dmfe: send_filter_frame() 0
[ 1017.844010] dmfe: dmfe_timer() 0
[ 1020.783053] dmfe: dmfe_get_stats 0
[ 1020.804475] dmfe: dmfe_get_stats 0
[ 1020.805020] dmfe: dmfe_get_stats 0
[ 1020.844024] dmfe: dmfe_timer() 0
[ 1020.844032] eth0: Tx timeout - resetting
[ 1020.844034] dmfe: Dynamic Reset device 1
[ 1020.844036] dmfe: dmfe_dynamic_reset() 0
[ 1020.844052] dmfe: dmfe_free_rxbuffer() 0
[ 1020.844077] dmfe: dmfe_init_dm910x() 0
[ 1020.844183] dmfe: dmfe_parse_srom()  0
[ 1020.845126] dmfe: dmfe_descriptor_init() 0
[ 1020.845158] dmfe: send_filter_frame() 0
[ 1021.805210] dmfe: dmfe_get_stats 0
[ 1021.844011] dmfe: dmfe_timer() 0
[ 1022.805119] dmfe: dmfe_get_stats 0
[ 1023.806785] dmfe: dmfe_get_stats 0
[ 1024.806799] dmfe: dmfe_get_stats 0
[ 1024.844012] dmfe: dmfe_timer() 0
[ 1024.844020] eth0: Tx timeout - resetting
[ 1024.844022] dmfe: Dynamic Reset device 1
[ 1024.844025] dmfe: dmfe_dynamic_reset() 0
[ 1024.844041] dmfe: dmfe_free_rxbuffer() 0
[ 1024.844060] dmfe: dmfe_init_dm910x() 0
[ 1024.844166] dmfe: dmfe_parse_srom()  0
[ 1024.845110] dmfe: dmfe_descriptor_init() 0
[ 1024.845139] dmfe: send_filter_frame() 0
[ 1025.806803] dmfe: dmfe_get_stats 0
[ 1025.844012] dmfe: dmfe_timer() 0
[ 1026.807180] dmfe: dmfe_get_stats 0
[ 1027.806927] dmfe: dmfe_get_stats 0
[ 1028.806045] dmfe: dmfe_get_stats 0
[ 1028.844008] dmfe: dmfe_timer() 0
[ 1028.844015] eth0: Tx timeout - resetting
[ 1028.844017] dmfe: Dynamic Reset device 1
[ 1028.844019] dmfe: dmfe_dynamic_reset() 0
[ 1028.844035] dmfe: dmfe_free_rxbuffer() 0
[ 1028.844056] dmfe: dmfe_init_dm910x() 0
[ 1028.844162] dmfe: dmfe_parse_srom()  0
[ 1028.845105] dmfe: dmfe_descriptor_init() 0
[ 1028.845135] dmfe: send_filter_frame() 0
[ 1029.805995] dmfe: dmfe_get_stats 0
[ 1029.844012] dmfe: dmfe_timer() 0
[ 1030.805713] dmfe: dmfe_get_stats 0
[ 1031.805402] dmfe: dmfe_get_stats 0
[ 1032.805074] dmfe: dmfe_get_stats 0
[ 1032.844018] dmfe: dmfe_timer() 0
[ 1032.844026] eth0: Tx timeout - resetting
[ 1032.844028] dmfe: Dynamic Reset device 1
[ 1032.844030] dmfe: dmfe_dynamic_reset() 0
[ 1032.844046] dmfe: dmfe_free_rxbuffer() 0
[ 1032.844068] dmfe: dmfe_init_dm910x() 0
[ 1032.844174] dmfe: dmfe_parse_srom()  0
[ 1032.845118] dmfe: dmfe_descriptor_init() 0
[ 1032.845147] dmfe: send_filter_frame() 0
[ 1033.805238] dmfe: dmfe_get_stats 0
[ 1033.844009] dmfe: dmfe_timer() 0
[ 1034.805100] dmfe: dmfe_get_stats 0
[ 1035.152899] dmfe: dmfe_get_stats 0
[ 1035.152930] dmfe: dmfe_get_stats 0
[ 1035.152952] dmfe: dmfe_get_stats 0
[ 1035.152974] dmfe: dmfe_get_stats 0
[ 1035.152996] dmfe: dmfe_get_stats 0
[ 1035.153017] dmfe: dmfe_get_stats 0
[ 1035.153039] dmfe: dmfe_get_stats 0
[ 1035.153069] dmfe: dmfe_get_stats 0
[ 1035.153366] dmfe: dmfe_get_stats 0
[ 1035.153387] dmfe: dmfe_get_stats 0
[ 1035.153406] dmfe: dmfe_get_stats 0
[ 1035.153425] dmfe: dmfe_get_stats 0
[ 1035.153444] dmfe: dmfe_get_stats 0
[ 1035.153463] dmfe: dmfe_get_stats 0
[ 1035.153482] dmfe: dmfe_get_stats 0
[ 1035.153501] dmfe: dmfe_get_stats 0
[ 1036.154605] dmfe: dmfe_get_stats 0
[ 1036.154632] dmfe: dmfe_get_stats 0
[ 1036.154653] dmfe: dmfe_get_stats 0
[ 1036.154672] dmfe: dmfe_get_stats 0
[ 1036.154692] dmfe: dmfe_get_stats 0
[ 1036.154711] dmfe: dmfe_get_stats 0
[ 1036.154730] dmfe: dmfe_get_stats 0
[ 1036.154761] dmfe: dmfe_get_stats 0
[ 1036.844008] dmfe: dmfe_timer() 0
[ 1036.844016] eth0: Tx timeout - resetting
[ 1036.844018] dmfe: Dynamic Reset device 1
[ 1036.844020] dmfe: dmfe_dynamic_reset() 0
[ 1036.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1036.844058] dmfe: dmfe_init_dm910x() 0
[ 1036.844165] dmfe: dmfe_parse_srom()  0
[ 1036.845108] dmfe: dmfe_descriptor_init() 0
[ 1036.845139] dmfe: send_filter_frame() 0
[ 1037.154120] dmfe: dmfe_get_stats 0
[ 1037.154148] dmfe: dmfe_get_stats 0
[ 1037.154168] dmfe: dmfe_get_stats 0
[ 1037.154187] dmfe: dmfe_get_stats 0
[ 1037.154207] dmfe: dmfe_get_stats 0
[ 1037.154226] dmfe: dmfe_get_stats 0
[ 1037.154245] dmfe: dmfe_get_stats 0
[ 1037.154276] dmfe: dmfe_get_stats 0
[ 1037.844009] dmfe: dmfe_timer() 0
[ 1040.844008] dmfe: dmfe_timer() 0
[ 1040.844016] eth0: Tx timeout - resetting
[ 1040.844018] dmfe: Dynamic Reset device 1
[ 1040.844020] dmfe: dmfe_dynamic_reset() 0
[ 1040.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1040.844058] dmfe: dmfe_init_dm910x() 0
[ 1040.844165] dmfe: dmfe_parse_srom()  0
[ 1040.845109] dmfe: dmfe_descriptor_init() 0
[ 1040.845137] dmfe: send_filter_frame() 0
[ 1041.844009] dmfe: dmfe_timer() 0
[ 1044.844007] dmfe: dmfe_timer() 0
[ 1044.844015] eth0: Tx timeout - resetting
[ 1044.844017] dmfe: Dynamic Reset device 1
[ 1044.844019] dmfe: dmfe_dynamic_reset() 0
[ 1044.844035] dmfe: dmfe_free_rxbuffer() 0
[ 1044.844058] dmfe: dmfe_init_dm910x() 0
[ 1044.844164] dmfe: dmfe_parse_srom()  0
[ 1044.845107] dmfe: dmfe_descriptor_init() 0
[ 1044.845136] dmfe: send_filter_frame() 0
[ 1045.844009] dmfe: dmfe_timer() 0
[ 1048.844009] dmfe: dmfe_timer() 0
[ 1048.844016] eth0: Tx timeout - resetting
[ 1048.844018] dmfe: Dynamic Reset device 1
[ 1048.844021] dmfe: dmfe_dynamic_reset() 0
[ 1048.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1048.844055] dmfe: dmfe_init_dm910x() 0
[ 1048.844162] dmfe: dmfe_parse_srom()  0
[ 1048.845105] dmfe: dmfe_descriptor_init() 0
[ 1048.845133] dmfe: send_filter_frame() 0
[ 1049.844010] dmfe: dmfe_timer() 0
[ 1052.844009] dmfe: dmfe_timer() 0
[ 1052.844017] eth0: Tx timeout - resetting
[ 1052.844019] dmfe: Dynamic Reset device 1
[ 1052.844021] dmfe: dmfe_dynamic_reset() 0
[ 1052.844038] dmfe: dmfe_free_rxbuffer() 0
[ 1052.844060] dmfe: dmfe_init_dm910x() 0
[ 1052.844167] dmfe: dmfe_parse_srom()  0
[ 1052.845111] dmfe: dmfe_descriptor_init() 0
[ 1052.845142] dmfe: send_filter_frame() 0
[ 1053.844010] dmfe: dmfe_timer() 0
[ 1056.844009] dmfe: dmfe_timer() 0
[ 1056.844017] eth0: Tx timeout - resetting
[ 1056.844019] dmfe: Dynamic Reset device 1
[ 1056.844021] dmfe: dmfe_dynamic_reset() 0
[ 1056.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1056.844058] dmfe: dmfe_init_dm910x() 0
[ 1056.844164] dmfe: dmfe_parse_srom()  0
[ 1056.845109] dmfe: dmfe_descriptor_init() 0
[ 1056.845137] dmfe: send_filter_frame() 0
[ 1057.844012] dmfe: dmfe_timer() 0
[ 1060.844014] dmfe: dmfe_timer() 0
[ 1060.844022] eth0: Tx timeout - resetting
[ 1060.844024] dmfe: Dynamic Reset device 1
[ 1060.844026] dmfe: dmfe_dynamic_reset() 0
[ 1060.844042] dmfe: dmfe_free_rxbuffer() 0
[ 1060.844064] dmfe: dmfe_init_dm910x() 0
[ 1060.844171] dmfe: dmfe_parse_srom()  0
[ 1060.845114] dmfe: dmfe_descriptor_init() 0
[ 1060.845144] dmfe: send_filter_frame() 0
[ 1061.844009] dmfe: dmfe_timer() 0
[ 1064.844007] dmfe: dmfe_timer() 0
[ 1064.844015] eth0: Tx timeout - resetting
[ 1064.844017] dmfe: Dynamic Reset device 1
[ 1064.844019] dmfe: dmfe_dynamic_reset() 0
[ 1064.844035] dmfe: dmfe_free_rxbuffer() 0
[ 1064.844055] dmfe: dmfe_init_dm910x() 0
[ 1064.844161] dmfe: dmfe_parse_srom()  0
[ 1064.845105] dmfe: dmfe_descriptor_init() 0
[ 1064.845133] dmfe: send_filter_frame() 0
[ 1065.844009] dmfe: dmfe_timer() 0
[ 1068.844007] dmfe: dmfe_timer() 0
[ 1068.844015] eth0: Tx timeout - resetting
[ 1068.844017] dmfe: Dynamic Reset device 1
[ 1068.844020] dmfe: dmfe_dynamic_reset() 0
[ 1068.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1068.844057] dmfe: dmfe_init_dm910x() 0
[ 1068.844164] dmfe: dmfe_parse_srom()  0
[ 1068.845107] dmfe: dmfe_descriptor_init() 0
[ 1068.845138] dmfe: send_filter_frame() 0
[ 1069.844038] dmfe: dmfe_timer() 0
[ 1072.844008] dmfe: dmfe_timer() 0
[ 1072.844016] eth0: Tx timeout - resetting
[ 1072.844018] dmfe: Dynamic Reset device 1
[ 1072.844021] dmfe: dmfe_dynamic_reset() 0
[ 1072.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1072.844058] dmfe: dmfe_init_dm910x() 0
[ 1072.844164] dmfe: dmfe_parse_srom()  0
[ 1072.845107] dmfe: dmfe_descriptor_init() 0
[ 1072.845135] dmfe: send_filter_frame() 0
[ 1073.844009] dmfe: dmfe_timer() 0
[ 1076.844019] dmfe: dmfe_timer() 0
[ 1076.844027] eth0: Tx timeout - resetting
[ 1076.844029] dmfe: Dynamic Reset device 1
[ 1076.844031] dmfe: dmfe_dynamic_reset() 0
[ 1076.844048] dmfe: dmfe_free_rxbuffer() 0
[ 1076.844069] dmfe: dmfe_init_dm910x() 0
[ 1076.844176] dmfe: dmfe_parse_srom()  0
[ 1076.845121] dmfe: dmfe_descriptor_init() 0
[ 1076.845151] dmfe: send_filter_frame() 0
[ 1077.844009] dmfe: dmfe_timer() 0
[ 1080.844008] dmfe: dmfe_timer() 0
[ 1080.844016] eth0: Tx timeout - resetting
[ 1080.844018] dmfe: Dynamic Reset device 1
[ 1080.844020] dmfe: dmfe_dynamic_reset() 0
[ 1080.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1080.844055] dmfe: dmfe_init_dm910x() 0
[ 1080.844162] dmfe: dmfe_parse_srom()  0
[ 1080.845105] dmfe: dmfe_descriptor_init() 0
[ 1080.845133] dmfe: send_filter_frame() 0
[ 1081.844011] dmfe: dmfe_timer() 0
[ 1084.844012] dmfe: dmfe_timer() 0
[ 1084.844020] eth0: Tx timeout - resetting
[ 1084.844023] dmfe: Dynamic Reset device 1
[ 1084.844025] dmfe: dmfe_dynamic_reset() 0
[ 1084.844041] dmfe: dmfe_free_rxbuffer() 0
[ 1084.844063] dmfe: dmfe_init_dm910x() 0
[ 1084.844169] dmfe: dmfe_parse_srom()  0
[ 1084.845113] dmfe: dmfe_descriptor_init() 0
[ 1084.845142] dmfe: send_filter_frame() 0
[ 1085.844009] dmfe: dmfe_timer() 0
[ 1088.844008] dmfe: dmfe_timer() 0
[ 1088.844016] eth0: Tx timeout - resetting
[ 1088.844018] dmfe: Dynamic Reset device 1
[ 1088.844020] dmfe: dmfe_dynamic_reset() 0
[ 1088.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1088.844056] dmfe: dmfe_init_dm910x() 0
[ 1088.844162] dmfe: dmfe_parse_srom()  0
[ 1088.845105] dmfe: dmfe_descriptor_init() 0
[ 1088.845133] dmfe: send_filter_frame() 0
[ 1089.844009] dmfe: dmfe_timer() 0
[ 1092.844011] dmfe: dmfe_timer() 0
[ 1092.844019] eth0: Tx timeout - resetting
[ 1092.844021] dmfe: Dynamic Reset device 1
[ 1092.844023] dmfe: dmfe_dynamic_reset() 0
[ 1092.844040] dmfe: dmfe_free_rxbuffer() 0
[ 1092.844062] dmfe: dmfe_init_dm910x() 0
[ 1092.844169] dmfe: dmfe_parse_srom()  0
[ 1092.845113] dmfe: dmfe_descriptor_init() 0
[ 1092.845145] dmfe: send_filter_frame() 0
[ 1093.844012] dmfe: dmfe_timer() 0
[ 1096.844007] dmfe: dmfe_timer() 0
[ 1096.844015] eth0: Tx timeout - resetting
[ 1096.844017] dmfe: Dynamic Reset device 1
[ 1096.844019] dmfe: dmfe_dynamic_reset() 0
[ 1096.844035] dmfe: dmfe_free_rxbuffer() 0
[ 1096.844056] dmfe: dmfe_init_dm910x() 0
[ 1096.844163] dmfe: dmfe_parse_srom()  0
[ 1096.845105] dmfe: dmfe_descriptor_init() 0
[ 1096.845133] dmfe: send_filter_frame() 0
[ 1097.844008] dmfe: dmfe_timer() 0
[ 1100.844008] dmfe: dmfe_timer() 0
[ 1100.844016] eth0: Tx timeout - resetting
[ 1100.844018] dmfe: Dynamic Reset device 1
[ 1100.844020] dmfe: dmfe_dynamic_reset() 0
[ 1100.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1100.844057] dmfe: dmfe_init_dm910x() 0
[ 1100.844164] dmfe: dmfe_parse_srom()  0
[ 1100.845107] dmfe: dmfe_descriptor_init() 0
[ 1100.845137] dmfe: send_filter_frame() 0
[ 1101.844010] dmfe: dmfe_timer() 0
[ 1104.844008] dmfe: dmfe_timer() 0
[ 1104.844016] eth0: Tx timeout - resetting
[ 1104.844018] dmfe: Dynamic Reset device 1
[ 1104.844020] dmfe: dmfe_dynamic_reset() 0
[ 1104.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1104.844055] dmfe: dmfe_init_dm910x() 0
[ 1104.844161] dmfe: dmfe_parse_srom()  0
[ 1104.845104] dmfe: dmfe_descriptor_init() 0
[ 1104.845133] dmfe: send_filter_frame() 0
[ 1105.844009] dmfe: dmfe_timer() 0
[ 1108.844013] dmfe: dmfe_timer() 0
[ 1108.844021] eth0: Tx timeout - resetting
[ 1108.844023] dmfe: Dynamic Reset device 1
[ 1108.844025] dmfe: dmfe_dynamic_reset() 0
[ 1108.844042] dmfe: dmfe_free_rxbuffer() 0
[ 1108.844065] dmfe: dmfe_init_dm910x() 0
[ 1108.844172] dmfe: dmfe_parse_srom()  0
[ 1108.845115] dmfe: dmfe_descriptor_init() 0
[ 1108.845144] dmfe: send_filter_frame() 0
[ 1109.844009] dmfe: dmfe_timer() 0
[ 1112.844008] dmfe: dmfe_timer() 0
[ 1112.844016] eth0: Tx timeout - resetting
[ 1112.844018] dmfe: Dynamic Reset device 1
[ 1112.844020] dmfe: dmfe_dynamic_reset() 0
[ 1112.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1112.844057] dmfe: dmfe_init_dm910x() 0
[ 1112.844164] dmfe: dmfe_parse_srom()  0
[ 1112.845108] dmfe: dmfe_descriptor_init() 0
[ 1112.845137] dmfe: send_filter_frame() 0
[ 1113.844009] dmfe: dmfe_timer() 0
[ 1116.844008] dmfe: dmfe_timer() 0
[ 1116.844016] eth0: Tx timeout - resetting
[ 1116.844018] dmfe: Dynamic Reset device 1
[ 1116.844021] dmfe: dmfe_dynamic_reset() 0
[ 1116.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1116.844059] dmfe: dmfe_init_dm910x() 0
[ 1116.844166] dmfe: dmfe_parse_srom()  0
[ 1116.845109] dmfe: dmfe_descriptor_init() 0
[ 1116.845138] dmfe: send_filter_frame() 0
[ 1117.844012] dmfe: dmfe_timer() 0
[ 1120.844010] dmfe: dmfe_timer() 0
[ 1120.844018] eth0: Tx timeout - resetting
[ 1120.844021] dmfe: Dynamic Reset device 1
[ 1120.844023] dmfe: dmfe_dynamic_reset() 0
[ 1120.844039] dmfe: dmfe_free_rxbuffer() 0
[ 1120.844059] dmfe: dmfe_init_dm910x() 0
[ 1120.844165] dmfe: dmfe_parse_srom()  0
[ 1120.845111] dmfe: dmfe_descriptor_init() 0
[ 1120.845139] dmfe: send_filter_frame() 0
[ 1121.844010] dmfe: dmfe_timer() 0
[ 1124.844008] dmfe: dmfe_timer() 0
[ 1124.844016] eth0: Tx timeout - resetting
[ 1124.844018] dmfe: Dynamic Reset device 1
[ 1124.844020] dmfe: dmfe_dynamic_reset() 0
[ 1124.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1124.844058] dmfe: dmfe_init_dm910x() 0
[ 1124.844165] dmfe: dmfe_parse_srom()  0
[ 1124.845107] dmfe: dmfe_descriptor_init() 0
[ 1124.845138] dmfe: send_filter_frame() 0
[ 1125.844010] dmfe: dmfe_timer() 0
[ 1128.844008] dmfe: dmfe_timer() 0
[ 1128.844016] eth0: Tx timeout - resetting
[ 1128.844018] dmfe: Dynamic Reset device 1
[ 1128.844020] dmfe: dmfe_dynamic_reset() 0
[ 1128.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1128.844056] dmfe: dmfe_init_dm910x() 0
[ 1128.844162] dmfe: dmfe_parse_srom()  0
[ 1128.845105] dmfe: dmfe_descriptor_init() 0
[ 1128.845134] dmfe: send_filter_frame() 0
[ 1129.844010] dmfe: dmfe_timer() 0
[ 1132.844008] dmfe: dmfe_timer() 0
[ 1132.844016] eth0: Tx timeout - resetting
[ 1132.844018] dmfe: Dynamic Reset device 1
[ 1132.844021] dmfe: dmfe_dynamic_reset() 0
[ 1132.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1132.844059] dmfe: dmfe_init_dm910x() 0
[ 1132.844165] dmfe: dmfe_parse_srom()  0
[ 1132.845109] dmfe: dmfe_descriptor_init() 0
[ 1132.845140] dmfe: send_filter_frame() 0
[ 1133.844009] dmfe: dmfe_timer() 0
[ 1136.844023] dmfe: dmfe_timer() 0
[ 1136.844030] eth0: Tx timeout - resetting
[ 1136.844032] dmfe: Dynamic Reset device 1
[ 1136.844035] dmfe: dmfe_dynamic_reset() 0
[ 1136.844051] dmfe: dmfe_free_rxbuffer() 0
[ 1136.844071] dmfe: dmfe_init_dm910x() 0
[ 1136.844178] dmfe: dmfe_parse_srom()  0
[ 1136.845121] dmfe: dmfe_descriptor_init() 0
[ 1136.845150] dmfe: send_filter_frame() 0
[ 1137.844009] dmfe: dmfe_timer() 0
[ 1140.844008] dmfe: dmfe_timer() 0
[ 1140.844016] eth0: Tx timeout - resetting
[ 1140.844018] dmfe: Dynamic Reset device 1
[ 1140.844020] dmfe: dmfe_dynamic_reset() 0
[ 1140.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1140.844058] dmfe: dmfe_init_dm910x() 0
[ 1140.844164] dmfe: dmfe_parse_srom()  0
[ 1140.845108] dmfe: dmfe_descriptor_init() 0
[ 1140.845138] dmfe: send_filter_frame() 0
[ 1141.844013] dmfe: dmfe_timer() 0
[ 1144.844014] dmfe: dmfe_timer() 0
[ 1144.844022] eth0: Tx timeout - resetting
[ 1144.844024] dmfe: Dynamic Reset device 1
[ 1144.844026] dmfe: dmfe_dynamic_reset() 0
[ 1144.844042] dmfe: dmfe_free_rxbuffer() 0
[ 1144.844062] dmfe: dmfe_init_dm910x() 0
[ 1144.844168] dmfe: dmfe_parse_srom()  0
[ 1144.845113] dmfe: dmfe_descriptor_init() 0
[ 1144.845141] dmfe: send_filter_frame() 0
[ 1145.844009] dmfe: dmfe_timer() 0
[ 1148.844008] dmfe: dmfe_timer() 0
[ 1148.844016] eth0: Tx timeout - resetting
[ 1148.844018] dmfe: Dynamic Reset device 1
[ 1148.844020] dmfe: dmfe_dynamic_reset() 0
[ 1148.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1148.844058] dmfe: dmfe_init_dm910x() 0
[ 1148.844165] dmfe: dmfe_parse_srom()  0
[ 1148.845107] dmfe: dmfe_descriptor_init() 0
[ 1148.845137] dmfe: send_filter_frame() 0
[ 1149.844010] dmfe: dmfe_timer() 0
[ 1152.844008] dmfe: dmfe_timer() 0
[ 1152.844016] eth0: Tx timeout - resetting
[ 1152.844018] dmfe: Dynamic Reset device 1
[ 1152.844021] dmfe: dmfe_dynamic_reset() 0
[ 1152.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1152.844057] dmfe: dmfe_init_dm910x() 0
[ 1152.844164] dmfe: dmfe_parse_srom()  0
[ 1152.845108] dmfe: dmfe_descriptor_init() 0
[ 1152.845137] dmfe: send_filter_frame() 0
[ 1153.844011] dmfe: dmfe_timer() 0
[ 1156.844008] dmfe: dmfe_timer() 0
[ 1156.844016] eth0: Tx timeout - resetting
[ 1156.844018] dmfe: Dynamic Reset device 1
[ 1156.844020] dmfe: dmfe_dynamic_reset() 0
[ 1156.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1156.844058] dmfe: dmfe_init_dm910x() 0
[ 1156.844164] dmfe: dmfe_parse_srom()  0
[ 1156.845107] dmfe: dmfe_descriptor_init() 0
[ 1156.845137] dmfe: send_filter_frame() 0
[ 1157.844009] dmfe: dmfe_timer() 0
[ 1160.844007] dmfe: dmfe_timer() 0
[ 1160.844015] eth0: Tx timeout - resetting
[ 1160.844018] dmfe: Dynamic Reset device 1
[ 1160.844020] dmfe: dmfe_dynamic_reset() 0
[ 1160.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1160.844055] dmfe: dmfe_init_dm910x() 0
[ 1160.844161] dmfe: dmfe_parse_srom()  0
[ 1160.845105] dmfe: dmfe_descriptor_init() 0
[ 1160.845134] dmfe: send_filter_frame() 0
[ 1161.844009] dmfe: dmfe_timer() 0
[ 1164.844008] dmfe: dmfe_timer() 0
[ 1164.844016] eth0: Tx timeout - resetting
[ 1164.844018] dmfe: Dynamic Reset device 1
[ 1164.844020] dmfe: dmfe_dynamic_reset() 0
[ 1164.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1164.844059] dmfe: dmfe_init_dm910x() 0
[ 1164.844166] dmfe: dmfe_parse_srom()  0
[ 1164.845109] dmfe: dmfe_descriptor_init() 0
[ 1164.845138] dmfe: send_filter_frame() 0
[ 1165.844010] dmfe: dmfe_timer() 0
[ 1168.844014] dmfe: dmfe_timer() 0
[ 1168.844022] eth0: Tx timeout - resetting
[ 1168.844024] dmfe: Dynamic Reset device 1
[ 1168.844026] dmfe: dmfe_dynamic_reset() 0
[ 1168.844042] dmfe: dmfe_free_rxbuffer() 0
[ 1168.844062] dmfe: dmfe_init_dm910x() 0
[ 1168.844168] dmfe: dmfe_parse_srom()  0
[ 1168.845111] dmfe: dmfe_descriptor_init() 0
[ 1168.845139] dmfe: send_filter_frame() 0
[ 1169.844009] dmfe: dmfe_timer() 0
[ 1172.844008] dmfe: dmfe_timer() 0
[ 1172.844016] eth0: Tx timeout - resetting
[ 1172.844019] dmfe: Dynamic Reset device 1
[ 1172.844021] dmfe: dmfe_dynamic_reset() 0
[ 1172.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1172.844059] dmfe: dmfe_init_dm910x() 0
[ 1172.844166] dmfe: dmfe_parse_srom()  0
[ 1172.845110] dmfe: dmfe_descriptor_init() 0
[ 1172.845141] dmfe: send_filter_frame() 0
[ 1173.844009] dmfe: dmfe_timer() 0
[ 1176.844008] dmfe: dmfe_timer() 0
[ 1176.844016] eth0: Tx timeout - resetting
[ 1176.844018] dmfe: Dynamic Reset device 1
[ 1176.844021] dmfe: dmfe_dynamic_reset() 0
[ 1176.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1176.844058] dmfe: dmfe_init_dm910x() 0
[ 1176.844164] dmfe: dmfe_parse_srom()  0
[ 1176.845107] dmfe: dmfe_descriptor_init() 0
[ 1176.845134] dmfe: send_filter_frame() 0
[ 1177.844012] dmfe: dmfe_timer() 0
[ 1180.844013] dmfe: dmfe_timer() 0
[ 1180.844022] eth0: Tx timeout - resetting
[ 1180.844024] dmfe: Dynamic Reset device 1
[ 1180.844026] dmfe: dmfe_dynamic_reset() 0
[ 1180.844042] dmfe: dmfe_free_rxbuffer() 0
[ 1180.844064] dmfe: dmfe_init_dm910x() 0
[ 1180.844171] dmfe: dmfe_parse_srom()  0
[ 1180.845116] dmfe: dmfe_descriptor_init() 0
[ 1180.845145] dmfe: send_filter_frame() 0
[ 1181.844010] dmfe: dmfe_timer() 0
[ 1184.844008] dmfe: dmfe_timer() 0
[ 1184.844016] eth0: Tx timeout - resetting
[ 1184.844018] dmfe: Dynamic Reset device 1
[ 1184.844020] dmfe: dmfe_dynamic_reset() 0
[ 1184.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1184.844055] dmfe: dmfe_init_dm910x() 0
[ 1184.844161] dmfe: dmfe_parse_srom()  0
[ 1184.845105] dmfe: dmfe_descriptor_init() 0
[ 1184.845133] dmfe: send_filter_frame() 0
[ 1185.844012] dmfe: dmfe_timer() 0
[ 1188.844008] dmfe: dmfe_timer() 0
[ 1188.844016] eth0: Tx timeout - resetting
[ 1188.844018] dmfe: Dynamic Reset device 1
[ 1188.844020] dmfe: dmfe_dynamic_reset() 0
[ 1188.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1188.844059] dmfe: dmfe_init_dm910x() 0
[ 1188.844165] dmfe: dmfe_parse_srom()  0
[ 1188.845110] dmfe: dmfe_descriptor_init() 0
[ 1188.845140] dmfe: send_filter_frame() 0
[ 1189.844009] dmfe: dmfe_timer() 0
[ 1192.844013] dmfe: dmfe_timer() 0
[ 1192.844021] eth0: Tx timeout - resetting
[ 1192.844023] dmfe: Dynamic Reset device 1
[ 1192.844025] dmfe: dmfe_dynamic_reset() 0
[ 1192.844042] dmfe: dmfe_free_rxbuffer() 0
[ 1192.844063] dmfe: dmfe_init_dm910x() 0
[ 1192.844169] dmfe: dmfe_parse_srom()  0
[ 1192.845114] dmfe: dmfe_descriptor_init() 0
[ 1192.845142] dmfe: send_filter_frame() 0
[ 1193.844009] dmfe: dmfe_timer() 0
[ 1196.844020] dmfe: dmfe_timer() 0
[ 1196.844029] eth0: Tx timeout - resetting
[ 1196.844031] dmfe: Dynamic Reset device 1
[ 1196.844033] dmfe: dmfe_dynamic_reset() 0
[ 1196.844049] dmfe: dmfe_free_rxbuffer() 0
[ 1196.844070] dmfe: dmfe_init_dm910x() 0
[ 1196.844178] dmfe: dmfe_parse_srom()  0
[ 1196.845122] dmfe: dmfe_descriptor_init() 0
[ 1196.845152] dmfe: send_filter_frame() 0
[ 1197.844009] dmfe: dmfe_timer() 0
[ 1200.844008] dmfe: dmfe_timer() 0
[ 1200.844016] eth0: Tx timeout - resetting
[ 1200.844018] dmfe: Dynamic Reset device 1
[ 1200.844020] dmfe: dmfe_dynamic_reset() 0
[ 1200.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1200.844055] dmfe: dmfe_init_dm910x() 0
[ 1200.844162] dmfe: dmfe_parse_srom()  0
[ 1200.845104] dmfe: dmfe_descriptor_init() 0
[ 1200.845133] dmfe: send_filter_frame() 0
[ 1201.844012] dmfe: dmfe_timer() 0
[ 1204.844013] dmfe: dmfe_timer() 0
[ 1204.844021] eth0: Tx timeout - resetting
[ 1204.844023] dmfe: Dynamic Reset device 1
[ 1204.844025] dmfe: dmfe_dynamic_reset() 0
[ 1204.844041] dmfe: dmfe_free_rxbuffer() 0
[ 1204.844063] dmfe: dmfe_init_dm910x() 0
[ 1204.844170] dmfe: dmfe_parse_srom()  0
[ 1204.845113] dmfe: dmfe_descriptor_init() 0
[ 1204.845143] dmfe: send_filter_frame() 0
[ 1205.844010] dmfe: dmfe_timer() 0
[ 1208.844008] dmfe: dmfe_timer() 0
[ 1208.844015] eth0: Tx timeout - resetting
[ 1208.844017] dmfe: Dynamic Reset device 1
[ 1208.844019] dmfe: dmfe_dynamic_reset() 0
[ 1208.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1208.844055] dmfe: dmfe_init_dm910x() 0
[ 1208.844161] dmfe: dmfe_parse_srom()  0
[ 1208.845104] dmfe: dmfe_descriptor_init() 0
[ 1208.845133] dmfe: send_filter_frame() 0
[ 1209.844010] dmfe: dmfe_timer() 0
[ 1212.844009] dmfe: dmfe_timer() 0
[ 1212.844017] eth0: Tx timeout - resetting
[ 1212.844019] dmfe: Dynamic Reset device 1
[ 1212.844021] dmfe: dmfe_dynamic_reset() 0
[ 1212.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1212.844058] dmfe: dmfe_init_dm910x() 0
[ 1212.844165] dmfe: dmfe_parse_srom()  0
[ 1212.845112] dmfe: dmfe_descriptor_init() 0
[ 1212.845142] dmfe: send_filter_frame() 0
[ 1213.844012] dmfe: dmfe_timer() 0
[ 1216.844018] dmfe: dmfe_timer() 0
[ 1216.844026] eth0: Tx timeout - resetting
[ 1216.844028] dmfe: Dynamic Reset device 1
[ 1216.844030] dmfe: dmfe_dynamic_reset() 0
[ 1216.844047] dmfe: dmfe_free_rxbuffer() 0
[ 1216.844066] dmfe: dmfe_init_dm910x() 0
[ 1216.844172] dmfe: dmfe_parse_srom()  0
[ 1216.845116] dmfe: dmfe_descriptor_init() 0
[ 1216.845144] dmfe: send_filter_frame() 0
[ 1217.844011] dmfe: dmfe_timer() 0
[ 1220.350439] dmfe: dmfe_get_stats 0
[ 1220.524296] dmfe: dmfe_get_stats 0
[ 1220.691427] dmfe: dmfe_get_stats 0
[ 1220.844017] dmfe: dmfe_timer() 0
[ 1220.844025] eth0: Tx timeout - resetting
[ 1220.844027] dmfe: Dynamic Reset device 1
[ 1220.844030] dmfe: dmfe_dynamic_reset() 0
[ 1220.844046] dmfe: dmfe_free_rxbuffer() 0
[ 1220.844070] dmfe: dmfe_init_dm910x() 0
[ 1220.844177] dmfe: dmfe_parse_srom()  0
[ 1220.845121] dmfe: dmfe_descriptor_init() 0
[ 1220.845151] dmfe: send_filter_frame() 0
[ 1221.844009] dmfe: dmfe_timer() 0
[ 1224.844008] dmfe: dmfe_timer() 0
[ 1224.844016] eth0: Tx timeout - resetting
[ 1224.844018] dmfe: Dynamic Reset device 1
[ 1224.844020] dmfe: dmfe_dynamic_reset() 0
[ 1224.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1224.844057] dmfe: dmfe_init_dm910x() 0
[ 1224.844163] dmfe: dmfe_parse_srom()  0
[ 1224.845106] dmfe: dmfe_descriptor_init() 0
[ 1224.845134] dmfe: send_filter_frame() 0
[ 1225.844009] dmfe: dmfe_timer() 0
[ 1228.844008] dmfe: dmfe_timer() 0
[ 1228.844016] eth0: Tx timeout - resetting
[ 1228.844018] dmfe: Dynamic Reset device 1
[ 1228.844020] dmfe: dmfe_dynamic_reset() 0
[ 1228.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1228.844056] dmfe: dmfe_init_dm910x() 0
[ 1228.844162] dmfe: dmfe_parse_srom()  0
[ 1228.845105] dmfe: dmfe_descriptor_init() 0
[ 1228.845133] dmfe: send_filter_frame() 0
[ 1229.844009] dmfe: dmfe_timer() 0
[ 1232.844011] dmfe: dmfe_timer() 0
[ 1232.844019] eth0: Tx timeout - resetting
[ 1232.844021] dmfe: Dynamic Reset device 1
[ 1232.844023] dmfe: dmfe_dynamic_reset() 0
[ 1232.844039] dmfe: dmfe_free_rxbuffer() 0
[ 1232.844060] dmfe: dmfe_init_dm910x() 0
[ 1232.844166] dmfe: dmfe_parse_srom()  0
[ 1232.845111] dmfe: dmfe_descriptor_init() 0
[ 1232.845140] dmfe: send_filter_frame() 0
[ 1233.844009] dmfe: dmfe_timer() 0
[ 1236.844012] dmfe: dmfe_timer() 0
[ 1236.844019] eth0: Tx timeout - resetting
[ 1236.844022] dmfe: Dynamic Reset device 1
[ 1236.844024] dmfe: dmfe_dynamic_reset() 0
[ 1236.844041] dmfe: dmfe_free_rxbuffer() 0
[ 1236.844065] dmfe: dmfe_init_dm910x() 0
[ 1236.844171] dmfe: dmfe_parse_srom()  0
[ 1236.845114] dmfe: dmfe_descriptor_init() 0
[ 1236.845142] dmfe: send_filter_frame() 0
[ 1237.844015] dmfe: dmfe_timer() 0
[ 1240.844011] dmfe: dmfe_timer() 0
[ 1240.844019] eth0: Tx timeout - resetting
[ 1240.844021] dmfe: Dynamic Reset device 1
[ 1240.844023] dmfe: dmfe_dynamic_reset() 0
[ 1240.844039] dmfe: dmfe_free_rxbuffer() 0
[ 1240.844061] dmfe: dmfe_init_dm910x() 0
[ 1240.844167] dmfe: dmfe_parse_srom()  0
[ 1240.845111] dmfe: dmfe_descriptor_init() 0
[ 1240.845139] dmfe: send_filter_frame() 0
[ 1241.844011] dmfe: dmfe_timer() 0
[ 1244.844011] dmfe: dmfe_timer() 0
[ 1244.844019] eth0: Tx timeout - resetting
[ 1244.844021] dmfe: Dynamic Reset device 1
[ 1244.844023] dmfe: dmfe_dynamic_reset() 0
[ 1244.844039] dmfe: dmfe_free_rxbuffer() 0
[ 1244.844062] dmfe: dmfe_init_dm910x() 0
[ 1244.844168] dmfe: dmfe_parse_srom()  0
[ 1244.845112] dmfe: dmfe_descriptor_init() 0
[ 1244.845143] dmfe: send_filter_frame() 0
[ 1245.844016] dmfe: dmfe_timer() 0
[ 1248.844011] dmfe: dmfe_timer() 0
[ 1248.844020] eth0: Tx timeout - resetting
[ 1248.844022] dmfe: Dynamic Reset device 1
[ 1248.844024] dmfe: dmfe_dynamic_reset() 0
[ 1248.844040] dmfe: dmfe_free_rxbuffer() 0
[ 1248.844067] dmfe: dmfe_init_dm910x() 0
[ 1248.844173] dmfe: dmfe_parse_srom()  0
[ 1248.845116] dmfe: dmfe_descriptor_init() 0
[ 1248.845145] dmfe: send_filter_frame() 0
[ 1249.844008] dmfe: dmfe_timer() 0
[ 1252.844008] dmfe: dmfe_timer() 0
[ 1252.844015] eth0: Tx timeout - resetting
[ 1252.844018] dmfe: Dynamic Reset device 1
[ 1252.844020] dmfe: dmfe_dynamic_reset() 0
[ 1252.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1252.844056] dmfe: dmfe_init_dm910x() 0
[ 1252.844163] dmfe: dmfe_parse_srom()  0
[ 1252.845108] dmfe: dmfe_descriptor_init() 0
[ 1252.845138] dmfe: send_filter_frame() 0
[ 1253.844009] dmfe: dmfe_timer() 0
[ 1256.844021] dmfe: dmfe_timer() 0
[ 1256.844029] eth0: Tx timeout - resetting
[ 1256.844031] dmfe: Dynamic Reset device 1
[ 1256.844033] dmfe: dmfe_dynamic_reset() 0
[ 1256.844049] dmfe: dmfe_free_rxbuffer() 0
[ 1256.844070] dmfe: dmfe_init_dm910x() 0
[ 1256.844176] dmfe: dmfe_parse_srom()  0
[ 1256.845119] dmfe: dmfe_descriptor_init() 0
[ 1256.845149] dmfe: send_filter_frame() 0
[ 1257.844010] dmfe: dmfe_timer() 0
[ 1260.844008] dmfe: dmfe_timer() 0
[ 1260.844016] eth0: Tx timeout - resetting
[ 1260.844018] dmfe: Dynamic Reset device 1
[ 1260.844020] dmfe: dmfe_dynamic_reset() 0
[ 1260.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1260.844056] dmfe: dmfe_init_dm910x() 0
[ 1260.844163] dmfe: dmfe_parse_srom()  0
[ 1260.845106] dmfe: dmfe_descriptor_init() 0
[ 1260.845135] dmfe: send_filter_frame() 0
[ 1261.844009] dmfe: dmfe_timer() 0
[ 1264.844008] dmfe: dmfe_timer() 0
[ 1264.844016] eth0: Tx timeout - resetting
[ 1264.844018] dmfe: Dynamic Reset device 1
[ 1264.844020] dmfe: dmfe_dynamic_reset() 0
[ 1264.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1264.844056] dmfe: dmfe_init_dm910x() 0
[ 1264.844163] dmfe: dmfe_parse_srom()  0
[ 1264.845105] dmfe: dmfe_descriptor_init() 0
[ 1264.845134] dmfe: send_filter_frame() 0
[ 1265.844009] dmfe: dmfe_timer() 0
[ 1268.844009] dmfe: dmfe_timer() 0
[ 1268.844017] eth0: Tx timeout - resetting
[ 1268.844019] dmfe: Dynamic Reset device 1
[ 1268.844021] dmfe: dmfe_dynamic_reset() 0
[ 1268.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1268.844057] dmfe: dmfe_init_dm910x() 0
[ 1268.844164] dmfe: dmfe_parse_srom()  0
[ 1268.845107] dmfe: dmfe_descriptor_init() 0
[ 1268.845135] dmfe: send_filter_frame() 0
[ 1269.844012] dmfe: dmfe_timer() 0
[ 1272.844011] dmfe: dmfe_timer() 0
[ 1272.844019] eth0: Tx timeout - resetting
[ 1272.844021] dmfe: Dynamic Reset device 1
[ 1272.844024] dmfe: dmfe_dynamic_reset() 0
[ 1272.844040] dmfe: dmfe_free_rxbuffer() 0
[ 1272.844060] dmfe: dmfe_init_dm910x() 0
[ 1272.844166] dmfe: dmfe_parse_srom()  0
[ 1272.845110] dmfe: dmfe_descriptor_init() 0
[ 1272.845138] dmfe: send_filter_frame() 0
[ 1273.844010] dmfe: dmfe_timer() 0
[ 1276.844008] dmfe: dmfe_timer() 0
[ 1276.844016] eth0: Tx timeout - resetting
[ 1276.844018] dmfe: Dynamic Reset device 1
[ 1276.844020] dmfe: dmfe_dynamic_reset() 0
[ 1276.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1276.844057] dmfe: dmfe_init_dm910x() 0
[ 1276.844163] dmfe: dmfe_parse_srom()  0
[ 1276.845106] dmfe: dmfe_descriptor_init() 0
[ 1276.845135] dmfe: send_filter_frame() 0
[ 1277.844010] dmfe: dmfe_timer() 0
[ 1280.844008] dmfe: dmfe_timer() 0
[ 1280.844016] eth0: Tx timeout - resetting
[ 1280.844018] dmfe: Dynamic Reset device 1
[ 1280.844020] dmfe: dmfe_dynamic_reset() 0
[ 1280.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1280.844057] dmfe: dmfe_init_dm910x() 0
[ 1280.844163] dmfe: dmfe_parse_srom()  0
[ 1280.845106] dmfe: dmfe_descriptor_init() 0
[ 1280.845135] dmfe: send_filter_frame() 0
[ 1281.844009] dmfe: dmfe_timer() 0
[ 1284.844008] dmfe: dmfe_timer() 0
[ 1284.844016] eth0: Tx timeout - resetting
[ 1284.844018] dmfe: Dynamic Reset device 1
[ 1284.844020] dmfe: dmfe_dynamic_reset() 0
[ 1284.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1284.844057] dmfe: dmfe_init_dm910x() 0
[ 1284.844163] dmfe: dmfe_parse_srom()  0
[ 1284.845106] dmfe: dmfe_descriptor_init() 0
[ 1284.845134] dmfe: send_filter_frame() 0
[ 1285.844009] dmfe: dmfe_timer() 0
[ 1288.844008] dmfe: dmfe_timer() 0
[ 1288.844016] eth0: Tx timeout - resetting
[ 1288.844018] dmfe: Dynamic Reset device 1
[ 1288.844020] dmfe: dmfe_dynamic_reset() 0
[ 1288.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1288.844056] dmfe: dmfe_init_dm910x() 0
[ 1288.844162] dmfe: dmfe_parse_srom()  0
[ 1288.845107] dmfe: dmfe_descriptor_init() 0
[ 1288.845136] dmfe: send_filter_frame() 0
[ 1289.844009] dmfe: dmfe_timer() 0
[ 1292.844008] dmfe: dmfe_timer() 0
[ 1292.844016] eth0: Tx timeout - resetting
[ 1292.844018] dmfe: Dynamic Reset device 1
[ 1292.844020] dmfe: dmfe_dynamic_reset() 0
[ 1292.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1292.844057] dmfe: dmfe_init_dm910x() 0
[ 1292.844164] dmfe: dmfe_parse_srom()  0
[ 1292.845108] dmfe: dmfe_descriptor_init() 0
[ 1292.845137] dmfe: send_filter_frame() 0
[ 1293.844009] dmfe: dmfe_timer() 0
[ 1296.844011] dmfe: dmfe_timer() 0
[ 1296.844019] eth0: Tx timeout - resetting
[ 1296.844021] dmfe: Dynamic Reset device 1
[ 1296.844024] dmfe: dmfe_dynamic_reset() 0
[ 1296.844040] dmfe: dmfe_free_rxbuffer() 0
[ 1296.844060] dmfe: dmfe_init_dm910x() 0
[ 1296.844166] dmfe: dmfe_parse_srom()  0
[ 1296.845109] dmfe: dmfe_descriptor_init() 0
[ 1296.845138] dmfe: send_filter_frame() 0
[ 1297.844009] dmfe: dmfe_timer() 0
[ 1300.844008] dmfe: dmfe_timer() 0
[ 1300.844016] eth0: Tx timeout - resetting
[ 1300.844018] dmfe: Dynamic Reset device 1
[ 1300.844020] dmfe: dmfe_dynamic_reset() 0
[ 1300.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1300.844057] dmfe: dmfe_init_dm910x() 0
[ 1300.844164] dmfe: dmfe_parse_srom()  0
[ 1300.845109] dmfe: dmfe_descriptor_init() 0
[ 1300.845138] dmfe: send_filter_frame() 0
[ 1301.844009] dmfe: dmfe_timer() 0
[ 1304.844008] dmfe: dmfe_timer() 0
[ 1304.844016] eth0: Tx timeout - resetting
[ 1304.844018] dmfe: Dynamic Reset device 1
[ 1304.844020] dmfe: dmfe_dynamic_reset() 0
[ 1304.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1304.844055] dmfe: dmfe_init_dm910x() 0
[ 1304.844161] dmfe: dmfe_parse_srom()  0
[ 1304.845104] dmfe: dmfe_descriptor_init() 0
[ 1304.845133] dmfe: send_filter_frame() 0
[ 1305.844038] dmfe: dmfe_timer() 0
[ 1308.844010] dmfe: dmfe_timer() 0
[ 1308.844018] eth0: Tx timeout - resetting
[ 1308.844020] dmfe: Dynamic Reset device 1
[ 1308.844022] dmfe: dmfe_dynamic_reset() 0
[ 1308.844039] dmfe: dmfe_free_rxbuffer() 0
[ 1308.844059] dmfe: dmfe_init_dm910x() 0
[ 1308.844165] dmfe: dmfe_parse_srom()  0
[ 1308.845109] dmfe: dmfe_descriptor_init() 0
[ 1308.845138] dmfe: send_filter_frame() 0
[ 1309.844010] dmfe: dmfe_timer() 0
[ 1312.844008] dmfe: dmfe_timer() 0
[ 1312.844016] eth0: Tx timeout - resetting
[ 1312.844018] dmfe: Dynamic Reset device 1
[ 1312.844020] dmfe: dmfe_dynamic_reset() 0
[ 1312.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1312.844057] dmfe: dmfe_init_dm910x() 0
[ 1312.844164] dmfe: dmfe_parse_srom()  0
[ 1312.845108] dmfe: dmfe_descriptor_init() 0
[ 1312.845137] dmfe: send_filter_frame() 0
[ 1313.844009] dmfe: dmfe_timer() 0
[ 1316.844021] dmfe: dmfe_timer() 0
[ 1316.844029] eth0: Tx timeout - resetting
[ 1316.844031] dmfe: Dynamic Reset device 1
[ 1316.844033] dmfe: dmfe_dynamic_reset() 0
[ 1316.844049] dmfe: dmfe_free_rxbuffer() 0
[ 1316.844069] dmfe: dmfe_init_dm910x() 0
[ 1316.844176] dmfe: dmfe_parse_srom()  0
[ 1316.845120] dmfe: dmfe_descriptor_init() 0
[ 1316.845148] dmfe: send_filter_frame() 0
[ 1317.844009] dmfe: dmfe_timer() 0
[ 1320.844008] dmfe: dmfe_timer() 0
[ 1320.844016] eth0: Tx timeout - resetting
[ 1320.844018] dmfe: Dynamic Reset device 1
[ 1320.844020] dmfe: dmfe_dynamic_reset() 0
[ 1320.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1320.844056] dmfe: dmfe_init_dm910x() 0
[ 1320.844162] dmfe: dmfe_parse_srom()  0
[ 1320.845107] dmfe: dmfe_descriptor_init() 0
[ 1320.845136] dmfe: send_filter_frame() 0
[ 1321.844009] dmfe: dmfe_timer() 0
[ 1324.844008] dmfe: dmfe_timer() 0
[ 1324.844016] eth0: Tx timeout - resetting
[ 1324.844018] dmfe: Dynamic Reset device 1
[ 1324.844020] dmfe: dmfe_dynamic_reset() 0
[ 1324.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1324.844056] dmfe: dmfe_init_dm910x() 0
[ 1324.844163] dmfe: dmfe_parse_srom()  0
[ 1324.845106] dmfe: dmfe_descriptor_init() 0
[ 1324.845134] dmfe: send_filter_frame() 0
[ 1325.844009] dmfe: dmfe_timer() 0
[ 1328.844008] dmfe: dmfe_timer() 0
[ 1328.844016] eth0: Tx timeout - resetting
[ 1328.844018] dmfe: Dynamic Reset device 1
[ 1328.844021] dmfe: dmfe_dynamic_reset() 0
[ 1328.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1328.844056] dmfe: dmfe_init_dm910x() 0
[ 1328.844163] dmfe: dmfe_parse_srom()  0
[ 1328.845105] dmfe: dmfe_descriptor_init() 0
[ 1328.845134] dmfe: send_filter_frame() 0
[ 1329.844012] dmfe: dmfe_timer() 0
[ 1332.844013] dmfe: dmfe_timer() 0
[ 1332.844021] eth0: Tx timeout - resetting
[ 1332.844023] dmfe: Dynamic Reset device 1
[ 1332.844025] dmfe: dmfe_dynamic_reset() 0
[ 1332.844042] dmfe: dmfe_free_rxbuffer() 0
[ 1332.844063] dmfe: dmfe_init_dm910x() 0
[ 1332.844170] dmfe: dmfe_parse_srom()  0
[ 1332.845112] dmfe: dmfe_descriptor_init() 0
[ 1332.845141] dmfe: send_filter_frame() 0
[ 1333.844009] dmfe: dmfe_timer() 0
[ 1336.844008] dmfe: dmfe_timer() 0
[ 1336.844016] eth0: Tx timeout - resetting
[ 1336.844018] dmfe: Dynamic Reset device 1
[ 1336.844020] dmfe: dmfe_dynamic_reset() 0
[ 1336.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1336.844057] dmfe: dmfe_init_dm910x() 0
[ 1336.844163] dmfe: dmfe_parse_srom()  0
[ 1336.845107] dmfe: dmfe_descriptor_init() 0
[ 1336.845135] dmfe: send_filter_frame() 0
[ 1337.844009] dmfe: dmfe_timer() 0
[ 1340.844009] dmfe: dmfe_timer() 0
[ 1340.844017] eth0: Tx timeout - resetting
[ 1340.844019] dmfe: Dynamic Reset device 1
[ 1340.844021] dmfe: dmfe_dynamic_reset() 0
[ 1340.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1340.844057] dmfe: dmfe_init_dm910x() 0
[ 1340.844163] dmfe: dmfe_parse_srom()  0
[ 1340.845106] dmfe: dmfe_descriptor_init() 0
[ 1340.845135] dmfe: send_filter_frame() 0
[ 1341.844013] dmfe: dmfe_timer() 0
[ 1344.844007] dmfe: dmfe_timer() 0
[ 1344.844015] eth0: Tx timeout - resetting
[ 1344.844018] dmfe: Dynamic Reset device 1
[ 1344.844020] dmfe: dmfe_dynamic_reset() 0
[ 1344.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1344.844057] dmfe: dmfe_init_dm910x() 0
[ 1344.844163] dmfe: dmfe_parse_srom()  0
[ 1344.845106] dmfe: dmfe_descriptor_init() 0
[ 1344.845135] dmfe: send_filter_frame() 0
[ 1345.844007] dmfe: dmfe_timer() 0
[ 1348.844008] dmfe: dmfe_timer() 0
[ 1348.844016] eth0: Tx timeout - resetting
[ 1348.844018] dmfe: Dynamic Reset device 1
[ 1348.844020] dmfe: dmfe_dynamic_reset() 0
[ 1348.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1348.844059] dmfe: dmfe_init_dm910x() 0
[ 1348.844165] dmfe: dmfe_parse_srom()  0
[ 1348.845109] dmfe: dmfe_descriptor_init() 0
[ 1348.845139] dmfe: send_filter_frame() 0
[ 1349.844008] dmfe: dmfe_timer() 0
[ 1352.844009] dmfe: dmfe_timer() 0
[ 1352.844016] eth0: Tx timeout - resetting
[ 1352.844019] dmfe: Dynamic Reset device 1
[ 1352.844021] dmfe: dmfe_dynamic_reset() 0
[ 1352.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1352.844057] dmfe: dmfe_init_dm910x() 0
[ 1352.844165] dmfe: dmfe_parse_srom()  0
[ 1352.845108] dmfe: dmfe_descriptor_init() 0
[ 1352.845137] dmfe: send_filter_frame() 0
[ 1353.844013] dmfe: dmfe_timer() 0
[ 1356.844014] dmfe: dmfe_timer() 0
[ 1356.844022] eth0: Tx timeout - resetting
[ 1356.844024] dmfe: Dynamic Reset device 1
[ 1356.844026] dmfe: dmfe_dynamic_reset() 0
[ 1356.844042] dmfe: dmfe_free_rxbuffer() 0
[ 1356.844063] dmfe: dmfe_init_dm910x() 0
[ 1356.844170] dmfe: dmfe_parse_srom()  0
[ 1356.845113] dmfe: dmfe_descriptor_init() 0
[ 1356.845141] dmfe: send_filter_frame() 0
[ 1357.844010] dmfe: dmfe_timer() 0
[ 1360.844008] dmfe: dmfe_timer() 0
[ 1360.844016] eth0: Tx timeout - resetting
[ 1360.844018] dmfe: Dynamic Reset device 1
[ 1360.844020] dmfe: dmfe_dynamic_reset() 0
[ 1360.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1360.844057] dmfe: dmfe_init_dm910x() 0
[ 1360.844163] dmfe: dmfe_parse_srom()  0
[ 1360.845106] dmfe: dmfe_descriptor_init() 0
[ 1360.845135] dmfe: send_filter_frame() 0
[ 1361.844008] dmfe: dmfe_timer() 0
[ 1364.844008] dmfe: dmfe_timer() 0
[ 1364.844016] eth0: Tx timeout - resetting
[ 1364.844018] dmfe: Dynamic Reset device 1
[ 1364.844020] dmfe: dmfe_dynamic_reset() 0
[ 1364.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1364.844057] dmfe: dmfe_init_dm910x() 0
[ 1364.844163] dmfe: dmfe_parse_srom()  0
[ 1364.845106] dmfe: dmfe_descriptor_init() 0
[ 1364.845135] dmfe: send_filter_frame() 0
[ 1365.844013] dmfe: dmfe_timer() 0
[ 1368.844011] dmfe: dmfe_timer() 0
[ 1368.844019] eth0: Tx timeout - resetting
[ 1368.844021] dmfe: Dynamic Reset device 1
[ 1368.844023] dmfe: dmfe_dynamic_reset() 0
[ 1368.844040] dmfe: dmfe_free_rxbuffer() 0
[ 1368.844060] dmfe: dmfe_init_dm910x() 0
[ 1368.844166] dmfe: dmfe_parse_srom()  0
[ 1368.845109] dmfe: dmfe_descriptor_init() 0
[ 1368.845138] dmfe: send_filter_frame() 0
[ 1369.844008] dmfe: dmfe_timer() 0
[ 1372.844011] dmfe: dmfe_timer() 0
[ 1372.844019] eth0: Tx timeout - resetting
[ 1372.844021] dmfe: Dynamic Reset device 1
[ 1372.844023] dmfe: dmfe_dynamic_reset() 0
[ 1372.844040] dmfe: dmfe_free_rxbuffer() 0
[ 1372.844060] dmfe: dmfe_init_dm910x() 0
[ 1372.844167] dmfe: dmfe_parse_srom()  0
[ 1372.845112] dmfe: dmfe_descriptor_init() 0
[ 1372.845140] dmfe: send_filter_frame() 0
[ 1373.844008] dmfe: dmfe_timer() 0
[ 1376.844018] dmfe: dmfe_timer() 0
[ 1376.844026] eth0: Tx timeout - resetting
[ 1376.844028] dmfe: Dynamic Reset device 1
[ 1376.844030] dmfe: dmfe_dynamic_reset() 0
[ 1376.844047] dmfe: dmfe_free_rxbuffer() 0
[ 1376.844066] dmfe: dmfe_init_dm910x() 0
[ 1376.844173] dmfe: dmfe_parse_srom()  0
[ 1376.845120] dmfe: dmfe_descriptor_init() 0
[ 1376.845149] dmfe: send_filter_frame() 0
[ 1377.844008] dmfe: dmfe_timer() 0
[ 1380.844011] dmfe: dmfe_timer() 0
[ 1380.844019] eth0: Tx timeout - resetting
[ 1380.844021] dmfe: Dynamic Reset device 1
[ 1380.844023] dmfe: dmfe_dynamic_reset() 0
[ 1380.844039] dmfe: dmfe_free_rxbuffer() 0
[ 1380.844061] dmfe: dmfe_init_dm910x() 0
[ 1380.844168] dmfe: dmfe_parse_srom()  0
[ 1380.845110] dmfe: dmfe_descriptor_init() 0
[ 1380.845139] dmfe: send_filter_frame() 0
[ 1381.844008] dmfe: dmfe_timer() 0
[ 1384.844007] dmfe: dmfe_timer() 0
[ 1384.844015] eth0: Tx timeout - resetting
[ 1384.844017] dmfe: Dynamic Reset device 1
[ 1384.844019] dmfe: dmfe_dynamic_reset() 0
[ 1384.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1384.844056] dmfe: dmfe_init_dm910x() 0
[ 1384.844162] dmfe: dmfe_parse_srom()  0
[ 1384.845105] dmfe: dmfe_descriptor_init() 0
[ 1384.845133] dmfe: send_filter_frame() 0
[ 1385.844008] dmfe: dmfe_timer() 0
[ 1388.844008] dmfe: dmfe_timer() 0
[ 1388.844016] eth0: Tx timeout - resetting
[ 1388.844018] dmfe: Dynamic Reset device 1
[ 1388.844020] dmfe: dmfe_dynamic_reset() 0
[ 1388.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1388.844056] dmfe: dmfe_init_dm910x() 0
[ 1388.844163] dmfe: dmfe_parse_srom()  0
[ 1388.845107] dmfe: dmfe_descriptor_init() 0
[ 1388.845135] dmfe: send_filter_frame() 0
[ 1389.844013] dmfe: dmfe_timer() 0
[ 1392.844013] dmfe: dmfe_timer() 0
[ 1392.844022] eth0: Tx timeout - resetting
[ 1392.844024] dmfe: Dynamic Reset device 1
[ 1392.844026] dmfe: dmfe_dynamic_reset() 0
[ 1392.844042] dmfe: dmfe_free_rxbuffer() 0
[ 1392.844061] dmfe: dmfe_init_dm910x() 0
[ 1392.844167] dmfe: dmfe_parse_srom()  0
[ 1392.845111] dmfe: dmfe_descriptor_init() 0
[ 1392.845141] dmfe: send_filter_frame() 0
[ 1393.844008] dmfe: dmfe_timer() 0
[ 1396.844008] dmfe: dmfe_timer() 0
[ 1396.844016] eth0: Tx timeout - resetting
[ 1396.844018] dmfe: Dynamic Reset device 1
[ 1396.844020] dmfe: dmfe_dynamic_reset() 0
[ 1396.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1396.844059] dmfe: dmfe_init_dm910x() 0
[ 1396.844165] dmfe: dmfe_parse_srom()  0
[ 1396.845108] dmfe: dmfe_descriptor_init() 0
[ 1396.845137] dmfe: send_filter_frame() 0
[ 1397.844008] dmfe: dmfe_timer() 0
[ 1400.844009] dmfe: dmfe_timer() 0
[ 1400.844017] eth0: Tx timeout - resetting
[ 1400.844019] dmfe: Dynamic Reset device 1
[ 1400.844021] dmfe: dmfe_dynamic_reset() 0
[ 1400.844038] dmfe: dmfe_free_rxbuffer() 0
[ 1400.844058] dmfe: dmfe_init_dm910x() 0
[ 1400.844164] dmfe: dmfe_parse_srom()  0
[ 1400.845110] dmfe: dmfe_descriptor_init() 0
[ 1400.845138] dmfe: send_filter_frame() 0
[ 1401.844010] dmfe: dmfe_timer() 0
[ 1404.844008] dmfe: dmfe_timer() 0
[ 1404.844016] eth0: Tx timeout - resetting
[ 1404.844018] dmfe: Dynamic Reset device 1
[ 1404.844020] dmfe: dmfe_dynamic_reset() 0
[ 1404.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1404.844057] dmfe: dmfe_init_dm910x() 0
[ 1404.844163] dmfe: dmfe_parse_srom()  0
[ 1404.845106] dmfe: dmfe_descriptor_init() 0
[ 1404.845135] dmfe: send_filter_frame() 0
[ 1405.844007] dmfe: dmfe_timer() 0
[ 1408.844008] dmfe: dmfe_timer() 0
[ 1408.844016] eth0: Tx timeout - resetting
[ 1408.844018] dmfe: Dynamic Reset device 1
[ 1408.844020] dmfe: dmfe_dynamic_reset() 0
[ 1408.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1408.844055] dmfe: dmfe_init_dm910x() 0
[ 1408.844162] dmfe: dmfe_parse_srom()  0
[ 1408.845106] dmfe: dmfe_descriptor_init() 0
[ 1408.845136] dmfe: send_filter_frame() 0
[ 1409.844008] dmfe: dmfe_timer() 0
[ 1412.844008] dmfe: dmfe_timer() 0
[ 1412.844016] eth0: Tx timeout - resetting
[ 1412.844018] dmfe: Dynamic Reset device 1
[ 1412.844020] dmfe: dmfe_dynamic_reset() 0
[ 1412.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1412.844057] dmfe: dmfe_init_dm910x() 0
[ 1412.844164] dmfe: dmfe_parse_srom()  0
[ 1412.845108] dmfe: dmfe_descriptor_init() 0
[ 1412.845137] dmfe: send_filter_frame() 0
[ 1413.844010] dmfe: dmfe_timer() 0
[ 1416.844013] dmfe: dmfe_timer() 0
[ 1416.844021] eth0: Tx timeout - resetting
[ 1416.844023] dmfe: Dynamic Reset device 1
[ 1416.844026] dmfe: dmfe_dynamic_reset() 0
[ 1416.844042] dmfe: dmfe_free_rxbuffer() 0
[ 1416.844061] dmfe: dmfe_init_dm910x() 0
[ 1416.844168] dmfe: dmfe_parse_srom()  0
[ 1416.845110] dmfe: dmfe_descriptor_init() 0
[ 1416.845138] dmfe: send_filter_frame() 0
[ 1417.844007] dmfe: dmfe_timer() 0
[ 1420.844008] dmfe: dmfe_timer() 0
[ 1420.844016] eth0: Tx timeout - resetting
[ 1420.844018] dmfe: Dynamic Reset device 1
[ 1420.844020] dmfe: dmfe_dynamic_reset() 0
[ 1420.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1420.844056] dmfe: dmfe_init_dm910x() 0
[ 1420.844162] dmfe: dmfe_parse_srom()  0
[ 1420.845105] dmfe: dmfe_descriptor_init() 0
[ 1420.845133] dmfe: send_filter_frame() 0
[ 1421.844008] dmfe: dmfe_timer() 0
[ 1424.844008] dmfe: dmfe_timer() 0
[ 1424.844016] eth0: Tx timeout - resetting
[ 1424.844018] dmfe: Dynamic Reset device 1
[ 1424.844020] dmfe: dmfe_dynamic_reset() 0
[ 1424.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1424.844056] dmfe: dmfe_init_dm910x() 0
[ 1424.844163] dmfe: dmfe_parse_srom()  0
[ 1424.845106] dmfe: dmfe_descriptor_init() 0
[ 1424.845136] dmfe: send_filter_frame() 0
[ 1425.844014] dmfe: dmfe_timer() 0
[ 1428.844008] dmfe: dmfe_timer() 0
[ 1428.844016] eth0: Tx timeout - resetting
[ 1428.844018] dmfe: Dynamic Reset device 1
[ 1428.844020] dmfe: dmfe_dynamic_reset() 0
[ 1428.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1428.844057] dmfe: dmfe_init_dm910x() 0
[ 1428.844163] dmfe: dmfe_parse_srom()  0
[ 1428.845107] dmfe: dmfe_descriptor_init() 0
[ 1428.845136] dmfe: send_filter_frame() 0
[ 1429.844008] dmfe: dmfe_timer() 0
[ 1432.844008] dmfe: dmfe_timer() 0
[ 1432.844017] eth0: Tx timeout - resetting
[ 1432.844019] dmfe: Dynamic Reset device 1
[ 1432.844021] dmfe: dmfe_dynamic_reset() 0
[ 1432.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1432.844057] dmfe: dmfe_init_dm910x() 0
[ 1432.844164] dmfe: dmfe_parse_srom()  0
[ 1432.845109] dmfe: dmfe_descriptor_init() 0
[ 1432.845137] dmfe: send_filter_frame() 0
[ 1433.844013] dmfe: dmfe_timer() 0
[ 1436.844020] dmfe: dmfe_timer() 0
[ 1436.844028] eth0: Tx timeout - resetting
[ 1436.844030] dmfe: Dynamic Reset device 1
[ 1436.844032] dmfe: dmfe_dynamic_reset() 0
[ 1436.844049] dmfe: dmfe_free_rxbuffer() 0
[ 1436.844068] dmfe: dmfe_init_dm910x() 0
[ 1436.844175] dmfe: dmfe_parse_srom()  0
[ 1436.845118] dmfe: dmfe_descriptor_init() 0
[ 1436.845146] dmfe: send_filter_frame() 0
[ 1437.844007] dmfe: dmfe_timer() 0
[ 1440.844008] dmfe: dmfe_timer() 0
[ 1440.844015] eth0: Tx timeout - resetting
[ 1440.844017] dmfe: Dynamic Reset device 1
[ 1440.844020] dmfe: dmfe_dynamic_reset() 0
[ 1440.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1440.844055] dmfe: dmfe_init_dm910x() 0
[ 1440.844162] dmfe: dmfe_parse_srom()  0
[ 1440.845104] dmfe: dmfe_descriptor_init() 0
[ 1440.845134] dmfe: send_filter_frame() 0
[ 1441.844007] dmfe: dmfe_timer() 0
[ 1444.844008] dmfe: dmfe_timer() 0
[ 1444.844016] eth0: Tx timeout - resetting
[ 1444.844018] dmfe: Dynamic Reset device 1
[ 1444.844020] dmfe: dmfe_dynamic_reset() 0
[ 1444.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1444.844058] dmfe: dmfe_init_dm910x() 0
[ 1444.844164] dmfe: dmfe_parse_srom()  0
[ 1444.845109] dmfe: dmfe_descriptor_init() 0
[ 1444.845137] dmfe: send_filter_frame() 0
[ 1445.844008] dmfe: dmfe_timer() 0
[ 1448.844008] dmfe: dmfe_timer() 0
[ 1448.844016] eth0: Tx timeout - resetting
[ 1448.844018] dmfe: Dynamic Reset device 1
[ 1448.844020] dmfe: dmfe_dynamic_reset() 0
[ 1448.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1448.844056] dmfe: dmfe_init_dm910x() 0
[ 1448.844162] dmfe: dmfe_parse_srom()  0
[ 1448.845107] dmfe: dmfe_descriptor_init() 0
[ 1448.845136] dmfe: send_filter_frame() 0
[ 1449.844008] dmfe: dmfe_timer() 0
[ 1452.844008] dmfe: dmfe_timer() 0
[ 1452.844016] eth0: Tx timeout - resetting
[ 1452.844018] dmfe: Dynamic Reset device 1
[ 1452.844020] dmfe: dmfe_dynamic_reset() 0
[ 1452.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1452.844056] dmfe: dmfe_init_dm910x() 0
[ 1452.844164] dmfe: dmfe_parse_srom()  0
[ 1452.845110] dmfe: dmfe_descriptor_init() 0
[ 1452.845139] dmfe: send_filter_frame() 0
[ 1453.844008] dmfe: dmfe_timer() 0
[ 1456.844008] dmfe: dmfe_timer() 0
[ 1456.844016] eth0: Tx timeout - resetting
[ 1456.844018] dmfe: Dynamic Reset device 1
[ 1456.844020] dmfe: dmfe_dynamic_reset() 0
[ 1456.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1456.844056] dmfe: dmfe_init_dm910x() 0
[ 1456.844163] dmfe: dmfe_parse_srom()  0
[ 1456.845106] dmfe: dmfe_descriptor_init() 0
[ 1456.845136] dmfe: send_filter_frame() 0
[ 1457.844013] dmfe: dmfe_timer() 0
[ 1460.844013] dmfe: dmfe_timer() 0
[ 1460.844021] eth0: Tx timeout - resetting
[ 1460.844024] dmfe: Dynamic Reset device 1
[ 1460.844026] dmfe: dmfe_dynamic_reset() 0
[ 1460.844042] dmfe: dmfe_free_rxbuffer() 0
[ 1460.844063] dmfe: dmfe_init_dm910x() 0
[ 1460.844169] dmfe: dmfe_parse_srom()  0
[ 1460.845112] dmfe: dmfe_descriptor_init() 0
[ 1460.845141] dmfe: send_filter_frame() 0
[ 1461.844008] dmfe: dmfe_timer() 0
[ 1464.844009] dmfe: dmfe_timer() 0
[ 1464.844017] eth0: Tx timeout - resetting
[ 1464.844019] dmfe: Dynamic Reset device 1
[ 1464.844021] dmfe: dmfe_dynamic_reset() 0
[ 1464.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1464.844056] dmfe: dmfe_init_dm910x() 0
[ 1464.844163] dmfe: dmfe_parse_srom()  0
[ 1464.845106] dmfe: dmfe_descriptor_init() 0
[ 1464.845134] dmfe: send_filter_frame() 0
[ 1465.844008] dmfe: dmfe_timer() 0
[ 1468.844007] dmfe: dmfe_timer() 0
[ 1468.844015] eth0: Tx timeout - resetting
[ 1468.844017] dmfe: Dynamic Reset device 1
[ 1468.844019] dmfe: dmfe_dynamic_reset() 0
[ 1468.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1468.844056] dmfe: dmfe_init_dm910x() 0
[ 1468.844162] dmfe: dmfe_parse_srom()  0
[ 1468.845105] dmfe: dmfe_descriptor_init() 0
[ 1468.845134] dmfe: send_filter_frame() 0
[ 1469.844008] dmfe: dmfe_timer() 0
[ 1472.844008] dmfe: dmfe_timer() 0
[ 1472.844017] eth0: Tx timeout - resetting
[ 1472.844019] dmfe: Dynamic Reset device 1
[ 1472.844021] dmfe: dmfe_dynamic_reset() 0
[ 1472.844038] dmfe: dmfe_free_rxbuffer() 0
[ 1472.844058] dmfe: dmfe_init_dm910x() 0
[ 1472.844164] dmfe: dmfe_parse_srom()  0
[ 1472.845108] dmfe: dmfe_descriptor_init() 0
[ 1472.845136] dmfe: send_filter_frame() 0
[ 1473.844008] dmfe: dmfe_timer() 0
[ 1476.844008] dmfe: dmfe_timer() 0
[ 1476.844016] eth0: Tx timeout - resetting
[ 1476.844018] dmfe: Dynamic Reset device 1
[ 1476.844020] dmfe: dmfe_dynamic_reset() 0
[ 1476.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1476.844056] dmfe: dmfe_init_dm910x() 0
[ 1476.844162] dmfe: dmfe_parse_srom()  0
[ 1476.845106] dmfe: dmfe_descriptor_init() 0
[ 1476.845135] dmfe: send_filter_frame() 0
[ 1477.844008] dmfe: dmfe_timer() 0
[ 1480.844008] dmfe: dmfe_timer() 0
[ 1480.844016] eth0: Tx timeout - resetting
[ 1480.844018] dmfe: Dynamic Reset device 1
[ 1480.844020] dmfe: dmfe_dynamic_reset() 0
[ 1480.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1480.844058] dmfe: dmfe_init_dm910x() 0
[ 1480.844164] dmfe: dmfe_parse_srom()  0
[ 1480.845110] dmfe: dmfe_descriptor_init() 0
[ 1480.845139] dmfe: send_filter_frame() 0
[ 1481.844008] dmfe: dmfe_timer() 0
[ 1484.844013] dmfe: dmfe_timer() 0
[ 1484.844021] eth0: Tx timeout - resetting
[ 1484.844023] dmfe: Dynamic Reset device 1
[ 1484.844026] dmfe: dmfe_dynamic_reset() 0
[ 1484.844042] dmfe: dmfe_free_rxbuffer() 0
[ 1484.844063] dmfe: dmfe_init_dm910x() 0
[ 1484.844169] dmfe: dmfe_parse_srom()  0
[ 1484.845112] dmfe: dmfe_descriptor_init() 0
[ 1484.845141] dmfe: send_filter_frame() 0
[ 1485.844008] dmfe: dmfe_timer() 0
[ 1488.844008] dmfe: dmfe_timer() 0
[ 1488.844016] eth0: Tx timeout - resetting
[ 1488.844018] dmfe: Dynamic Reset device 1
[ 1488.844020] dmfe: dmfe_dynamic_reset() 0
[ 1488.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1488.844057] dmfe: dmfe_init_dm910x() 0
[ 1488.844163] dmfe: dmfe_parse_srom()  0
[ 1488.845106] dmfe: dmfe_descriptor_init() 0
[ 1488.845135] dmfe: send_filter_frame() 0
[ 1489.844008] dmfe: dmfe_timer() 0
[ 1492.844008] dmfe: dmfe_timer() 0
[ 1492.844016] eth0: Tx timeout - resetting
[ 1492.844019] dmfe: Dynamic Reset device 1
[ 1492.844021] dmfe: dmfe_dynamic_reset() 0
[ 1492.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1492.844057] dmfe: dmfe_init_dm910x() 0
[ 1492.844164] dmfe: dmfe_parse_srom()  0
[ 1492.845109] dmfe: dmfe_descriptor_init() 0
[ 1492.845138] dmfe: send_filter_frame() 0
[ 1493.844013] dmfe: dmfe_timer() 0
[ 1496.844021] dmfe: dmfe_timer() 0
[ 1496.844029] eth0: Tx timeout - resetting
[ 1496.844031] dmfe: Dynamic Reset device 1
[ 1496.844033] dmfe: dmfe_dynamic_reset() 0
[ 1496.844049] dmfe: dmfe_free_rxbuffer() 0
[ 1496.844069] dmfe: dmfe_init_dm910x() 0
[ 1496.844177] dmfe: dmfe_parse_srom()  0
[ 1496.845121] dmfe: dmfe_descriptor_init() 0
[ 1496.845149] dmfe: send_filter_frame() 0
[ 1497.844008] dmfe: dmfe_timer() 0
[ 1500.844007] dmfe: dmfe_timer() 0
[ 1500.844015] eth0: Tx timeout - resetting
[ 1500.844017] dmfe: Dynamic Reset device 1
[ 1500.844020] dmfe: dmfe_dynamic_reset() 0
[ 1500.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1500.844055] dmfe: dmfe_init_dm910x() 0
[ 1500.844162] dmfe: dmfe_parse_srom()  0
[ 1500.845104] dmfe: dmfe_descriptor_init() 0
[ 1500.845133] dmfe: send_filter_frame() 0
[ 1501.844008] dmfe: dmfe_timer() 0
[ 1504.844008] dmfe: dmfe_timer() 0
[ 1504.844016] eth0: Tx timeout - resetting
[ 1504.844018] dmfe: Dynamic Reset device 1
[ 1504.844020] dmfe: dmfe_dynamic_reset() 0
[ 1504.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1504.844057] dmfe: dmfe_init_dm910x() 0
[ 1504.844163] dmfe: dmfe_parse_srom()  0
[ 1504.845106] dmfe: dmfe_descriptor_init() 0
[ 1504.845135] dmfe: send_filter_frame() 0
[ 1505.844008] dmfe: dmfe_timer() 0
[ 1508.844008] dmfe: dmfe_timer() 0
[ 1508.844016] eth0: Tx timeout - resetting
[ 1508.844018] dmfe: Dynamic Reset device 1
[ 1508.844020] dmfe: dmfe_dynamic_reset() 0
[ 1508.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1508.844057] dmfe: dmfe_init_dm910x() 0
[ 1508.844163] dmfe: dmfe_parse_srom()  0
[ 1508.845106] dmfe: dmfe_descriptor_init() 0
[ 1508.845135] dmfe: send_filter_frame() 0
[ 1509.844007] dmfe: dmfe_timer() 0
[ 1512.844008] dmfe: dmfe_timer() 0
[ 1512.844017] eth0: Tx timeout - resetting
[ 1512.844019] dmfe: Dynamic Reset device 1
[ 1512.844021] dmfe: dmfe_dynamic_reset() 0
[ 1512.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1512.844058] dmfe: dmfe_init_dm910x() 0
[ 1512.844165] dmfe: dmfe_parse_srom()  0
[ 1512.845108] dmfe: dmfe_descriptor_init() 0
[ 1512.845137] dmfe: send_filter_frame() 0
[ 1513.844008] dmfe: dmfe_timer() 0
[ 1516.844008] dmfe: dmfe_timer() 0
[ 1516.844016] eth0: Tx timeout - resetting
[ 1516.844018] dmfe: Dynamic Reset device 1
[ 1516.844020] dmfe: dmfe_dynamic_reset() 0
[ 1516.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1516.844056] dmfe: dmfe_init_dm910x() 0
[ 1516.844162] dmfe: dmfe_parse_srom()  0
[ 1516.845105] dmfe: dmfe_descriptor_init() 0
[ 1516.845133] dmfe: send_filter_frame() 0
[ 1517.844014] dmfe: dmfe_timer() 0
[ 1520.844009] dmfe: dmfe_timer() 0
[ 1520.844017] eth0: Tx timeout - resetting
[ 1520.844019] dmfe: Dynamic Reset device 1
[ 1520.844021] dmfe: dmfe_dynamic_reset() 0
[ 1520.844038] dmfe: dmfe_free_rxbuffer() 0
[ 1520.844058] dmfe: dmfe_init_dm910x() 0
[ 1520.844164] dmfe: dmfe_parse_srom()  0
[ 1520.845108] dmfe: dmfe_descriptor_init() 0
[ 1520.845136] dmfe: send_filter_frame() 0
[ 1521.844007] dmfe: dmfe_timer() 0
[ 1524.844008] dmfe: dmfe_timer() 0
[ 1524.844016] eth0: Tx timeout - resetting
[ 1524.844018] dmfe: Dynamic Reset device 1
[ 1524.844020] dmfe: dmfe_dynamic_reset() 0
[ 1524.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1524.844058] dmfe: dmfe_init_dm910x() 0
[ 1524.844164] dmfe: dmfe_parse_srom()  0
[ 1524.845107] dmfe: dmfe_descriptor_init() 0
[ 1524.845136] dmfe: send_filter_frame() 0
[ 1525.844010] dmfe: dmfe_timer() 0
[ 1528.844008] dmfe: dmfe_timer() 0
[ 1528.844016] eth0: Tx timeout - resetting
[ 1528.844018] dmfe: Dynamic Reset device 1
[ 1528.844020] dmfe: dmfe_dynamic_reset() 0
[ 1528.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1528.844056] dmfe: dmfe_init_dm910x() 0
[ 1528.844163] dmfe: dmfe_parse_srom()  0
[ 1528.845106] dmfe: dmfe_descriptor_init() 0
[ 1528.845135] dmfe: send_filter_frame() 0
[ 1529.844008] dmfe: dmfe_timer() 0
[ 1532.844008] dmfe: dmfe_timer() 0
[ 1532.844016] eth0: Tx timeout - resetting
[ 1532.844018] dmfe: Dynamic Reset device 1
[ 1532.844020] dmfe: dmfe_dynamic_reset() 0
[ 1532.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1532.844057] dmfe: dmfe_init_dm910x() 0
[ 1532.844163] dmfe: dmfe_parse_srom()  0
[ 1532.845106] dmfe: dmfe_descriptor_init() 0
[ 1532.845135] dmfe: send_filter_frame() 0
[ 1533.844007] dmfe: dmfe_timer() 0
[ 1536.844008] dmfe: dmfe_timer() 0
[ 1536.844016] eth0: Tx timeout - resetting
[ 1536.844018] dmfe: Dynamic Reset device 1
[ 1536.844020] dmfe: dmfe_dynamic_reset() 0
[ 1536.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1536.844057] dmfe: dmfe_init_dm910x() 0
[ 1536.844163] dmfe: dmfe_parse_srom()  0
[ 1536.845106] dmfe: dmfe_descriptor_init() 0
[ 1536.845134] dmfe: send_filter_frame() 0
[ 1537.844008] dmfe: dmfe_timer() 0
[ 1540.844008] dmfe: dmfe_timer() 0
[ 1540.844016] eth0: Tx timeout - resetting
[ 1540.844018] dmfe: Dynamic Reset device 1
[ 1540.844020] dmfe: dmfe_dynamic_reset() 0
[ 1540.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1540.844057] dmfe: dmfe_init_dm910x() 0
[ 1540.844164] dmfe: dmfe_parse_srom()  0
[ 1540.845106] dmfe: dmfe_descriptor_init() 0
[ 1540.845136] dmfe: send_filter_frame() 0
[ 1541.844011] dmfe: dmfe_timer() 0
[ 1544.844013] dmfe: dmfe_timer() 0
[ 1544.844021] eth0: Tx timeout - resetting
[ 1544.844023] dmfe: Dynamic Reset device 1
[ 1544.844025] dmfe: dmfe_dynamic_reset() 0
[ 1544.844041] dmfe: dmfe_free_rxbuffer() 0
[ 1544.844061] dmfe: dmfe_init_dm910x() 0
[ 1544.844168] dmfe: dmfe_parse_srom()  0
[ 1544.845111] dmfe: dmfe_descriptor_init() 0
[ 1544.845139] dmfe: send_filter_frame() 0
[ 1545.844008] dmfe: dmfe_timer() 0
[ 1548.844008] dmfe: dmfe_timer() 0
[ 1548.844016] eth0: Tx timeout - resetting
[ 1548.844018] dmfe: Dynamic Reset device 1
[ 1548.844021] dmfe: dmfe_dynamic_reset() 0
[ 1548.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1548.844057] dmfe: dmfe_init_dm910x() 0
[ 1548.844163] dmfe: dmfe_parse_srom()  0
[ 1548.845106] dmfe: dmfe_descriptor_init() 0
[ 1548.845136] dmfe: send_filter_frame() 0
[ 1549.844008] dmfe: dmfe_timer() 0
[ 1552.844009] dmfe: dmfe_timer() 0
[ 1552.844017] eth0: Tx timeout - resetting
[ 1552.844019] dmfe: Dynamic Reset device 1
[ 1552.844021] dmfe: dmfe_dynamic_reset() 0
[ 1552.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1552.844058] dmfe: dmfe_init_dm910x() 0
[ 1552.844165] dmfe: dmfe_parse_srom()  0
[ 1552.845109] dmfe: dmfe_descriptor_init() 0
[ 1552.845138] dmfe: send_filter_frame() 0
[ 1553.844009] dmfe: dmfe_timer() 0
[ 1556.844020] dmfe: dmfe_timer() 0
[ 1556.844029] eth0: Tx timeout - resetting
[ 1556.844031] dmfe: Dynamic Reset device 1
[ 1556.844033] dmfe: dmfe_dynamic_reset() 0
[ 1556.844049] dmfe: dmfe_free_rxbuffer() 0
[ 1556.844069] dmfe: dmfe_init_dm910x() 0
[ 1556.844176] dmfe: dmfe_parse_srom()  0
[ 1556.845119] dmfe: dmfe_descriptor_init() 0
[ 1556.845148] dmfe: send_filter_frame() 0
[ 1557.844011] dmfe: dmfe_timer() 0
[ 1560.844007] dmfe: dmfe_timer() 0
[ 1560.844015] eth0: Tx timeout - resetting
[ 1560.844017] dmfe: Dynamic Reset device 1
[ 1560.844019] dmfe: dmfe_dynamic_reset() 0
[ 1560.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1560.844056] dmfe: dmfe_init_dm910x() 0
[ 1560.844163] dmfe: dmfe_parse_srom()  0
[ 1560.845106] dmfe: dmfe_descriptor_init() 0
[ 1560.845135] dmfe: send_filter_frame() 0
[ 1561.844007] dmfe: dmfe_timer() 0
[ 1564.844008] dmfe: dmfe_timer() 0
[ 1564.844016] eth0: Tx timeout - resetting
[ 1564.844018] dmfe: Dynamic Reset device 1
[ 1564.844020] dmfe: dmfe_dynamic_reset() 0
[ 1564.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1564.844058] dmfe: dmfe_init_dm910x() 0
[ 1564.844165] dmfe: dmfe_parse_srom()  0
[ 1564.845108] dmfe: dmfe_descriptor_init() 0
[ 1564.845136] dmfe: send_filter_frame() 0
[ 1565.844007] dmfe: dmfe_timer() 0
[ 1568.844012] dmfe: dmfe_timer() 0
[ 1568.844020] eth0: Tx timeout - resetting
[ 1568.844023] dmfe: Dynamic Reset device 1
[ 1568.844025] dmfe: dmfe_dynamic_reset() 0
[ 1568.844041] dmfe: dmfe_free_rxbuffer() 0
[ 1568.844061] dmfe: dmfe_init_dm910x() 0
[ 1568.844167] dmfe: dmfe_parse_srom()  0
[ 1568.845110] dmfe: dmfe_descriptor_init() 0
[ 1568.845139] dmfe: send_filter_frame() 0
[ 1569.844007] dmfe: dmfe_timer() 0
[ 1572.844008] dmfe: dmfe_timer() 0
[ 1572.844016] eth0: Tx timeout - resetting
[ 1572.844018] dmfe: Dynamic Reset device 1
[ 1572.844020] dmfe: dmfe_dynamic_reset() 0
[ 1572.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1572.844058] dmfe: dmfe_init_dm910x() 0
[ 1572.844165] dmfe: dmfe_parse_srom()  0
[ 1572.845109] dmfe: dmfe_descriptor_init() 0
[ 1572.845138] dmfe: send_filter_frame() 0
[ 1573.844008] dmfe: dmfe_timer() 0
[ 1576.844008] dmfe: dmfe_timer() 0
[ 1576.844016] eth0: Tx timeout - resetting
[ 1576.844018] dmfe: Dynamic Reset device 1
[ 1576.844020] dmfe: dmfe_dynamic_reset() 0
[ 1576.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1576.844057] dmfe: dmfe_init_dm910x() 0
[ 1576.844163] dmfe: dmfe_parse_srom()  0
[ 1576.845108] dmfe: dmfe_descriptor_init() 0
[ 1576.845136] dmfe: send_filter_frame() 0
[ 1577.844013] dmfe: dmfe_timer() 0
[ 1580.844013] dmfe: dmfe_timer() 0
[ 1580.844021] eth0: Tx timeout - resetting
[ 1580.844023] dmfe: Dynamic Reset device 1
[ 1580.844026] dmfe: dmfe_dynamic_reset() 0
[ 1580.844042] dmfe: dmfe_free_rxbuffer() 0
[ 1580.844062] dmfe: dmfe_init_dm910x() 0
[ 1580.844168] dmfe: dmfe_parse_srom()  0
[ 1580.845112] dmfe: dmfe_descriptor_init() 0
[ 1580.845141] dmfe: send_filter_frame() 0
[ 1581.844008] dmfe: dmfe_timer() 0
[ 1584.844008] dmfe: dmfe_timer() 0
[ 1584.844016] eth0: Tx timeout - resetting
[ 1584.844018] dmfe: Dynamic Reset device 1
[ 1584.844020] dmfe: dmfe_dynamic_reset() 0
[ 1584.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1584.844057] dmfe: dmfe_init_dm910x() 0
[ 1584.844164] dmfe: dmfe_parse_srom()  0
[ 1584.845107] dmfe: dmfe_descriptor_init() 0
[ 1584.845136] dmfe: send_filter_frame() 0
[ 1585.844009] dmfe: dmfe_timer() 0
[ 1588.844009] dmfe: dmfe_timer() 0
[ 1588.844017] eth0: Tx timeout - resetting
[ 1588.844019] dmfe: Dynamic Reset device 1
[ 1588.844021] dmfe: dmfe_dynamic_reset() 0
[ 1588.844038] dmfe: dmfe_free_rxbuffer() 0
[ 1588.844059] dmfe: dmfe_init_dm910x() 0
[ 1588.844165] dmfe: dmfe_parse_srom()  0
[ 1588.845109] dmfe: dmfe_descriptor_init() 0
[ 1588.845138] dmfe: send_filter_frame() 0
[ 1589.844014] dmfe: dmfe_timer() 0
[ 1592.844008] dmfe: dmfe_timer() 0
[ 1592.844016] eth0: Tx timeout - resetting
[ 1592.844018] dmfe: Dynamic Reset device 1
[ 1592.844020] dmfe: dmfe_dynamic_reset() 0
[ 1592.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1592.844057] dmfe: dmfe_init_dm910x() 0
[ 1592.844164] dmfe: dmfe_parse_srom()  0
[ 1592.845107] dmfe: dmfe_descriptor_init() 0
[ 1592.845135] dmfe: send_filter_frame() 0
[ 1593.844008] dmfe: dmfe_timer() 0
[ 1596.844008] dmfe: dmfe_timer() 0
[ 1596.844016] eth0: Tx timeout - resetting
[ 1596.844018] dmfe: Dynamic Reset device 1
[ 1596.844020] dmfe: dmfe_dynamic_reset() 0
[ 1596.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1596.844057] dmfe: dmfe_init_dm910x() 0
[ 1596.844163] dmfe: dmfe_parse_srom()  0
[ 1596.845106] dmfe: dmfe_descriptor_init() 0
[ 1596.845134] dmfe: send_filter_frame() 0
[ 1597.844009] dmfe: dmfe_timer() 0
[ 1600.844008] dmfe: dmfe_timer() 0
[ 1600.844016] eth0: Tx timeout - resetting
[ 1600.844018] dmfe: Dynamic Reset device 1
[ 1600.844020] dmfe: dmfe_dynamic_reset() 0
[ 1600.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1600.844057] dmfe: dmfe_init_dm910x() 0
[ 1600.844163] dmfe: dmfe_parse_srom()  0
[ 1600.845107] dmfe: dmfe_descriptor_init() 0
[ 1600.845135] dmfe: send_filter_frame() 0
[ 1601.844013] dmfe: dmfe_timer() 0
[ 1604.844012] dmfe: dmfe_timer() 0
[ 1604.844020] eth0: Tx timeout - resetting
[ 1604.844023] dmfe: Dynamic Reset device 1
[ 1604.844025] dmfe: dmfe_dynamic_reset() 0
[ 1604.844041] dmfe: dmfe_free_rxbuffer() 0
[ 1604.844061] dmfe: dmfe_init_dm910x() 0
[ 1604.844167] dmfe: dmfe_parse_srom()  0
[ 1604.845111] dmfe: dmfe_descriptor_init() 0
[ 1604.845140] dmfe: send_filter_frame() 0
[ 1605.844008] dmfe: dmfe_timer() 0
[ 1608.844008] dmfe: dmfe_timer() 0
[ 1608.844016] eth0: Tx timeout - resetting
[ 1608.844018] dmfe: Dynamic Reset device 1
[ 1608.844020] dmfe: dmfe_dynamic_reset() 0
[ 1608.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1608.844056] dmfe: dmfe_init_dm910x() 0
[ 1608.844163] dmfe: dmfe_parse_srom()  0
[ 1608.845105] dmfe: dmfe_descriptor_init() 0
[ 1608.845134] dmfe: send_filter_frame() 0
[ 1609.844009] dmfe: dmfe_timer() 0
[ 1612.844009] dmfe: dmfe_timer() 0
[ 1612.844017] eth0: Tx timeout - resetting
[ 1612.844019] dmfe: Dynamic Reset device 1
[ 1612.844022] dmfe: dmfe_dynamic_reset() 0
[ 1612.844038] dmfe: dmfe_free_rxbuffer() 0
[ 1612.844059] dmfe: dmfe_init_dm910x() 0
[ 1612.844165] dmfe: dmfe_parse_srom()  0
[ 1612.845108] dmfe: dmfe_descriptor_init() 0
[ 1612.845137] dmfe: send_filter_frame() 0
[ 1613.844014] dmfe: dmfe_timer() 0
[ 1616.844020] dmfe: dmfe_timer() 0
[ 1616.844029] eth0: Tx timeout - resetting
[ 1616.844031] dmfe: Dynamic Reset device 1
[ 1616.844033] dmfe: dmfe_dynamic_reset() 0
[ 1616.844049] dmfe: dmfe_free_rxbuffer() 0
[ 1616.844070] dmfe: dmfe_init_dm910x() 0
[ 1616.844176] dmfe: dmfe_parse_srom()  0
[ 1616.845120] dmfe: dmfe_descriptor_init() 0
[ 1616.845149] dmfe: send_filter_frame() 0
[ 1617.844009] dmfe: dmfe_timer() 0
[ 1620.844008] dmfe: dmfe_timer() 0
[ 1620.844016] eth0: Tx timeout - resetting
[ 1620.844018] dmfe: Dynamic Reset device 1
[ 1620.844020] dmfe: dmfe_dynamic_reset() 0
[ 1620.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1620.844057] dmfe: dmfe_init_dm910x() 0
[ 1620.844164] dmfe: dmfe_parse_srom()  0
[ 1620.845107] dmfe: dmfe_descriptor_init() 0
[ 1620.845136] dmfe: send_filter_frame() 0
[ 1621.844009] dmfe: dmfe_timer() 0
[ 1624.844008] dmfe: dmfe_timer() 0
[ 1624.844016] eth0: Tx timeout - resetting
[ 1624.844018] dmfe: Dynamic Reset device 1
[ 1624.844020] dmfe: dmfe_dynamic_reset() 0
[ 1624.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1624.844058] dmfe: dmfe_init_dm910x() 0
[ 1624.844164] dmfe: dmfe_parse_srom()  0
[ 1624.845107] dmfe: dmfe_descriptor_init() 0
[ 1624.845135] dmfe: send_filter_frame() 0
[ 1625.844016] dmfe: dmfe_timer() 0
[ 1628.844009] dmfe: dmfe_timer() 0
[ 1628.844017] eth0: Tx timeout - resetting
[ 1628.844020] dmfe: Dynamic Reset device 1
[ 1628.844022] dmfe: dmfe_dynamic_reset() 0
[ 1628.844038] dmfe: dmfe_free_rxbuffer() 0
[ 1628.844057] dmfe: dmfe_init_dm910x() 0
[ 1628.844163] dmfe: dmfe_parse_srom()  0
[ 1628.845107] dmfe: dmfe_descriptor_init() 0
[ 1628.845135] dmfe: send_filter_frame() 0
[ 1629.844007] dmfe: dmfe_timer() 0
[ 1632.844010] dmfe: dmfe_timer() 0
[ 1632.844018] eth0: Tx timeout - resetting
[ 1632.844020] dmfe: Dynamic Reset device 1
[ 1632.844022] dmfe: dmfe_dynamic_reset() 0
[ 1632.844039] dmfe: dmfe_free_rxbuffer() 0
[ 1632.844059] dmfe: dmfe_init_dm910x() 0
[ 1632.844167] dmfe: dmfe_parse_srom()  0
[ 1632.845111] dmfe: dmfe_descriptor_init() 0
[ 1632.845140] dmfe: send_filter_frame() 0
[ 1633.844007] dmfe: dmfe_timer() 0
[ 1636.844009] dmfe: dmfe_timer() 0
[ 1636.844016] eth0: Tx timeout - resetting
[ 1636.844018] dmfe: Dynamic Reset device 1
[ 1636.844020] dmfe: dmfe_dynamic_reset() 0
[ 1636.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1636.844056] dmfe: dmfe_init_dm910x() 0
[ 1636.844163] dmfe: dmfe_parse_srom()  0
[ 1636.845105] dmfe: dmfe_descriptor_init() 0
[ 1636.845133] dmfe: send_filter_frame() 0
[ 1637.844009] dmfe: dmfe_timer() 0
[ 1637.956932] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 1640.844009] dmfe: dmfe_timer() 0
[ 1640.844017] eth0: Tx timeout - resetting
[ 1640.844019] dmfe: Dynamic Reset device 1
[ 1640.844021] dmfe: dmfe_dynamic_reset() 0
[ 1640.844038] dmfe: dmfe_free_rxbuffer() 0
[ 1640.844058] dmfe: dmfe_init_dm910x() 0
[ 1640.844164] dmfe: dmfe_parse_srom()  0
[ 1640.845107] dmfe: dmfe_descriptor_init() 0
[ 1640.845135] dmfe: send_filter_frame() 0
[ 1641.844013] dmfe: dmfe_timer() 0
[ 1644.844013] dmfe: dmfe_timer() 0
[ 1644.844021] eth0: Tx timeout - resetting
[ 1644.844023] dmfe: Dynamic Reset device 1
[ 1644.844025] dmfe: dmfe_dynamic_reset() 0
[ 1644.844042] dmfe: dmfe_free_rxbuffer() 0
[ 1644.844062] dmfe: dmfe_init_dm910x() 0
[ 1644.844168] dmfe: dmfe_parse_srom()  0
[ 1644.845113] dmfe: dmfe_descriptor_init() 0
[ 1644.845142] dmfe: send_filter_frame() 0
[ 1645.844009] dmfe: dmfe_timer() 0
[ 1648.844008] dmfe: dmfe_timer() 0
[ 1648.844016] eth0: Tx timeout - resetting
[ 1648.844018] dmfe: Dynamic Reset device 1
[ 1648.844020] dmfe: dmfe_dynamic_reset() 0
[ 1648.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1648.844058] dmfe: dmfe_init_dm910x() 0
[ 1648.844165] dmfe: dmfe_parse_srom()  0
[ 1648.845108] dmfe: dmfe_descriptor_init() 0
[ 1648.845137] dmfe: send_filter_frame() 0
[ 1649.844010] dmfe: dmfe_timer() 0
[ 1652.844008] dmfe: dmfe_timer() 0
[ 1652.844016] eth0: Tx timeout - resetting
[ 1652.844018] dmfe: Dynamic Reset device 1
[ 1652.844021] dmfe: dmfe_dynamic_reset() 0
[ 1652.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1652.844059] dmfe: dmfe_init_dm910x() 0
[ 1652.844166] dmfe: dmfe_parse_srom()  0
[ 1652.845110] dmfe: dmfe_descriptor_init() 0
[ 1652.845139] dmfe: send_filter_frame() 0
[ 1653.844009] dmfe: dmfe_timer() 0
[ 1656.844008] dmfe: dmfe_timer() 0
[ 1656.844016] eth0: Tx timeout - resetting
[ 1656.844018] dmfe: Dynamic Reset device 1
[ 1656.844020] dmfe: dmfe_dynamic_reset() 0
[ 1656.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1656.844056] dmfe: dmfe_init_dm910x() 0
[ 1656.844163] dmfe: dmfe_parse_srom()  0
[ 1656.845106] dmfe: dmfe_descriptor_init() 0
[ 1656.845134] dmfe: send_filter_frame() 0
[ 1657.844010] dmfe: dmfe_timer() 0
[ 1660.844008] dmfe: dmfe_timer() 0
[ 1660.844016] eth0: Tx timeout - resetting
[ 1660.844018] dmfe: Dynamic Reset device 1
[ 1660.844020] dmfe: dmfe_dynamic_reset() 0
[ 1660.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1660.844057] dmfe: dmfe_init_dm910x() 0
[ 1660.844163] dmfe: dmfe_parse_srom()  0
[ 1660.845106] dmfe: dmfe_descriptor_init() 0
[ 1660.845135] dmfe: send_filter_frame() 0
[ 1661.844009] dmfe: dmfe_timer() 0
[ 1664.844008] dmfe: dmfe_timer() 0
[ 1664.844016] eth0: Tx timeout - resetting
[ 1664.844018] dmfe: Dynamic Reset device 1
[ 1664.844020] dmfe: dmfe_dynamic_reset() 0
[ 1664.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1664.844057] dmfe: dmfe_init_dm910x() 0
[ 1664.844163] dmfe: dmfe_parse_srom()  0
[ 1664.845107] dmfe: dmfe_descriptor_init() 0
[ 1664.845136] dmfe: send_filter_frame() 0
[ 1665.844012] dmfe: dmfe_timer() 0
[ 1668.844009] dmfe: dmfe_timer() 0
[ 1668.844017] eth0: Tx timeout - resetting
[ 1668.844019] dmfe: Dynamic Reset device 1
[ 1668.844021] dmfe: dmfe_dynamic_reset() 0
[ 1668.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1668.844058] dmfe: dmfe_init_dm910x() 0
[ 1668.844164] dmfe: dmfe_parse_srom()  0
[ 1668.845107] dmfe: dmfe_descriptor_init() 0
[ 1668.845136] dmfe: send_filter_frame() 0
[ 1669.844010] dmfe: dmfe_timer() 0
[ 1672.844008] dmfe: dmfe_timer() 0
[ 1672.844016] eth0: Tx timeout - resetting
[ 1672.844018] dmfe: Dynamic Reset device 1
[ 1672.844021] dmfe: dmfe_dynamic_reset() 0
[ 1672.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1672.844058] dmfe: dmfe_init_dm910x() 0
[ 1672.844165] dmfe: dmfe_parse_srom()  0
[ 1672.845111] dmfe: dmfe_descriptor_init() 0
[ 1672.845140] dmfe: send_filter_frame() 0
[ 1673.844009] dmfe: dmfe_timer() 0
[ 1676.844020] dmfe: dmfe_timer() 0
[ 1676.844028] eth0: Tx timeout - resetting
[ 1676.844030] dmfe: Dynamic Reset device 1
[ 1676.844033] dmfe: dmfe_dynamic_reset() 0
[ 1676.844049] dmfe: dmfe_free_rxbuffer() 0
[ 1676.844068] dmfe: dmfe_init_dm910x() 0
[ 1676.844175] dmfe: dmfe_parse_srom()  0
[ 1676.845122] dmfe: dmfe_descriptor_init() 0
[ 1676.845151] dmfe: send_filter_frame() 0
[ 1677.844012] dmfe: dmfe_timer() 0
[ 1680.844009] dmfe: dmfe_timer() 0
[ 1680.844018] eth0: Tx timeout - resetting
[ 1680.844020] dmfe: Dynamic Reset device 1
[ 1680.844022] dmfe: dmfe_dynamic_reset() 0
[ 1680.844038] dmfe: dmfe_free_rxbuffer() 0
[ 1680.844058] dmfe: dmfe_init_dm910x() 0
[ 1680.844164] dmfe: dmfe_parse_srom()  0
[ 1680.845108] dmfe: dmfe_descriptor_init() 0
[ 1680.845137] dmfe: send_filter_frame() 0
[ 1681.844010] dmfe: dmfe_timer() 0
[ 1684.844007] dmfe: dmfe_timer() 0
[ 1684.844015] eth0: Tx timeout - resetting
[ 1684.844017] dmfe: Dynamic Reset device 1
[ 1684.844020] dmfe: dmfe_dynamic_reset() 0
[ 1684.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1684.844056] dmfe: dmfe_init_dm910x() 0
[ 1684.844162] dmfe: dmfe_parse_srom()  0
[ 1684.845105] dmfe: dmfe_descriptor_init() 0
[ 1684.845134] dmfe: send_filter_frame() 0
[ 1685.844009] dmfe: dmfe_timer() 0
[ 1688.844008] dmfe: dmfe_timer() 0
[ 1688.844016] eth0: Tx timeout - resetting
[ 1688.844018] dmfe: Dynamic Reset device 1
[ 1688.844020] dmfe: dmfe_dynamic_reset() 0
[ 1688.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1688.844059] dmfe: dmfe_init_dm910x() 0
[ 1688.844165] dmfe: dmfe_parse_srom()  0
[ 1688.845109] dmfe: dmfe_descriptor_init() 0
[ 1688.845138] dmfe: send_filter_frame() 0
[ 1689.844012] dmfe: dmfe_timer() 0
[ 1692.844010] dmfe: dmfe_timer() 0
[ 1692.844018] eth0: Tx timeout - resetting
[ 1692.844020] dmfe: Dynamic Reset device 1
[ 1692.844022] dmfe: dmfe_dynamic_reset() 0
[ 1692.844039] dmfe: dmfe_free_rxbuffer() 0
[ 1692.844058] dmfe: dmfe_init_dm910x() 0
[ 1692.844164] dmfe: dmfe_parse_srom()  0
[ 1692.845108] dmfe: dmfe_descriptor_init() 0
[ 1692.845136] dmfe: send_filter_frame() 0
[ 1693.844009] dmfe: dmfe_timer() 0
[ 1696.844007] dmfe: dmfe_timer() 0
[ 1696.844015] eth0: Tx timeout - resetting
[ 1696.844017] dmfe: Dynamic Reset device 1
[ 1696.844019] dmfe: dmfe_dynamic_reset() 0
[ 1696.844035] dmfe: dmfe_free_rxbuffer() 0
[ 1696.844055] dmfe: dmfe_init_dm910x() 0
[ 1696.844161] dmfe: dmfe_parse_srom()  0
[ 1696.845104] dmfe: dmfe_descriptor_init() 0
[ 1696.845132] dmfe: send_filter_frame() 0
[ 1697.844010] dmfe: dmfe_timer() 0
[ 1700.844009] dmfe: dmfe_timer() 0
[ 1700.844017] eth0: Tx timeout - resetting
[ 1700.844019] dmfe: Dynamic Reset device 1
[ 1700.844021] dmfe: dmfe_dynamic_reset() 0
[ 1700.844038] dmfe: dmfe_free_rxbuffer() 0
[ 1700.844059] dmfe: dmfe_init_dm910x() 0
[ 1700.844165] dmfe: dmfe_parse_srom()  0
[ 1700.845110] dmfe: dmfe_descriptor_init() 0
[ 1700.845139] dmfe: send_filter_frame() 0
[ 1701.844011] dmfe: dmfe_timer() 0
[ 1704.844013] dmfe: dmfe_timer() 0
[ 1704.844021] eth0: Tx timeout - resetting
[ 1704.844023] dmfe: Dynamic Reset device 1
[ 1704.844025] dmfe: dmfe_dynamic_reset() 0
[ 1704.844042] dmfe: dmfe_free_rxbuffer() 0
[ 1704.844062] dmfe: dmfe_init_dm910x() 0
[ 1704.844168] dmfe: dmfe_parse_srom()  0
[ 1704.845111] dmfe: dmfe_descriptor_init() 0
[ 1704.845141] dmfe: send_filter_frame() 0
[ 1705.844009] dmfe: dmfe_timer() 0
[ 1708.844008] dmfe: dmfe_timer() 0
[ 1708.844016] eth0: Tx timeout - resetting
[ 1708.844018] dmfe: Dynamic Reset device 1
[ 1708.844020] dmfe: dmfe_dynamic_reset() 0
[ 1708.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1708.844057] dmfe: dmfe_init_dm910x() 0
[ 1708.844163] dmfe: dmfe_parse_srom()  0
[ 1708.845107] dmfe: dmfe_descriptor_init() 0
[ 1708.845136] dmfe: send_filter_frame() 0
[ 1709.844011] dmfe: dmfe_timer() 0
[ 1712.844014] dmfe: dmfe_timer() 0
[ 1712.844022] eth0: Tx timeout - resetting
[ 1712.844024] dmfe: Dynamic Reset device 1
[ 1712.844026] dmfe: dmfe_dynamic_reset() 0
[ 1712.844043] dmfe: dmfe_free_rxbuffer() 0
[ 1712.844063] dmfe: dmfe_init_dm910x() 0
[ 1712.844170] dmfe: dmfe_parse_srom()  0
[ 1712.845113] dmfe: dmfe_descriptor_init() 0
[ 1712.845141] dmfe: send_filter_frame() 0
[ 1713.844012] dmfe: dmfe_timer() 0
[ 1716.844017] dmfe: dmfe_timer() 0
[ 1716.844025] eth0: Tx timeout - resetting
[ 1716.844028] dmfe: Dynamic Reset device 1
[ 1716.844030] dmfe: dmfe_dynamic_reset() 0
[ 1716.844046] dmfe: dmfe_free_rxbuffer() 0
[ 1716.844066] dmfe: dmfe_init_dm910x() 0
[ 1716.844173] dmfe: dmfe_parse_srom()  0
[ 1716.845116] dmfe: dmfe_descriptor_init() 0
[ 1716.845145] dmfe: send_filter_frame() 0
[ 1717.844009] dmfe: dmfe_timer() 0
[ 1720.844009] dmfe: dmfe_timer() 0
[ 1720.844017] eth0: Tx timeout - resetting
[ 1720.844019] dmfe: Dynamic Reset device 1
[ 1720.844021] dmfe: dmfe_dynamic_reset() 0
[ 1720.844038] dmfe: dmfe_free_rxbuffer() 0
[ 1720.844057] dmfe: dmfe_init_dm910x() 0
[ 1720.844164] dmfe: dmfe_parse_srom()  0
[ 1720.845109] dmfe: dmfe_descriptor_init() 0
[ 1720.845138] dmfe: send_filter_frame() 0
[ 1721.844009] dmfe: dmfe_timer() 0
[ 1724.844008] dmfe: dmfe_timer() 0
[ 1724.844016] eth0: Tx timeout - resetting
[ 1724.844018] dmfe: Dynamic Reset device 1
[ 1724.844020] dmfe: dmfe_dynamic_reset() 0
[ 1724.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1724.844058] dmfe: dmfe_init_dm910x() 0
[ 1724.844164] dmfe: dmfe_parse_srom()  0
[ 1724.845107] dmfe: dmfe_descriptor_init() 0
[ 1724.845136] dmfe: send_filter_frame() 0
[ 1725.844009] dmfe: dmfe_timer() 0
[ 1728.844008] dmfe: dmfe_timer() 0
[ 1728.844016] eth0: Tx timeout - resetting
[ 1728.844018] dmfe: Dynamic Reset device 1
[ 1728.844021] dmfe: dmfe_dynamic_reset() 0
[ 1728.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1728.844055] dmfe: dmfe_init_dm910x() 0
[ 1728.844162] dmfe: dmfe_parse_srom()  0
[ 1728.845107] dmfe: dmfe_descriptor_init() 0
[ 1728.845135] dmfe: send_filter_frame() 0
[ 1729.844009] dmfe: dmfe_timer() 0
[ 1732.844009] dmfe: dmfe_timer() 0
[ 1732.844017] eth0: Tx timeout - resetting
[ 1732.844019] dmfe: Dynamic Reset device 1
[ 1732.844021] dmfe: dmfe_dynamic_reset() 0
[ 1732.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1732.844057] dmfe: dmfe_init_dm910x() 0
[ 1732.844165] dmfe: dmfe_parse_srom()  0
[ 1732.845110] dmfe: dmfe_descriptor_init() 0
[ 1732.845139] dmfe: send_filter_frame() 0
[ 1733.844009] dmfe: dmfe_timer() 0
[ 1736.844022] dmfe: dmfe_timer() 0
[ 1736.844030] eth0: Tx timeout - resetting
[ 1736.844032] dmfe: Dynamic Reset device 1
[ 1736.844034] dmfe: dmfe_dynamic_reset() 0
[ 1736.844051] dmfe: dmfe_free_rxbuffer() 0
[ 1736.844071] dmfe: dmfe_init_dm910x() 0
[ 1736.844177] dmfe: dmfe_parse_srom()  0
[ 1736.845120] dmfe: dmfe_descriptor_init() 0
[ 1736.845151] dmfe: send_filter_frame() 0
[ 1737.844010] dmfe: dmfe_timer() 0
[ 1740.844010] dmfe: dmfe_timer() 0
[ 1740.844018] eth0: Tx timeout - resetting
[ 1740.844020] dmfe: Dynamic Reset device 1
[ 1740.844022] dmfe: dmfe_dynamic_reset() 0
[ 1740.844039] dmfe: dmfe_free_rxbuffer() 0
[ 1740.844060] dmfe: dmfe_init_dm910x() 0
[ 1740.844166] dmfe: dmfe_parse_srom()  0
[ 1740.845109] dmfe: dmfe_descriptor_init() 0
[ 1740.845138] dmfe: send_filter_frame() 0
[ 1741.844010] dmfe: dmfe_timer() 0
[ 1744.844009] dmfe: dmfe_timer() 0
[ 1744.844017] eth0: Tx timeout - resetting
[ 1744.844019] dmfe: Dynamic Reset device 1
[ 1744.844021] dmfe: dmfe_dynamic_reset() 0
[ 1744.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1744.844056] dmfe: dmfe_init_dm910x() 0
[ 1744.844162] dmfe: dmfe_parse_srom()  0
[ 1744.845105] dmfe: dmfe_descriptor_init() 0
[ 1744.845135] dmfe: send_filter_frame() 0
[ 1745.844010] dmfe: dmfe_timer() 0
[ 1748.844008] dmfe: dmfe_timer() 0
[ 1748.844016] eth0: Tx timeout - resetting
[ 1748.844018] dmfe: Dynamic Reset device 1
[ 1748.844020] dmfe: dmfe_dynamic_reset() 0
[ 1748.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1748.844058] dmfe: dmfe_init_dm910x() 0
[ 1748.844164] dmfe: dmfe_parse_srom()  0
[ 1748.845107] dmfe: dmfe_descriptor_init() 0
[ 1748.845136] dmfe: send_filter_frame() 0
[ 1749.844009] dmfe: dmfe_timer() 0
[ 1752.844008] dmfe: dmfe_timer() 0
[ 1752.844016] eth0: Tx timeout - resetting
[ 1752.844018] dmfe: Dynamic Reset device 1
[ 1752.844020] dmfe: dmfe_dynamic_reset() 0
[ 1752.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1752.844057] dmfe: dmfe_init_dm910x() 0
[ 1752.844164] dmfe: dmfe_parse_srom()  0
[ 1752.845108] dmfe: dmfe_descriptor_init() 0
[ 1752.845137] dmfe: send_filter_frame() 0
[ 1753.844009] dmfe: dmfe_timer() 0
[ 1756.844008] dmfe: dmfe_timer() 0
[ 1756.844016] eth0: Tx timeout - resetting
[ 1756.844018] dmfe: Dynamic Reset device 1
[ 1756.844020] dmfe: dmfe_dynamic_reset() 0
[ 1756.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1756.844056] dmfe: dmfe_init_dm910x() 0
[ 1756.844162] dmfe: dmfe_parse_srom()  0
[ 1756.845107] dmfe: dmfe_descriptor_init() 0
[ 1756.845137] dmfe: send_filter_frame() 0
[ 1757.844010] dmfe: dmfe_timer() 0
[ 1760.844008] dmfe: dmfe_timer() 0
[ 1760.844016] eth0: Tx timeout - resetting
[ 1760.844018] dmfe: Dynamic Reset device 1
[ 1760.844020] dmfe: dmfe_dynamic_reset() 0
[ 1760.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1760.844058] dmfe: dmfe_init_dm910x() 0
[ 1760.844164] dmfe: dmfe_parse_srom()  0
[ 1760.845107] dmfe: dmfe_descriptor_init() 0
[ 1760.845136] dmfe: send_filter_frame() 0
[ 1761.844009] dmfe: dmfe_timer() 0
[ 1764.844008] dmfe: dmfe_timer() 0
[ 1764.844016] eth0: Tx timeout - resetting
[ 1764.844018] dmfe: Dynamic Reset device 1
[ 1764.844020] dmfe: dmfe_dynamic_reset() 0
[ 1764.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1764.844055] dmfe: dmfe_init_dm910x() 0
[ 1764.844161] dmfe: dmfe_parse_srom()  0
[ 1764.845104] dmfe: dmfe_descriptor_init() 0
[ 1764.845133] dmfe: send_filter_frame() 0
[ 1765.844009] dmfe: dmfe_timer() 0
[ 1768.844009] dmfe: dmfe_timer() 0
[ 1768.844017] eth0: Tx timeout - resetting
[ 1768.844019] dmfe: Dynamic Reset device 1
[ 1768.844021] dmfe: dmfe_dynamic_reset() 0
[ 1768.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1768.844058] dmfe: dmfe_init_dm910x() 0
[ 1768.844165] dmfe: dmfe_parse_srom()  0
[ 1768.845108] dmfe: dmfe_descriptor_init() 0
[ 1768.845137] dmfe: send_filter_frame() 0
[ 1769.844012] dmfe: dmfe_timer() 0
[ 1772.844013] dmfe: dmfe_timer() 0
[ 1772.844022] eth0: Tx timeout - resetting
[ 1772.844024] dmfe: Dynamic Reset device 1
[ 1772.844026] dmfe: dmfe_dynamic_reset() 0
[ 1772.844042] dmfe: dmfe_free_rxbuffer() 0
[ 1772.844062] dmfe: dmfe_init_dm910x() 0
[ 1772.844168] dmfe: dmfe_parse_srom()  0
[ 1772.845111] dmfe: dmfe_descriptor_init() 0
[ 1772.845139] dmfe: send_filter_frame() 0
[ 1773.844009] dmfe: dmfe_timer() 0
[ 1776.844008] dmfe: dmfe_timer() 0
[ 1776.844016] eth0: Tx timeout - resetting
[ 1776.844018] dmfe: Dynamic Reset device 1
[ 1776.844020] dmfe: dmfe_dynamic_reset() 0
[ 1776.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1776.844056] dmfe: dmfe_init_dm910x() 0
[ 1776.844163] dmfe: dmfe_parse_srom()  0
[ 1776.845111] dmfe: dmfe_descriptor_init() 0
[ 1776.845139] dmfe: send_filter_frame() 0
[ 1777.844009] dmfe: dmfe_timer() 0
[ 1780.844007] dmfe: dmfe_timer() 0
[ 1780.844015] eth0: Tx timeout - resetting
[ 1780.844017] dmfe: Dynamic Reset device 1
[ 1780.844020] dmfe: dmfe_dynamic_reset() 0
[ 1780.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1780.844055] dmfe: dmfe_init_dm910x() 0
[ 1780.844161] dmfe: dmfe_parse_srom()  0
[ 1780.845104] dmfe: dmfe_descriptor_init() 0
[ 1780.845134] dmfe: send_filter_frame() 0
[ 1781.844009] dmfe: dmfe_timer() 0
[ 1784.844008] dmfe: dmfe_timer() 0
[ 1784.844016] eth0: Tx timeout - resetting
[ 1784.844018] dmfe: Dynamic Reset device 1
[ 1784.844021] dmfe: dmfe_dynamic_reset() 0
[ 1784.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1784.844057] dmfe: dmfe_init_dm910x() 0
[ 1784.844164] dmfe: dmfe_parse_srom()  0
[ 1784.845107] dmfe: dmfe_descriptor_init() 0
[ 1784.845135] dmfe: send_filter_frame() 0
[ 1785.844009] dmfe: dmfe_timer() 0
[ 1788.844008] dmfe: dmfe_timer() 0
[ 1788.844016] eth0: Tx timeout - resetting
[ 1788.844018] dmfe: Dynamic Reset device 1
[ 1788.844020] dmfe: dmfe_dynamic_reset() 0
[ 1788.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1788.844056] dmfe: dmfe_init_dm910x() 0
[ 1788.844162] dmfe: dmfe_parse_srom()  0
[ 1788.845106] dmfe: dmfe_descriptor_init() 0
[ 1788.845135] dmfe: send_filter_frame() 0
[ 1789.844009] dmfe: dmfe_timer() 0
[ 1792.844009] dmfe: dmfe_timer() 0
[ 1792.844017] eth0: Tx timeout - resetting
[ 1792.844019] dmfe: Dynamic Reset device 1
[ 1792.844021] dmfe: dmfe_dynamic_reset() 0
[ 1792.844038] dmfe: dmfe_free_rxbuffer() 0
[ 1792.844059] dmfe: dmfe_init_dm910x() 0
[ 1792.844167] dmfe: dmfe_parse_srom()  0
[ 1792.845111] dmfe: dmfe_descriptor_init() 0
[ 1792.845140] dmfe: send_filter_frame() 0
[ 1793.844012] dmfe: dmfe_timer() 0
[ 1796.844020] dmfe: dmfe_timer() 0
[ 1796.844028] eth0: Tx timeout - resetting
[ 1796.844030] dmfe: Dynamic Reset device 1
[ 1796.844032] dmfe: dmfe_dynamic_reset() 0
[ 1796.844048] dmfe: dmfe_free_rxbuffer() 0
[ 1796.844067] dmfe: dmfe_init_dm910x() 0
[ 1796.844175] dmfe: dmfe_parse_srom()  0
[ 1796.845121] dmfe: dmfe_descriptor_init() 0
[ 1796.845150] dmfe: send_filter_frame() 0
[ 1797.844009] dmfe: dmfe_timer() 0
[ 1800.844008] dmfe: dmfe_timer() 0
[ 1800.844016] eth0: Tx timeout - resetting
[ 1800.844018] dmfe: Dynamic Reset device 1
[ 1800.844020] dmfe: dmfe_dynamic_reset() 0
[ 1800.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1800.844058] dmfe: dmfe_init_dm910x() 0
[ 1800.844164] dmfe: dmfe_parse_srom()  0
[ 1800.845108] dmfe: dmfe_descriptor_init() 0
[ 1800.845136] dmfe: send_filter_frame() 0
[ 1801.844010] dmfe: dmfe_timer() 0
[ 1804.844008] dmfe: dmfe_timer() 0
[ 1804.844016] eth0: Tx timeout - resetting
[ 1804.844018] dmfe: Dynamic Reset device 1
[ 1804.844020] dmfe: dmfe_dynamic_reset() 0
[ 1804.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1804.844056] dmfe: dmfe_init_dm910x() 0
[ 1804.844162] dmfe: dmfe_parse_srom()  0
[ 1804.845106] dmfe: dmfe_descriptor_init() 0
[ 1804.845134] dmfe: send_filter_frame() 0
[ 1805.844012] dmfe: dmfe_timer() 0
[ 1808.844008] dmfe: dmfe_timer() 0
[ 1808.844016] eth0: Tx timeout - resetting
[ 1808.844018] dmfe: Dynamic Reset device 1
[ 1808.844020] dmfe: dmfe_dynamic_reset() 0
[ 1808.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1808.844056] dmfe: dmfe_init_dm910x() 0
[ 1808.844163] dmfe: dmfe_parse_srom()  0
[ 1808.845107] dmfe: dmfe_descriptor_init() 0
[ 1808.845135] dmfe: send_filter_frame() 0
[ 1809.844009] dmfe: dmfe_timer() 0
[ 1812.844008] dmfe: dmfe_timer() 0
[ 1812.844016] eth0: Tx timeout - resetting
[ 1812.844018] dmfe: Dynamic Reset device 1
[ 1812.844020] dmfe: dmfe_dynamic_reset() 0
[ 1812.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1812.844057] dmfe: dmfe_init_dm910x() 0
[ 1812.844164] dmfe: dmfe_parse_srom()  0
[ 1812.845108] dmfe: dmfe_descriptor_init() 0
[ 1812.845137] dmfe: send_filter_frame() 0
[ 1813.844010] dmfe: dmfe_timer() 0
[ 1816.844008] dmfe: dmfe_timer() 0
[ 1816.844016] eth0: Tx timeout - resetting
[ 1816.844018] dmfe: Dynamic Reset device 1
[ 1816.844020] dmfe: dmfe_dynamic_reset() 0
[ 1816.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1816.844056] dmfe: dmfe_init_dm910x() 0
[ 1816.844162] dmfe: dmfe_parse_srom()  0
[ 1816.845106] dmfe: dmfe_descriptor_init() 0
[ 1816.845135] dmfe: send_filter_frame() 0
[ 1817.844009] dmfe: dmfe_timer() 0
[ 1820.844010] dmfe: dmfe_timer() 0
[ 1820.844018] eth0: Tx timeout - resetting
[ 1820.844020] dmfe: Dynamic Reset device 1
[ 1820.844022] dmfe: dmfe_dynamic_reset() 0
[ 1820.844038] dmfe: dmfe_free_rxbuffer() 0
[ 1820.844059] dmfe: dmfe_init_dm910x() 0
[ 1820.844165] dmfe: dmfe_parse_srom()  0
[ 1820.845108] dmfe: dmfe_descriptor_init() 0
[ 1820.845137] dmfe: send_filter_frame() 0
[ 1821.844009] dmfe: dmfe_timer() 0
[ 1823.912015] usb 1-4: new high speed USB device using ehci_hcd and address 4
[ 1824.065214] usb 1-4: configuration #1 chosen from 1 choice
[ 1824.089840] scsi5 : SCSI emulation for USB Mass Storage devices
[ 1824.091487] usb-storage: device found at 4
[ 1824.091491] usb-storage: waiting for device to settle before scanning
[ 1824.844008] dmfe: dmfe_timer() 0
[ 1824.844016] eth0: Tx timeout - resetting
[ 1824.844019] dmfe: Dynamic Reset device 1
[ 1824.844021] dmfe: dmfe_dynamic_reset() 0
[ 1824.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1824.844057] dmfe: dmfe_init_dm910x() 0
[ 1824.844163] dmfe: dmfe_parse_srom()  0
[ 1824.845107] dmfe: dmfe_descriptor_init() 0
[ 1824.845135] dmfe: send_filter_frame() 0
[ 1825.844012] dmfe: dmfe_timer() 0
[ 1828.844009] dmfe: dmfe_timer() 0
[ 1828.844017] eth0: Tx timeout - resetting
[ 1828.844019] dmfe: Dynamic Reset device 1
[ 1828.844021] dmfe: dmfe_dynamic_reset() 0
[ 1828.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1828.844058] dmfe: dmfe_init_dm910x() 0
[ 1828.844165] dmfe: dmfe_parse_srom()  0
[ 1828.845108] dmfe: dmfe_descriptor_init() 0
[ 1828.845135] dmfe: send_filter_frame() 0
[ 1829.088180] usb-storage: device scan complete
[ 1829.088666] scsi 5:0:0:0: Direct-Access     SanDisk  Cruzer Mini      0.4  PQ: 0 ANSI: 2
[ 1829.090776] sd 5:0:0:0: [sdb] 1000944 512-byte hardware sectors: (512 MB/488 MiB)
[ 1829.127049] sd 5:0:0:0: [sdb] Write Protect is off
[ 1829.127054] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1829.127057] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1829.131028] sd 5:0:0:0: [sdb] 1000944 512-byte hardware sectors: (512 MB/488 MiB)
[ 1829.131517] sd 5:0:0:0: [sdb] Write Protect is off
[ 1829.131521] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1829.131524] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1829.131530]  sdb: sdb1
[ 1829.133060] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 1829.133155] sd 5:0:0:0: Attached scsi generic sg3 type 0
[ 1829.844017] dmfe: dmfe_timer() 0
[ 1831.276586] dmfe: dmfe_get_stats 0
[ 1832.844008] dmfe: dmfe_timer() 0
[ 1832.844016] eth0: Tx timeout - resetting
[ 1832.844019] dmfe: Dynamic Reset device 1
[ 1832.844021] dmfe: dmfe_dynamic_reset() 0
[ 1832.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1832.844056] dmfe: dmfe_init_dm910x() 0
[ 1832.844163] dmfe: dmfe_parse_srom()  0
[ 1832.845107] dmfe: dmfe_descriptor_init() 0
[ 1832.845137] dmfe: send_filter_frame() 0
[ 1833.844008] dmfe: dmfe_timer() 0
[ 1836.844009] dmfe: dmfe_timer() 0
[ 1836.844016] eth0: Tx timeout - resetting
[ 1836.844019] dmfe: Dynamic Reset device 1
[ 1836.844021] dmfe: dmfe_dynamic_reset() 0
[ 1836.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1836.844059] dmfe: dmfe_init_dm910x() 0
[ 1836.844165] dmfe: dmfe_parse_srom()  0
[ 1836.845112] dmfe: dmfe_descriptor_init() 0
[ 1836.845141] dmfe: send_filter_frame() 0
[ 1837.844013] dmfe: dmfe_timer() 0
[ 1840.844007] dmfe: dmfe_timer() 0
[ 1840.844015] eth0: Tx timeout - resetting
[ 1840.844017] dmfe: Dynamic Reset device 1
[ 1840.844019] dmfe: dmfe_dynamic_reset() 0
[ 1840.844035] dmfe: dmfe_free_rxbuffer() 0
[ 1840.844057] dmfe: dmfe_init_dm910x() 0
[ 1840.844164] dmfe: dmfe_parse_srom()  0
[ 1840.845110] dmfe: dmfe_descriptor_init() 0
[ 1840.845138] dmfe: send_filter_frame() 0
[ 1841.844012] dmfe: dmfe_timer() 0
[ 1844.844008] dmfe: dmfe_timer() 0
[ 1844.844016] eth0: Tx timeout - resetting
[ 1844.844018] dmfe: Dynamic Reset device 1
[ 1844.844020] dmfe: dmfe_dynamic_reset() 0
[ 1844.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1844.844057] dmfe: dmfe_init_dm910x() 0
[ 1844.844163] dmfe: dmfe_parse_srom()  0
[ 1844.845106] dmfe: dmfe_descriptor_init() 0
[ 1844.845135] dmfe: send_filter_frame() 0
[ 1845.844008] dmfe: dmfe_timer() 0
[ 1848.844008] dmfe: dmfe_timer() 0
[ 1848.844016] eth0: Tx timeout - resetting
[ 1848.844018] dmfe: Dynamic Reset device 1
[ 1848.844020] dmfe: dmfe_dynamic_reset() 0
[ 1848.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1848.844059] dmfe: dmfe_init_dm910x() 0
[ 1848.844166] dmfe: dmfe_parse_srom()  0
[ 1848.845110] dmfe: dmfe_descriptor_init() 0
[ 1848.845138] dmfe: send_filter_frame() 0
[ 1849.844010] dmfe: dmfe_timer() 0
[ 1852.844012] dmfe: dmfe_timer() 0
[ 1852.844020] eth0: Tx timeout - resetting
[ 1852.844023] dmfe: Dynamic Reset device 1
[ 1852.844025] dmfe: dmfe_dynamic_reset() 0
[ 1852.844041] dmfe: dmfe_free_rxbuffer() 0
[ 1852.844059] dmfe: dmfe_init_dm910x() 0
[ 1852.844166] dmfe: dmfe_parse_srom()  0
[ 1852.845109] dmfe: dmfe_descriptor_init() 0
[ 1852.845137] dmfe: send_filter_frame() 0
[ 1853.844011] dmfe: dmfe_timer() 0
[ 1856.844022] dmfe: dmfe_timer() 0
[ 1856.844030] eth0: Tx timeout - resetting
[ 1856.844032] dmfe: Dynamic Reset device 1
[ 1856.844034] dmfe: dmfe_dynamic_reset() 0
[ 1856.844051] dmfe: dmfe_free_rxbuffer() 0
[ 1856.844071] dmfe: dmfe_init_dm910x() 0
[ 1856.844178] dmfe: dmfe_parse_srom()  0
[ 1856.845121] dmfe: dmfe_descriptor_init() 0
[ 1856.845150] dmfe: send_filter_frame() 0
[ 1857.844010] dmfe: dmfe_timer() 0
[ 1860.844008] dmfe: dmfe_timer() 0
[ 1860.844016] eth0: Tx timeout - resetting
[ 1860.844019] dmfe: Dynamic Reset device 1
[ 1860.844021] dmfe: dmfe_dynamic_reset() 0
[ 1860.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1860.844059] dmfe: dmfe_init_dm910x() 0
[ 1860.844165] dmfe: dmfe_parse_srom()  0
[ 1860.845108] dmfe: dmfe_descriptor_init() 0
[ 1860.845137] dmfe: send_filter_frame() 0
[ 1861.844011] dmfe: dmfe_timer() 0
[ 1864.844017] dmfe: dmfe_timer() 0
[ 1864.844025] eth0: Tx timeout - resetting
[ 1864.844028] dmfe: Dynamic Reset device 1
[ 1864.844030] dmfe: dmfe_dynamic_reset() 0
[ 1864.844046] dmfe: dmfe_free_rxbuffer() 0
[ 1864.844068] dmfe: dmfe_init_dm910x() 0
[ 1864.844174] dmfe: dmfe_parse_srom()  0
[ 1864.845117] dmfe: dmfe_descriptor_init() 0
[ 1864.845146] dmfe: send_filter_frame() 0
[ 1865.844010] dmfe: dmfe_timer() 0
[ 1868.844009] dmfe: dmfe_timer() 0
[ 1868.844017] eth0: Tx timeout - resetting
[ 1868.844019] dmfe: Dynamic Reset device 1
[ 1868.844021] dmfe: dmfe_dynamic_reset() 0
[ 1868.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1868.844058] dmfe: dmfe_init_dm910x() 0
[ 1868.844164] dmfe: dmfe_parse_srom()  0
[ 1868.845107] dmfe: dmfe_descriptor_init() 0
[ 1868.845135] dmfe: send_filter_frame() 0
[ 1869.844009] dmfe: dmfe_timer() 0
[ 1872.844008] dmfe: dmfe_timer() 0
[ 1872.844016] eth0: Tx timeout - resetting
[ 1872.844018] dmfe: Dynamic Reset device 1
[ 1872.844020] dmfe: dmfe_dynamic_reset() 0
[ 1872.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1872.844056] dmfe: dmfe_init_dm910x() 0
[ 1872.844163] dmfe: dmfe_parse_srom()  0
[ 1872.845107] dmfe: dmfe_descriptor_init() 0
[ 1872.845136] dmfe: send_filter_frame() 0
[ 1873.844009] dmfe: dmfe_timer() 0
[ 1876.844007] dmfe: dmfe_timer() 0
[ 1876.844015] eth0: Tx timeout - resetting
[ 1876.844017] dmfe: Dynamic Reset device 1
[ 1876.844020] dmfe: dmfe_dynamic_reset() 0
[ 1876.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1876.844058] dmfe: dmfe_init_dm910x() 0
[ 1876.844165] dmfe: dmfe_parse_srom()  0
[ 1876.845108] dmfe: dmfe_descriptor_init() 0
[ 1876.845135] dmfe: send_filter_frame() 0
[ 1877.844011] dmfe: dmfe_timer() 0
[ 1880.844010] dmfe: dmfe_timer() 0
[ 1880.844018] eth0: Tx timeout - resetting
[ 1880.844020] dmfe: Dynamic Reset device 1
[ 1880.844023] dmfe: dmfe_dynamic_reset() 0
[ 1880.844039] dmfe: dmfe_free_rxbuffer() 0
[ 1880.844060] dmfe: dmfe_init_dm910x() 0
[ 1880.844166] dmfe: dmfe_parse_srom()  0
[ 1880.845109] dmfe: dmfe_descriptor_init() 0
[ 1880.845138] dmfe: send_filter_frame() 0
[ 1881.844009] dmfe: dmfe_timer() 0
[ 1884.844011] dmfe: dmfe_timer() 0
[ 1884.844019] eth0: Tx timeout - resetting
[ 1884.844021] dmfe: Dynamic Reset device 1
[ 1884.844023] dmfe: dmfe_dynamic_reset() 0
[ 1884.844040] dmfe: dmfe_free_rxbuffer() 0
[ 1884.844061] dmfe: dmfe_init_dm910x() 0
[ 1884.844167] dmfe: dmfe_parse_srom()  0
[ 1884.845111] dmfe: dmfe_descriptor_init() 0
[ 1884.845138] dmfe: send_filter_frame() 0
[ 1885.844011] dmfe: dmfe_timer() 0
[ 1888.844011] dmfe: dmfe_timer() 0
[ 1888.844019] eth0: Tx timeout - resetting
[ 1888.844021] dmfe: Dynamic Reset device 1
[ 1888.844023] dmfe: dmfe_dynamic_reset() 0
[ 1888.844040] dmfe: dmfe_free_rxbuffer() 0
[ 1888.844059] dmfe: dmfe_init_dm910x() 0
[ 1888.844165] dmfe: dmfe_parse_srom()  0
[ 1888.845109] dmfe: dmfe_descriptor_init() 0
[ 1888.845137] dmfe: send_filter_frame() 0
[ 1889.844010] dmfe: dmfe_timer() 0
[ 1892.844012] dmfe: dmfe_timer() 0
[ 1892.844019] eth0: Tx timeout - resetting
[ 1892.844021] dmfe: Dynamic Reset device 1
[ 1892.844024] dmfe: dmfe_dynamic_reset() 0
[ 1892.844040] dmfe: dmfe_free_rxbuffer() 0
[ 1892.844061] dmfe: dmfe_init_dm910x() 0
[ 1892.844167] dmfe: dmfe_parse_srom()  0
[ 1892.845112] dmfe: dmfe_descriptor_init() 0
[ 1892.845141] dmfe: send_filter_frame() 0
[ 1893.844012] dmfe: dmfe_timer() 0
[ 1896.844011] dmfe: dmfe_timer() 0
[ 1896.844018] eth0: Tx timeout - resetting
[ 1896.844020] dmfe: Dynamic Reset device 1
[ 1896.844022] dmfe: dmfe_dynamic_reset() 0
[ 1896.844038] dmfe: dmfe_free_rxbuffer() 0
[ 1896.844060] dmfe: dmfe_init_dm910x() 0
[ 1896.844167] dmfe: dmfe_parse_srom()  0
[ 1896.845111] dmfe: dmfe_descriptor_init() 0
[ 1896.845140] dmfe: send_filter_frame() 0
[ 1897.844011] dmfe: dmfe_timer() 0
[ 1900.844007] dmfe: dmfe_timer() 0
[ 1900.844014] eth0: Tx timeout - resetting
[ 1900.844016] dmfe: Dynamic Reset device 1
[ 1900.844018] dmfe: dmfe_dynamic_reset() 0
[ 1900.844035] dmfe: dmfe_free_rxbuffer() 0
[ 1900.844057] dmfe: dmfe_init_dm910x() 0
[ 1900.844163] dmfe: dmfe_parse_srom()  0
[ 1900.845108] dmfe: dmfe_descriptor_init() 0
[ 1900.845136] dmfe: send_filter_frame() 0
[ 1901.844010] dmfe: dmfe_timer() 0
[ 1904.844007] dmfe: dmfe_timer() 0
[ 1904.844015] eth0: Tx timeout - resetting
[ 1904.844017] dmfe: Dynamic Reset device 1
[ 1904.844019] dmfe: dmfe_dynamic_reset() 0
[ 1904.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1904.844055] dmfe: dmfe_init_dm910x() 0
[ 1904.844162] dmfe: dmfe_parse_srom()  0
[ 1904.845106] dmfe: dmfe_descriptor_init() 0
[ 1904.845134] dmfe: send_filter_frame() 0
[ 1905.844010] dmfe: dmfe_timer() 0
[ 1908.844008] dmfe: dmfe_timer() 0
[ 1908.844015] eth0: Tx timeout - resetting
[ 1908.844017] dmfe: Dynamic Reset device 1
[ 1908.844020] dmfe: dmfe_dynamic_reset() 0
[ 1908.844036] dmfe: dmfe_free_rxbuffer() 0
[ 1908.844057] dmfe: dmfe_init_dm910x() 0
[ 1908.844163] dmfe: dmfe_parse_srom()  0
[ 1908.845106] dmfe: dmfe_descriptor_init() 0
[ 1908.845134] dmfe: send_filter_frame() 0
[ 1909.844010] dmfe: dmfe_timer() 0
[ 1912.844008] dmfe: dmfe_timer() 0
[ 1912.844016] eth0: Tx timeout - resetting
[ 1912.844018] dmfe: Dynamic Reset device 1
[ 1912.844020] dmfe: dmfe_dynamic_reset() 0
[ 1912.844037] dmfe: dmfe_free_rxbuffer() 0
[ 1912.844058] dmfe: dmfe_init_dm910x() 0
[ 1912.844165] dmfe: dmfe_parse_srom()  0
[ 1912.845109] dmfe: dmfe_descriptor_init() 0
[ 1912.845138] dmfe: send_filter_frame() 0
[ 1913.844013] dmfe: dmfe_timer() 0
[ 1916.844021] dmfe: dmfe_timer() 0
[ 1916.844029] eth0: Tx timeout - resetting
[ 1916.844031] dmfe: Dynamic Reset device 1
[ 1916.844033] dmfe: dmfe_dynamic_reset() 0
[ 1916.844049] dmfe: dmfe_free_rxbuffer() 0
[ 1916.844071] dmfe: dmfe_init_dm910x() 0
[ 1916.844178] dmfe: dmfe_parse_srom()  0
[ 1916.845124] dmfe: dmfe_descriptor_init() 0
[ 1916.845153] dmfe: send_filter_frame() 0
[ 1917.844010] dmfe: dmfe_timer() 0

```

---

### Post by mpokrywka on 2009-11-07
Looks that driver is not working properly (Tx timeout errors).
Maybe try forcing link settings:
**sudo rmmod dmfe**
**sudo modprobe dmfe mode=5** # if under windows connection is 100Mb/s
**sudo modprobe dmfe mode=4** # if under windows connection is 10Mb/s

---

### Post by mpokrywka on 2009-11-07
Could you also post output of:
**lspci -nn**

so we would know which exactly Davicom card we are talking about...

---

### Post by SatishP on 2009-11-09
Apologies for the delay in responding...

> **mpokrywka said:**
> Looks that driver is not working properly (Tx timeout errors).
Maybe try forcing link settings:
**sudo rmmod dmfe**
**sudo modprobe dmfe mode=5** # if under windows connection is 100Mb/s
**sudo modprobe dmfe mode=4** # if under windows connection is 10Mb/s

Unfortunately, this too had no effect

> **mpokrywka said:**
> Could you also post output of:
**lspci -nn**

so we would know which exactly Davicom card we are talking about...

Here's the output:
```
00:00.0 Host bridge [0600]: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub [8086:2580] (rev 0e)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller [8086:2582] (rev 0e)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 05)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 05)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 05)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 05)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d5)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640] (rev 05)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 05)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller [8086:2651] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 05)
01:02.0 Ethernet controller [0200]: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet [1282:9102] (rev 31)

```

---

### Post by SatishP on 2009-11-10
I guess everyone is out of ideas :confused:

There's a bug reported in Launchpad and I added myself sometime earlier but there hasn't been any update on that yet. 
```
https://bugs.launchpad.net/ubuntu/+bug/435244
```I guess I will have to wait for someone to work on it #-o but I am not hopeful. I know this is a pretty old card and people wouldn't want to waste time on this.

I was planning to move to Ubuntu but this scares the hell out of me; if I am not able to get my ethernet card working I can surely expect far bigger issues down the line. I probably would hold on to my 'Windoze'.

In any case, thanks to everyone who tried to help me. I honestly appreciate your effort.

---

### Post by mpokrywka on 2009-11-12
Sorry for delay. I, in fact, was curious and checked driver source code at:
[http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.31.y.git;a=blob;f=drivers/net/tulip/dmfe.c](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.31.y.git;a=blob;f=drivers/net/tulip/dmfe.c)
to see if there are any notes about possible problems... Unfortunately, I didn't infer anything usable.

Your problem is definitely some bug in dmfe driver.

I think you should report this bug directly on [http://bugzilla.kernel.org/](http://bugzilla.kernel.org/)
because real kernel network developers would be best to answer. They may have more ideas how to debug problems.

Your card may be old, but Davicom seems to be still alive (judging by website), and maybe network developers can get required technical manuals from them.

---

