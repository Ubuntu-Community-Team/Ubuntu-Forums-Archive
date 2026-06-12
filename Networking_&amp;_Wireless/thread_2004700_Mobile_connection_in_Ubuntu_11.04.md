---
title: "Mobile connection in Ubuntu 11.04"
date: 2012-06-16
forum: Networking &amp; Wireless
---

### Post by GirishSharma on 2012-06-16
Hello,

On this home PC machine P4 2GB RAM, I am struggling to have mobile connection on Ubuntu 11.04 Natty Narwhal using Nokia C5-03 device and BSNL ISP.  The same device and ISP are working fine on windows XP.  Here it is terminal cut and paste for your reference :

```

**1st Terminal :**
girish@girish-desktop:~$ uname -r
2.6.38-8-generic
girish@girish-desktop:~$ uname -a
Linux girish-desktop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
girish@girish-desktop:~$ sudo service network-manager stop
[sudo] password for girish: 
network-manager stop/waiting
girish@girish-desktop:~$ ps -A | grep modem
  442 ?        00:00:00 modem-manager
girish@girish-desktop:~$ sudo kill 442
girish@girish-desktop:~$ ps -A | grep modem
girish@girish-desktop:~$ NM_PPP_DEBUG=1
girish@girish-desktop:~$ sudo NetworkManager --no-daemon
NetworkManager[1804]: <info> NetworkManager (version 0.8.3.998) is starting...
NetworkManager[1804]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
NetworkManager[1804]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
NetworkManager[1804]: <info> modem-manager is now available
NetworkManager[1804]: <info> monitoring kernel firmware directory '/lib/firmware'.
NetworkManager[1804]:    SCPlugin-Ifupdown: init!
NetworkManager[1804]:    SCPlugin-Ifupdown: update_system_hostname
NetworkManager[1804]:    SCPluginIfupdown: management mode: unmanaged
NetworkManager[1804]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:01.0/net/eth0, iface: eth0)
NetworkManager[1804]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:01.0/net/eth0, iface: eth0): no ifupdown configuration found.
NetworkManager[1804]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
NetworkManager[1804]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
NetworkManager[1804]:    SCPlugin-Ifupdown: end _init.
NetworkManager[1804]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
NetworkManager[1804]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
NetworkManager[1804]:    Ifupdown: get unmanaged devices count: 0
NetworkManager[1804]:    SCPlugin-Ifupdown: (147234392) ... get_connections.
NetworkManager[1804]:    SCPlugin-Ifupdown: (147234392) ... get_connections (managed=false): return empty list.
NetworkManager[1804]:    keyfile: parsing BSNL*CellOne New GPRS*3G 1 ... 
NetworkManager[1804]:    keyfile:     read connection 'BSNL/CellOne New GPRS/3G 1'
NetworkManager[1804]:    keyfile: parsing MTS MBlaze connection 1 ... 
NetworkManager[1804]:    keyfile:     read connection 'MTS MBlaze connection 1'
NetworkManager[1804]:    Ifupdown: get unmanaged devices count: 0
NetworkManager[1804]: <info> WiFi enabled by radio killswitch; enabled by state file
NetworkManager[1804]: <info> WWAN enabled by radio killswitch; enabled by state file
NetworkManager[1804]: <info> WiMAX enabled by radio killswitch; enabled by state file
NetworkManager[1804]: <info> Networking is enabled by state file
NetworkManager[1804]: <info> (eth0): carrier is OFF
NetworkManager[1804]: <info> (eth0): new Ethernet device (driver: '8139too' ifindex: 2)
NetworkManager[1804]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
NetworkManager[1804]: <info> (eth0): now managed
NetworkManager[1804]: <info> (eth0): device state change: 1 -> 2 (reason 2)
NetworkManager[1804]: <info> (eth0): bringing up device.
NetworkManager[1804]: <info> (eth0): preparing device.
NetworkManager[1804]: <info> (eth0): deactivating device (reason: 2).
NetworkManager[1804]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:01:01.0/net/eth0
/sbin/ifup: interface lo already configured
NetworkManager[1804]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
NetworkManager[1804]: <warn> (ttyACM0): failed to look up interface index
NetworkManager[1804]: <info> (ttyACM0): new GSM device (driver: 'cdc_acm' ifindex: -1)
NetworkManager[1804]: <info> (ttyACM0): exported as /org/freedesktop/NetworkManager/Devices/1
NetworkManager[1804]: <info> (ttyACM0): now managed
NetworkManager[1804]: <info> (ttyACM0): device state change: 1 -> 2 (reason 2)
NetworkManager[1804]: <info> (ttyACM0): deactivating device (reason: 2).
NetworkManager[1804]: <info> (ttyACM0): device state change: 2 -> 3 (reason 0)
NetworkManager[1804]: <info> Activation (ttyACM0) starting connection 'BSNL/CellOne New GPRS/3G 1'
NetworkManager[1804]: <info> (ttyACM0): device state change: 3 -> 4 (reason 0)
NetworkManager[1804]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager[1804]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started...
NetworkManager[1804]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager[1804]: <info> WWAN now enabled by management service
NetworkManager[1804]: <info> Activation (ttyACM0) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager[1804]: <info> Activation (ttyACM0) Stage 2 of 5 (Device Configure) starting...
NetworkManager[1804]: <info> (ttyACM0): device state change: 4 -> 5 (reason 0)
NetworkManager[1804]: <info> Activation (ttyACM0) Stage 2 of 5 (Device Configure) successful.
NetworkManager[1804]: <info> Activation (ttyACM0) Stage 3 of 5 (IP Configure Start) scheduled.
NetworkManager[1804]: <info> Activation (ttyACM0) Stage 2 of 5 (Device Configure) complete.
NetworkManager[1804]: <info> Activation (ttyACM0) Stage 3 of 5 (IP Configure Start) started...
NetworkManager[1804]: <info> (ttyACM0): device state change: 5 -> 7 (reason 0)
NetworkManager[1804]: <info> starting PPP connection
NetworkManager[1804]: <info> pppd started with pid 1878
NetworkManager[1804]: <info> Activation (ttyACM0) Stage 3 of 5 (IP Configure Start) complete.
/usr/sbin/pppd: In file /etc/ppp/options: unrecognized option '/dev/ttyUSB3'
NetworkManager[1804]: <warn> pppd pid 1878 exited with error: pppd options error
NetworkManager[1804]: <info> (ttyACM0): device state change: 7 -> 9 (reason 5)
NetworkManager[1804]: <info> Marking connection 'BSNL/CellOne New GPRS/3G 1' invalid.
NetworkManager[1804]: <warn> Activation (ttyACM0) failed.
NetworkManager[1804]: <info> (ttyACM0): device state change: 9 -> 3 (reason 0)
NetworkManager[1804]: <info> (ttyACM0): deactivating device (reason: 0).
NetworkManager[1804]: <info> Activation (ttyACM0) starting connection 'BSNL/CellOne New GPRS/3G 1'
NetworkManager[1804]: <info> (ttyACM0): device state change: 3 -> 4 (reason 0)
NetworkManager[1804]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager[1804]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started...
NetworkManager[1804]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager[1804]: <warn> GSM connection failed: (32) Serial command timed out
NetworkManager[1804]: <info> (ttyACM0): device state change: 4 -> 9 (reason 1)
NetworkManager[1804]: <info> Marking connection 'BSNL/CellOne New GPRS/3G 1' invalid.
NetworkManager[1804]: <warn> Activation (ttyACM0) failed.
NetworkManager[1804]: <info> (ttyACM0): device state change: 9 -> 3 (reason 0)
NetworkManager[1804]: <info> (ttyACM0): deactivating device (reason: 0).
^CNetworkManager[1804]: <info> caught signal 2, shutting down normally.
NetworkManager[1804]: <info> (eth0): now unmanaged
NetworkManager[1804]: <info> (eth0): device state change: 2 -> 1 (reason 36)
NetworkManager[1804]: <info> (eth0): cleaning up...
NetworkManager[1804]: <info> (eth0): taking down device.
NetworkManager[1804]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
NetworkManager[1804]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
NetworkManager[1804]: <info> (ttyACM0): now unmanaged
NetworkManager[1804]: <info> (ttyACM0): device state change: 3 -> 1 (reason 36)
NetworkManager[1804]: <info> (ttyACM0): cleaning up...
NetworkManager[1804]: <info> (ttyACM0): taking down device.
NetworkManager[1804]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
NetworkManager[1804]: <info> exiting (success)

NetworkManager[1804]: <info> Activation (ttyACM0) starting connection 'BSNL/CellOne New GPRS/3G 1'
NetworkManager[1804]: <info> (ttyACM0): device state change: 3 -> 4 (reason 0)
NetworkManager[1804]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager[1804]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started...
NetworkManager[1804]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager[1804]: <warn> GSM connection failed: (32) Serial command timed out
NetworkManager[1804]: <info> (ttyACM0): device state change: 4 -> 9 (reason 1)
NetworkManager[1804]: <info> Marking connection 'BSNL/CellOne New GPRS/3G 1' invalid.
NetworkManager[1804]: <warn> Activation (ttyACM0) failed.
NetworkManager[1804]: <info> (ttyACM0): device state change: 9 -> 3 (reason 0)
NetworkManager[1804]: <info> (ttyACM0): deactivating device (reason: 0).

**2nd Terminal :**
girish@girish-desktop:~$ sudo modem-manager --debug
[sudo] password for girish: 
modem-manager[1798]: <debug> [1339849552.027327] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- '~\255}#\192!}!} } }2}#}$\192#}!}$}%\220}"}&} }*} } g}%~'
modem-manager[1798]: <debug> [1339849555.027327] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- '~\255}#\192!}!} } }2}#}$\192#}!}$}%\220}"}&} }*} } g}%~'
modem-manager[1798]: <debug> [1339849558.027321] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- '~\255}#\192!}!} } }2}#}$\192#}!}$}%\220}"}&} }*} } g}%~'
modem-manager[1798]: <debug> [1339849561.027312] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- '~\255}#\192!}!} } }2}#}$\192#}!}$}%\220}"}&} }*} } g}%~'
modem-manager[1798]: <debug> [1339849564.027332] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- '~\255}#\192!}!} } }2}#}$\192#}!}$}%\220}"}&} }*} } g}%~'
modem-manager[1798]: <debug> [1339849572.153435] [mm-generic-gsm.c:4362] simple_connect(): (ttyACM0): number => "*99#"
modem-manager[1798]: <debug> [1339849572.153578] [mm-generic-gsm.c:4362] simple_connect(): (ttyACM0): network_mode => 0
modem-manager[1798]: <debug> [1339849572.153625] [mm-generic-gsm.c:4362] simple_connect(): (ttyACM0): apn => "bsnlnet"
modem-manager[1798]: <debug> [1339849572.153666] [mm-generic-gsm.c:4362] simple_connect(): (ttyACM0): allowed_mode => 0
modem-manager[1798]: <debug> [1339849572.153737] [mm-generic-gsm.c:4251] simple_state_machine(): (ttyACM0): simple connect state 0
modem-manager[1798]: <debug> [1339849572.153918] [mm-generic-gsm.c:4251] simple_state_machine(): (ttyACM0): simple connect state 2
modem-manager[1798]: <debug> [1339849572.154128] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): --> 'AT+CREG?<CR>'
modem-manager[1798]: <debug> [1339849581.989730] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): --> 'AT+CSQ<CR>'
modem-manager[1798]: <debug> [1339849584.986920] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): --> 'AT+CGREG?<CR>'
modem-manager[1798]: <debug> [1339849603.985563] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): --> 'AT+CSQ<CR>'
modem-manager[1798]: <debug> [1339849633.999365] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): --> 'AT+CSQ<CR>'
modem-manager[1798]: <debug> [1339849663.999358] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): --> 'AT+CSQ<CR>'
modem-manager[1798]: <debug> [1339849693.995371] [mm-at-serial-port.c:298] debug_log(): (ttyACM0): --> 'AT+CSQ<CR>'

**3rd Terminal :**
girish@girish-desktop:~$ sudo lspci
[sudo] password for girish: 
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:02.0 Modem: PCTel Inc HSP56 MicroModem (rev 03)
girish@girish-desktop:~$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
	Subsystem: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
	Flags: bus master, fast devsel, latency 0
	Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [e4] Vendor Specific Information: Len=05 <?>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01) (prog-if 00 [VGA controller])
	Subsystem: Intel Corporation Device 5641
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Memory at ffa80000 (32-bit, non-prefetchable) [size=512K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [d0] Power Management version 1
	Kernel driver in use: i915
	Kernel modules: intelfb, i915

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Device 5641
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at e800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Device 5641
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at e880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Device 5641
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ec00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: Intel Corporation Device 5641
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at ffa7fc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=0080
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: ff800000-ff8fffff
	Prefetchable memory behind bridge: e6a00000-e6afffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Intel Corporation Device 5641
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Memory at 80000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
	Subsystem: Intel Corporation Device 5641
	Flags: medium devsel, IRQ 3
	I/O ports at e000 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
	Subsystem: Intel Corporation Device 0208
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at e400 [size=256]
	I/O ports at e080 [size=64]
	Memory at ffa7f800 (32-bit, non-prefetchable) [size=512]
	Memory at ffa7f400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
	Flags: bus master, medium devsel, latency 32, IRQ 22
	I/O ports at d800 [size=256]
	Memory at ff8ffc00 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at ff8e0000 [disabled] [size=64K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp

01:02.0 Modem: PCTel Inc HSP56 MicroModem (rev 03) (prog-if 00 [Generic])
	Subsystem: PCTel Inc Device 1002
	Flags: bus master, stepping, medium devsel, latency 32, IRQ 18
	Memory at ff8fe000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at d400 [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: serial

girish@girish-desktop:~$ sudo lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 01)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
01:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
01:02.0 Modem [0703]: PCTel Inc HSP56 MicroModem [134d:2189] (rev 03)
girish@girish-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:80:48:65:86:05  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

girish@girish-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:80:48:65:86:05  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

girish@girish-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

girish@girish-desktop:~$ lsmod
Module                  Size  Used by
rndis_wlan             28293  0 
cfg80211              156212  1 rndis_wlan
rndis_host             13521  1 rndis_wlan
cdc_phonet             12853  0 
cdc_ether              13032  1 rndis_host
cdc_acm                22150  2 
phonet                 29296  1 cdc_phonet
usbnet                 25175  3 rndis_wlan,rndis_host,cdc_ether
binfmt_misc            13213  1 
pci_stub               12550  1 
vboxpci                22892  0 
vboxnetadp             13348  0 
vboxnetflt             27225  0 
snd_intel8x0           33213  2 
vboxdrv               251892  3 vboxpci,vboxnetadp,vboxnetflt
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
i915                  450944  2 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12849  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 i915
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
serio_raw              12990  0 
drm                   180037  2 i915,drm_kms_helper
parport_pc             32111  1 
shpchp                 32345  0 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
8139too                23208  0 
8139cp                 22497  0 
girish@girish-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: eth0
       version: 10
       serial: 00:80:48:65:86:05
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:22 ioport:d800(size=256) memory:ff8ffc00-ff8ffcff memory:ff8e0000-ff8effff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
girish@girish-desktop:~$ 
girish@girish-desktop:~$ sudo lshw -C network
PCI (sysfs)  

^Cgirish@girish-desktop:~$ rfkill list
girish@girish-desktop:~$ 

```

Kindly tell me how do I establish mobile connection.  Since, I am not able to connect the internet, so I think sudo apt-get will not work, because it requires internet.

Kindly help me.

Thanks and Regards
Girish Sharma

---

### Post by GirishSharma on 2012-06-18
Any update please.

Regards
Girish Sharma

---

