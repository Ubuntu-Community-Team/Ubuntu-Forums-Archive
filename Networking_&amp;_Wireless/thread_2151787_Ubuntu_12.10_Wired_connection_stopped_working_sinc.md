---
title: "Ubuntu 12.10 Wired connection stopped working since update"
date: 2013-06-05
forum: Networking &amp; Wireless
---

### Post by ImTom on 2013-06-05
I'm running Ubuntu 12.10 with kernel 3.5.0-32.  I recently installed an update which, I believe, brought my system to 3.5.0-32.  Since the installation of this update my wired network connection has stopped working.  What I'm seeing is the network icon strobing while the system is searching for, I believe, the dhcp server.  After a minute or two, there is a popup stating "Wired network disconnected - you are now offline".  I tried the sanity check of switching ethernet cable with a working system to no avail.

I've included details below.  Please let me know if there is other pertinent info that I need to provide.

```

ifconfig

webert1@toms-file-server:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:29:36:fb:21  
          inet6 addr: fe80::21f:29ff:fe36:fb21/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36255 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:9600815 (9.6 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:89638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7353956 (7.3 MB)  TX bytes:7353956 (7.3 MB)

```

```

webert1@toms-file-server:~$ nm-tool


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             disconnected
  Default:           no
  HW Address:        00:1F:29:36:FB:21


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on



``````




webert1@toms-file-server:~$ lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:2a72]
    Kernel driver in use: forcedeth


```


```

sudo lshw
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:1f:29:36:fb:21
          size: 1000000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=1Gbit/s
          resources: irq:43 memory:fe02d000-fe02dfff ioport:f000(size=8)



```

---

### Post by varunendra on 2013-06-06
Welcome to the forums ImTom! :)
> **ImTom said:**
> ```

webert1@toms-file-server:~$ nm-tool
...
    Speed:           **1000 Mb/s**


  Wired Properties
    Carrier:         **on**

```

Physical connection looks good. Please try setting IPv6 to "Ignore" in Network Manager, try to connect, and post back outputs of -
```
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/network/interfaces
dmesg | grep -iE 'dhclient|forcedeth|eth|network'
cat /var/log/syslog | grep -iE 'dhclient|forcedeth|eth|network'
```

Have you tried a manually assigned IP address yet?

---

### Post by ImTom on 2013-06-06
Varun

Setting IPv6 to "ignore" had no effect.

Here's the other info you requested:

```

webert1@toms-file-server:~$ cat /var/lib/NetworkManager/NetworkManager.state
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```

```

webert1@toms-file-server:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


```


```

webert1@toms-file-server:~$ dmesg | grep -iE 'dhclient|forcedeth|eth|network'
[    0.226780] ACPI Error: Method parse/execution failed [\_SB_.MEM_._CRS] (Node ffff880074abe668), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[    0.226788] ACPI Error: Method execution failed [\_SB_.MEM_._CRS] (Node ffff880074abe668), AE_AML_BUFFER_LIMIT (20120320/uteval-103)
[    0.579203] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.579442] forcedeth 0000:00:07.0: setting latency timer to 64
[    1.104786] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1f:29:36:fb:21
[    1.104792] forcedeth 0000:00:07.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[   16.749056] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.942887] type=1400 audit(1370305034.977:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=489 comm="apparmor_parser"
[   16.943980] type=1400 audit(1370305034.977:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=489 comm="apparmor_parser"
[   16.944267] type=1400 audit(1370305034.981:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=489 comm="apparmor_parser"
[   17.804478] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.965552] forcedeth 0000:00:07.0: irq 43 for MSI/MSI-X
[   17.965585] forcedeth 0000:00:07.0: eth0: MSI enabled
[44938.225836] Modules linked in: parport_pc rfcomm bnep bluetooth ppdev snd_hda_codec_realtek nvidia(PO) kvm edac_core edac_mce_amd k8temp serio_raw snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device joydev mac_hid snd usblp soundcore snd_page_alloc i2c_nforce2 lp parport hid_generic usbhid hid forcedeth sata_nv
[69770.683254] forcedeth 0000:00:07.0: irq 43 for MSI/MSI-X
[69770.683329] forcedeth 0000:00:07.0: eth0: MSI enabled

```

```

This is just a snippet from the log file.  This snippet repeats itself.


Jun  6 07:54:14 toms-file-server dhclient: Internet Systems Consortium DHCP Client 4.2.4
Jun  6 07:54:14 toms-file-server dhclient: Copyright 2004-2012 Internet Systems Consortium.
Jun  6 07:54:14 toms-file-server dhclient: All rights reserved.
Jun  6 07:54:14 toms-file-server dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun  6 07:54:14 toms-file-server dhclient: 
Jun  6 07:54:14 toms-file-server NetworkManager[874]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jun  6 07:54:14 toms-file-server dhclient: Listening on LPF/eth0/00:1f:29:36:fb:21
Jun  6 07:54:14 toms-file-server dhclient: Sending on   LPF/eth0/00:1f:29:36:fb:21
Jun  6 07:54:14 toms-file-server dhclient: Sending on   Socket/fallback
Jun  6 07:54:14 toms-file-server dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jun  6 07:54:17 toms-file-server dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jun  6 07:54:24 toms-file-server dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Jun  6 07:54:37 toms-file-server dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Jun  6 07:54:49 toms-file-server dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Jun  6 07:54:59 toms-file-server NetworkManager[874]: <warn> (eth0): DHCPv4 request timed out.
Jun  6 07:54:59 toms-file-server NetworkManager[874]: <info> (eth0): canceled DHCP transaction, DHCP client pid 16169
Jun  6 07:54:59 toms-file-server NetworkManager[874]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Jun  6 07:54:59 toms-file-server NetworkManager[874]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Jun  6 07:54:59 toms-file-server NetworkManager[874]: <info> (eth0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Jun  6 07:54:59 toms-file-server NetworkManager[874]: <warn> Activation (eth0) failed for connection 'Auto Ethernet'
Jun  6 07:54:59 toms-file-server NetworkManager[874]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Jun  6 07:54:59 toms-file-server NetworkManager[874]: <info> (eth0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jun  6 07:54:59 toms-file-server NetworkManager[874]: <info> (eth0): deactivating device (reason 'none') [0]
Jun  6 07:55:02 toms-file-server NetworkManager[874]: <info> Auto-activating connection 'Auto Ethernet'.
Jun  6 07:55:02 toms-file-server NetworkManager[874]: <info> Activation (eth0) starting connection 'Auto Ethernet'
Jun  6 07:55:02 toms-file-server NetworkManager[874]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun  6 07:55:02 toms-file-server NetworkManager[874]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  6 07:55:02 toms-file-server NetworkManager[874]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun  6 07:55:02 toms-file-server NetworkManager[874]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun  6 07:55:02 toms-file-server NetworkManager[874]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun  6 07:55:02 toms-file-server NetworkManager[874]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun  6 07:55:02 toms-file-server NetworkManager[874]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  6 07:55:02 toms-file-server NetworkManager[874]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun  6 07:55:02 toms-file-server NetworkManager[874]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  6 07:55:02 toms-file-server NetworkManager[874]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun  6 07:55:02 toms-file-server NetworkManager[874]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun  6 07:55:02 toms-file-server NetworkManager[874]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun  6 07:55:02 toms-file-server NetworkManager[874]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun  6 07:55:02 toms-file-server NetworkManager[874]: <info> dhclient started with pid 16181
Jun  6 07:55:02 toms-file-server NetworkManager[874]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.

```


Regarding manually setting the ip address.  Currently my Ubuntu box is wired to my router.  I set up my dhcp server on my router so that when it sees the mac address of my  Ubuntu box, it allocates a fixed ip address.  Thus my Ubuntu box will always have the same ip address.  Everything else on my network uses dhcp.  I do this because the Ubuntu box is my file server, so the other systems on the network will know where the file server is.  This scheme has worked well for quite some time.  

I'm not sure how to set up my Ubuntu box to a fixed ip.  Will this conflict with what the scheme I have configured on the router?

I should have issued the warning that I'm fairly new to Linux & Ubuntu.

---

### Post by varunendra on 2013-06-06
> **ImTom said:**
> I should have issued the warning that I'm fairly new to Linux & Ubuntu.
:)
Unless someone says "I'm proficient in Ubuntu/Linux", I already assume that they're new ;)

As you must have noticed in syslog yourself, the dhcp request is failing. Accordingly, double-check your DHCP settings in the router, maybe give it a power cycle (power off > wait 2-4 minutes > power on again, do the same with the PC as well, simultaneously), then try again.

To assign manual IP (if required), make sure the DHCP pool in the router is set such that it does not cover the IP that you want to assign to this computer. Then in network manager, choose "Method" to "Manual" under IPv4 tab for your wired connection (Auto Ethernet). Assign the IP, subnet, gateway, DNS as applicable (enter IP, press 'Enter' to actually save it). Save settings > close > retry to connect.

To try a manual IP 'temporarily', try -
```
sudo ifconfig eth0 down
sudo ifconfig eth0 xx.xx.xx.xx
```
where xx.xx.xx.xx is the IP address you want to assign (make sure it is not in DHCP pool and is not already assigned to another device on the network). This will be a temporary IP and will be reset to current settings after reboot. It may confirm whether a manual IP is going to help or not.

So far, the dhcp failure is the only problem I can see (besides the ACPI error, which I don't think is related).

---

### Post by ImTom on 2013-06-06
Varun

Resetting my router did not resolve the problem.

I setup a static ip and now have an "Active Network Connection".

However, I can't ping my router's address 10.0.1.1.  I get "Destination Host Unreachable".  I am able to ping the router from my MacBook.


Here's updated info

```

webert1@toms-file-server:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:29:36:fb:21  
          inet addr:10.0.1.199  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:29ff:fe36:fb21/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:23167 (23.1 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20816 (20.8 KB)  TX bytes:20816 (20.8 KB)

```


```

Jun  6 11:14:08 toms-file-server NetworkManager[2292]: <info> NetworkManager (version 0.9.6.0) is starting...
Jun  6 11:14:08 toms-file-server NetworkManager[2292]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jun  6 11:14:08 toms-file-server NetworkManager[2292]: <info> WEXT support is enabled
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> DNS: loaded plugin dnsmasq
Jun  6 11:14:09 toms-file-server NetworkManager[2292]:    SCPlugin-Ifupdown: init!
Jun  6 11:14:09 toms-file-server NetworkManager[2292]:    SCPlugin-Ifupdown: update_system_hostname
Jun  6 11:14:09 toms-file-server NetworkManager[2292]:    SCPluginIfupdown: management mode: unmanaged
Jun  6 11:14:09 toms-file-server NetworkManager[2292]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:07.0/net/eth0, iface: eth0)
Jun  6 11:14:09 toms-file-server NetworkManager[2292]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:07.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun  6 11:14:09 toms-file-server NetworkManager[2292]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun  6 11:14:09 toms-file-server NetworkManager[2292]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun  6 11:14:09 toms-file-server NetworkManager[2292]:    SCPlugin-Ifupdown: end _init.
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun  6 11:14:09 toms-file-server NetworkManager[2292]:    Ifupdown: get unmanaged devices count: 0
Jun  6 11:14:09 toms-file-server NetworkManager[2292]:    SCPlugin-Ifupdown: (34034848) ... get_connections.
Jun  6 11:14:09 toms-file-server NetworkManager[2292]:    SCPlugin-Ifupdown: (34034848) ... get_connections (managed=false): return empty list.
Jun  6 11:14:09 toms-file-server NetworkManager[2292]:    keyfile: parsing Auto Ethernet ... 
Jun  6 11:14:09 toms-file-server NetworkManager[2292]:    keyfile:     read connection 'Auto Ethernet'
Jun  6 11:14:09 toms-file-server NetworkManager[2292]:    Ifupdown: get unmanaged devices count: 0
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> modem-manager is now available
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> WiFi enabled by radio killswitch; enabled by state file
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> WWAN enabled by radio killswitch; enabled by state file
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> Networking is enabled by state file
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <warn> failed to allocate link cache: (-10) Operation not supported
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> (eth0): carrier is ON
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> (eth0): now managed
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'connection-assumed') [10 20 41]
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> (eth0): preparing device.
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> Activation (eth0) starting connection 'Auto Ethernet'
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> (eth0): device state change: unavailable -> ip-config (reason 'none') [20 70 0]
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> DNS: starting dnsmasq...
**Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <error> [1370535249.231317] [nm-dns-dnsmasq.c:390] update(): dnsmasq not available on the bus, can't update servers.**
**Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <error> [1370535249.231355] [nm-dns-dnsmasq.c:392] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name**
**Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <warn> DNS: plugin dnsmasq update failed**
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> ((null)): writing resolv.conf to /sbin/resolvconf
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> Policy set 'Auto Ethernet' (eth0) as default for IPv4 routing and DNS.
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> Activation (eth0) successful, device activated.
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <warn> dnsmasq appeared on DBus: :1.55
Jun  6 11:14:09 toms-file-server NetworkManager[2292]: <info> ((null)): writing resolv.conf to /sbin/resolvconf

```


Please see the notice the error concerning dnsmasq.

---

### Post by varunendra on 2013-06-06
> **ImTom said:**
> I setup a static ip and now have an "Active Network Connection".

However, I can't ping my router's address 10.0.1.1.  I get "Destination Host Unreachable".  I am able to ping the router from my MacBook.
Did you make sure the subnet (255.255.255.0) is the same as your router and the rest of the network?
Can you ping your MacBook from your Ubuntu machine or vice-versa?

Please also post outputs of -
```
nm-tool
sudo cat "/etc/NetworkManager/system-connections/Auto Ethernet"
```

---

### Post by ImTom on 2013-06-06
> **varunendra said:**
> Did you make sure the subnet (255.255.255.0) is the same as your router and the rest of the network?
Can you ping your MacBook from your Ubuntu machine or vice-versa?

Please also post outputs of -
```
nm-tool
sudo cat "/etc/NetworkManager/system-connections/Auto Ethernet"
```


Double and triple checked the subnet mask.  it is the same as on the MacBook.

I can NOT ping the Ubuntu box from the MacBook.  I can NOT ping the MacBook from the Ubuntu box.  The Ubuntu box is an island unto itself.  :confused:

Here's the additional info you asked for.

```

webert1@toms-file-server:~$ nm-tool


NetworkManager Tool


State: connected (global)


- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        00:1F:29:36:FB:21


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         10.0.1.199
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.1.1


    DNS:             10.0.1.1

```


```
webert1@toms-file-server:~$ sudo cat "/etc/NetworkManager/system-connections/Auto Ethernet"
[sudo] password for webert1: 
[802-3-ethernet]
duplex=full
mac-address=00:1F:29:36:FB:21


[connection]
id=Auto Ethernet
uuid=c14ea34f-2936-42cb-a396-f7a52944004b
type=802-3-ethernet
timestamp=1370291416


[ipv6]
method=ignore


[ipv4]
method=manual
dns=10.0.1.1;
addresses1=10.0.1.199;24;10.0.1.1;




```

---

### Post by varunendra on 2013-06-06
> **ImTom said:**
> I recently installed an update which, I believe, brought my system to 3.5.0-32.  Since the installation of this update my wired network connection has stopped working.
Since everything else seems in place in current 'configuration' within the OS, I'd suggest to try booting with the older kernel and see if the connection still works there.

To choose an older kernel to boot with, you may have to press any key at the splash screen during boot-up to bring up the GRUB menu if it doesn't show up by default.

While running the older kernel, also run the **dmesg | grep -iE 'dhclient|forcedeth|eth|network'** command and see if the ACPI errors or any other errors appear in it.

There are a few other things we can try but they would be purely based on random guess, while this one may rule out a few.

---

### Post by ImTom on 2013-06-07
> **varunendra said:**
> Since everything else seems in place in current 'configuration' within the OS, I'd suggest to try booting with the older kernel and see if the connection still works there.

To choose an older kernel to boot with, you may have to press any key at the splash screen during boot-up to bring up the GRUB menu if it doesn't show up by default.

While running the older kernel, also run the **dmesg | grep -iE 'dhclient|forcedeth|eth|network'** command and see if the ACPI errors or any other errors appear in it.

There are a few other things we can try but they would be purely based on random guess, while this one may rule out a few.


I wish I had better news to report.  I tried 3.5.0-31 & 3.5.0-25.  I encountered the same problem.  I tried to go back further, -23 & -22, but the desktop did not display properly.

Here's the output from dmesg


```

with kernel 3.5.0-31 generic


webert1@toms-file-server:~$ dmesg | grep -iE 'dhcpclient|forcedeth|eth|network'
[    0.226784] ACPI Error: Method parse/execution failed [\_SB_.MEM_._CRS] (Node ffff880074abe668), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[    0.226792] ACPI Error: Method execution failed [\_SB_.MEM_._CRS] (Node ffff880074abe668), AE_AML_BUFFER_LIMIT (20120320/uteval-103)
[    0.568135] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.568383] forcedeth 0000:00:07.0: setting latency timer to 64
[    1.092728] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1f:29:36:fb:21
[    1.092732] forcedeth 0000:00:07.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[   15.064615] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.316184] type=1400 audit(1370607357.355:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=471 comm="apparmor_parser"
[   19.291454] forcedeth 0000:00:07.0: irq 43 for MSI/MSI-X
[   19.291489] forcedeth 0000:00:07.0: eth0: MSI enabled
[   19.437545] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

```



```

with kernel 3.5.0-25 generic


webert1@toms-file-server:~$ dmesg | grep -iE 'dhcpclient|forcedeth|eth|network'
[    0.226720] ACPI Error: Method parse/execution failed [\_SB_.MEM_._CRS] (Node ffff880074abe668), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[    0.226727] ACPI Error: Method execution failed [\_SB_.MEM_._CRS] (Node ffff880074abe668), AE_AML_BUFFER_LIMIT (20120320/uteval-103)
[    0.572664] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.572885] forcedeth 0000:00:07.0: setting latency timer to 64
[    1.096730] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1f:29:36:fb:21
[    1.096736] forcedeth 0000:00:07.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[   15.069938] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.282864] type=1400 audit(1370607818.319:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=436 comm="apparmor_parser"
[   19.230948] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.352670] forcedeth 0000:00:07.0: irq 43 for MSI/MSI-X
[   19.352704] forcedeth 0000:00:07.0: eth0: MSI enabled

```

---

### Post by varunendra on 2013-06-07
So that suggests that at least the problem is not with the updated version of the driver.

A few things to try/double-check -

[INDENT]- Did you try the automatic configuration with previous kernel as it was before? Try it if you didn't. Oh, and you don't need to go too far back, just the previously working one :)

- Make sure the IP that you have manually assigned (10.0.1.199) does not fall within the IP range of the DHCP in the router, and the subnet (255.255.255.0) is same in it (it can be different even if IP is same, so double-check).

- Check the firewall settings in the router, disable it just for a test if is enabled. Same for any other settings (like custom routing rules, filters etc.) that may interfere.

- Check the firewall status in Ubuntu ("**sudo ufw status**" command). By default, it should be "Inactive". Although it is one of the least possible issues.

- If the above are okay, then try resetting the BIOS. Actually this is what I am suspecting the most after DHCP configuration errors.[/INDENT]

And.. do you have a cross-cable available? If yes, you can try connecting directly to your MacBook (you'll have to manually assign IPs, say, 10.0.1.198 and 10.0.1.199, in both in that case) to see if they can communicate that way.

---

### Post by ImTom on 2013-06-07
> **varunendra said:**
> So that suggests that at least the problem is not with the updated version of the driver.

A few things to try/double-check -[INDENT]- Did you try the automatic configuration with previous kernel as it was before? Try it if you didn't. Oh, and you don't need to go too far back, just the previously working one :)

- Make sure the IP that you have manually assigned (10.0.1.199) does not fall within the IP range of the DHCP in the router, and the subnet (255.255.255.0) is same in it (it can be different even if IP is same, so double-check).

- Check the firewall settings in the router, disable it just for a test if is enabled. Same for any other settings (like custom routing rules, filters etc.) that may interfere.

- Check the firewall status in Ubuntu ("**sudo ufw status**" command). By default, it should be "Inactive". Although it is one of the least possible issues.

- If the above are okay, then try resetting the BIOS. Actually this is what I am suspecting the most after DHCP configuration errors.[/INDENT]

And.. do you have a cross-cable available? If yes, you can try connecting directly to your MacBook (you'll have to manually assign IPs, say, 10.0.1.198 and 10.0.1.199, in both in that case) to see if they can communicate that way.


1)  I went back to previous kernel and tried the automatic configuration - it exhibited the same problem.

2)  The ip I was using, 10.0.1.199, was in the DHCIP range (2..200).  :oops:   I tried 10.0.1.201 - same problem.  Verified that net mask is 255.255.255.0.

3)  Checked router settings.  There isn't the ability to disable the firewall.  BTw, I'm using an Apple AirPort router.

4)  The firewall status of Ubuntu is inactive

5)  Double-checked BIOS settings.  Exited and rebooted.  Not sure what you mean by "resetting the BIOS".

6)  I do have a cross-cable and gave it a try.  This was interesting.  When I pinged from my MacBook to the Ubuntu box, all ping requests timed out.  A ifconfig on the Ubuntu box showed "RX bytes:0".  When I ping from Ubuntu box to my MacBook, the ping requests timed-out, but via Mac network utility, the receive packet counter was increasing with each ping from Ubuntu.  An ifconfig on Ubuntu again showed "RX bytes:0".  So, it appears that the Ubuntu box is transmitting, but not receiving or discarding what is receiving.


An aside question.  Does Ubuntu automatically run a DHCP server?  When I connected my MacBook to the Ubuntu box, I had DHCP still enabled on the MacBook and the MacBook was assigned an ip address.  Thought that was strange.:confused:

---

### Post by varunendra on 2013-06-07
> **ImTom said:**
> 5)  Double-checked BIOS settings.  Exited and rebooted.  Not sure what you mean by "resetting the BIOS".
See in the "Save & Exit" (or similar that your BIOS have) section of the BIOS. There should be a couple of options to "Load Defaults" or "Load optimized defaults". They are meant to restore BIOS settings to factory defaults.

A nice general guide on resetting BIOS : [http://www.wikihow.com/Reset-Your-BIOS](http://www.wikihow.com/Reset-Your-BIOS)

> 6)  I do have a cross-cable and gave it a try.  This was interesting.  When I pinged from my MacBook to the Ubuntu box, all ping requests timed out.  A ifconfig on the Ubuntu box showed "RX bytes:0".  When I ping from Ubuntu box to my MacBook, the ping requests timed-out, but via Mac network utility, the receive packet counter was increasing with each ping from Ubuntu.  An ifconfig on Ubuntu again showed "RX bytes:0".  So, it appears that the Ubuntu box is transmitting, but not receiving or discarding what is receiving.
Was there also a record for tx bytes in the mac? Was it growing? If not, then maybe it wasn't replying anything for Ubuntu box to receive. Try pinging from MacBook to Ubuntu and see if anything significant happens. And you can use **System-Monitor > Resources** tab in Ubuntu to watch live network usage stats.

> An aside question.  Does Ubuntu automatically run a DHCP server?  When I connected my MacBook to the Ubuntu box, I had DHCP still enabled on the MacBook and the MacBook was assigned an ip address.  Thought that was strange.:confused:
No, only DHCP client is installed and enabled by default in Ubuntu.

DHCP assigned addresses are leased for a specific period (in min/seconds, usually equal to a couple of days). As far as I know, an OS keeps this IP in cache and does not make another request unless this lease period has expired or there is IP conflict or otherwise a new IP is required (like network/domain change). So it may have been the leased IP that was used as it was neither expired nor had conflict. But I'm open for corrections :)

---

### Post by ImTom on 2013-06-07
> **varunendra said:**
> See in the "Save & Exit" (or similar that your BIOS have) section of the BIOS. There should be a couple of options to "Load Defaults" or "Load optimized defaults". They are meant to restore BIOS settings to factory defaults.

A nice general guide on resetting BIOS : [http://www.wikihow.com/Reset-Your-BIOS](http://www.wikihow.com/Reset-Your-BIOS)


Haven't tried this yet.  

> 
Was there also a record for tx bytes in the mac? Was it growing? If not, then maybe it wasn't replying anything for Ubuntu box to receive. Try pinging from MacBook to Ubuntu and see if anything significant happens. And you can use **System-Monitor > Resources** tab in Ubuntu to watch live network usage stats.


Yes there is.  I watched activity monitor for both Mac and Ubuntu.  On the Mac I see the transmit counter increment when pinging the Ubuntu box - on the Ubuntu box there is NO receive activity.  When pinging from Ubuntu, on the Mac I see transmit and receive counters increment - on the Ubuntu box, the send activity goes up, but there is NO receive activity.

---

### Post by ImTom on 2013-06-07
Varun

On a whim I tried booting from two Unbuntu install DVDs, 12.04 and a 12.10.  In both cases, networking failed to function in the same manner as the installed version of Ubuntu.  

Do you supposed the onboard LAN controller is on the fritz??

---

### Post by varunendra on 2013-06-07
> **ImTom said:**
> Varun

On a whim I tried booting from two Unbuntu install DVDs, 12.04 and a 12.10.  In both cases, networking failed to function in the same manner as the installed version of Ubuntu.  

Do you supposed the onboard LAN controller is on the fritz??

I suspect BIOS.

I am noticing quite some rise in wired connection issues these days on the forums. And strangely enough, when all the sanity check is good, a BIOS reset seems to magically fix most (but not all) of the issues. It appears that some yet-to-be-identified bug has crept into the newer updates - interfering with basic BIOS settings. Although not yet sure if it is (if it is a bug indeed) a bug in Linux updates or the BIOS programs, because I know that most of the manufacturers don't implement ACPI standards properly in their boards. Maybe that or something similar in NICs could be causing this issues.

In any case, BIOS is now a big suspect in your case. Just reset it !

---

### Post by ImTom on 2013-06-08
> **varunendra said:**
> I suspect BIOS.

I am noticing quite some rise in wired connection issues these days on the forums. And strangely enough, when all the sanity check is good, a BIOS reset seems to magically fix most (but not all) of the issues. It appears that some yet-to-be-identified bug has crept into the newer updates - interfering with basic BIOS settings. Although not yet sure if it is (if it is a bug indeed) a bug in Linux updates or the BIOS programs, because I know that most of the manufacturers don't implement ACPI standards properly in their boards. Maybe that or something similar in NICs could be causing this issues.

In any case, BIOS is now a big suspect in your case. Just reset it !


I reset the BIOS to factory defaults via the BIOS setup utility at boot time.  This had NO affect on the problem.  :(

I did some digging and discovered there is an update to the BIOS, but the installer is a Windows executable.  :(

---

### Post by Hadaka on 2013-06-08
Hi, I noticed your eth0 has RX=0 on all the
outputs you posted,yet it is also showing full duplex.
```
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:36255 errors:0 dropped:0 overruns:0 carrier:0
configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full

```
just out of curiosity, try bypassing the router and plug directly into the modem
with a different cable if you have one and see if your eth0 comes to life.
thanks.

---

### Post by Hadaka on 2013-06-08
Also to verify the card is not defective, try as a temp
measure, with normal -modem--router--pc    configuration
setting your IPv4 like the attached.
[ATTACH=CONFIG]243664[/ATTACH]
boot and see if it connects.
 you may want to save a screenshot of your current configuration
before making these changes.

---

### Post by ImTom on 2013-06-13
Sorry for tardiness in replying to the latest posts to this thread.  Life got in the way.  :)

I have solved the problem by installing a D-LINK DGE-530T NIC and disabling the onboard ethernet.  The 530T working out of the box, Ubuntu recognized it upon start-up and smooth sailing ever since.

Though I'm happy to have my Ubuntu box back up, I'm a bit unsatisfied in not knowing why the onboard ethernet went on the fritz.  I guess I'll probably never know.

A big thank you!! to everyone who posted their suggestions and tips, especially Varun.  This was my first venture posting to the Ubuntu Forum.  I really appreciate everyone's help.

Thanks all,
Tom

---

