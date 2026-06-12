---
title: "Hang on resume from sleep (networkmanager?)"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by ikkus42 on 2009-01-18
Hardy installation on AMD 64 Dell Inspiron 1501 is hanging intermittently on resume from sleep.  I think it might have something to do with the network manager.  

When it hangs on startup from sleep , syslog looks like this:
on sleep:
```

...
Jan 18 14:36:31 no NetworkManager: <info>  Going to sleep. 
Jan 18 14:36:31 no vmnetBridge: RTM_NEWLINK: name:eth0 index:8 flags:0x00001002 
Jan 18 14:36:31 no vmnetBridge: Can't remove interface eth0 8 (does not exist). 
Jan 18 14:36:31 no dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 8266
Jan 18 14:36:31 no dhclient: killed old client process, removed PID file
Jan 18 14:36:31 no kernel: [25177.895620] bridge-wlan0: disabling the bridge
Jan 18 14:36:31 no vmnetBridge: RTM_NEWLINK: name:wlan0 index:7 flags:0x00011003 
Jan 18 14:36:31 no vmnetBridge: Stopped bridge wlan0 to virtual network 0. 
Jan 18 14:36:31 no kernel: [25177.926248] bridge-wlan0: down
Jan 18 14:36:31 no kernel: [25177.926583] bridge-wlan0: detached
Jan 18 14:36:31 no vmnetBridge: RTM_NEWLINK: name:wlan0 index:7 flags:0x00001003 
Jan 18 14:36:31 no vmnetBridge: Can't remove interface wlan0 7 (does not exist). 
Jan 18 14:36:31 no dhclient: DHCPRELEASE on wlan0 to 192.168.1.254 port 67
Jan 18 14:36:31 no vmnetBridge: RTM_NEWLINK: name:wlan0 index:7 flags:0x00001002 
Jan 18 14:36:31 no vmnetBridge: Can't remove interface wlan0 7 (does not exist). 
Jan 18 14:36:31 no avahi-daemon[5065]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan 18 14:36:31 no avahi-daemon[5065]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.69.
Jan 18 14:36:31 no avahi-daemon[5065]: Withdrawing address record for fe80::21d:60ff:feb0:a1cc on wlan0.
Jan 18 14:36:31 no avahi-daemon[5065]: Withdrawing address record for 192.168.1.69 on wlan0.
Jan 18 14:36:32 no kernel: [25178.562954] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 18 14:36:32 no vmnetBridge: RTM_NEWLINK: name:wlan0 index:7 flags:0x00001003 
Jan 18 14:36:32 no vmnetBridge: Can't remove interface wlan0 7 (does not exist). 
Jan 18 14:36:33 no vmnetBridge: RTM_DELLINK: name:eth0 index:8 flags:0x00001002 
Jan 18 14:36:33 no vmnetBridge: Can't remove interface eth0 8 (does not exist). 
Jan 18 14:36:33 no NetworkManager: <debug> [1232289393.468246] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_1c_23
_a9_2f_f0'). 
Jan 18 14:36:33 no NetworkManager: <info>  Deactivating device eth0. 
Jan 18 14:36:33 no kernel: [25179.881388] ACPI: PCI interrupt for device 0000:08:00.0 disabled
Jan 18 14:36:33 no NetworkManager: <debug> [1232289393.622820] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/ssb__null_')
. 
Jan 18 14:36:33 no NetworkManager: <debug> [1232289393.622918] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/ssb__null_')
. 
Jan 18 14:36:33 no vmnetBridge: RTM_NEWLINK: name:wlan0 index:7 flags:0x00001002 
Jan 18 14:36:33 no vmnetBridge: Can't remove interface wlan0 7 (does not exist). 
Jan 18 14:36:33 no vmnetBridge: RTM_DELLINK: name:wlan0 index:7 flags:0x00001002 
Jan 18 14:36:33 no vmnetBridge: Can't remove interface wlan0 7 (does not exist). 
Jan 18 14:36:33 no NetworkManager: <debug> [1232289393.668320] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_1d_60_b0_a1_cc'). 
Jan 18 14:36:33 no NetworkManager: <info>  Deactivating device wlan0. 
Jan 18 14:36:33 no kernel: [25180.081091] ndiswrapper: device wlan0 removed
...

```

and on resume:
```

...
Jan 18 14:48:31 no kernel: [    4.700599] PM: Finishing wakeup.
Jan 18 14:48:31 no kernel: [    4.700601] Restarting tasks ... done.
Jan 18 14:48:32 no gnome-power-manager: (mwood) Resuming computer
Jan 18 14:48:32 no NetworkManager: <info>  Waking up from sleep. 

```

and then it hangs and I have to kill it.

my network config looks like this:
```

$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:1d:60:b0:a1:cc
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. ip=192.168.1.69 latency=0 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:a9:2f:f0
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s

```

I'm not sure if it's the fault of the network manager, because otherwise network is working fine.  But any time my system hangs, there is a notice from network manager or dhcdbd nearby.  Any suggestions how to confirm or rule it out?

Thanks all.

---

### Post by ikkus42 on 2009-01-18
A successful sleep/resume looks like this:

sleep:
```

...
Jan 18 17:13:42 no NetworkManager: <info>  Going to sleep. 
Jan 18 17:13:42 no vmnetBridge: RTM_NEWLINK: name:eth0 index:8 flags:0x00001002 
Jan 18 17:13:42 no vmnetBridge: Can't remove interface eth0 8 (does not exist). 
Jan 18 17:13:42 no kernel: [ 8062.251017] bridge-wlan0: disabling the bridge
Jan 18 17:13:42 no dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 8137
Jan 18 17:13:42 no dhclient: killed old client process, removed PID file
Jan 18 17:13:43 no kernel: [ 8062.273172] bridge-wlan0: down
Jan 18 17:13:43 no vmnetBridge: RTM_NEWLINK: name:wlan0 index:7 flags:0x00011003 
Jan 18 17:13:43 no vmnetBridge: Stopped bridge wlan0 to virtual network 0. 
Jan 18 17:13:43 no kernel: [ 8062.273509] bridge-wlan0: detached
Jan 18 17:13:43 no vmnetBridge: RTM_NEWLINK: name:wlan0 index:7 flags:0x00001003 
Jan 18 17:13:43 no vmnetBridge: Can't remove interface wlan0 7 (does not exist). 
Jan 18 17:13:43 no dhclient: DHCPRELEASE on wlan0 to 192.168.1.254 port 67
Jan 18 17:13:43 no avahi-daemon[4990]: Withdrawing address record for 192.168.1.69 on wlan0.
Jan 18 17:13:43 no avahi-daemon[4990]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.69.
Jan 18 17:13:43 no avahi-daemon[4990]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan 18 17:13:43 no dhcdbd:  dhclient 8137 down (9) but si_code == 0 and releasing==0 !
Jan 18 17:13:43 no vmnetBridge: RTM_NEWLINK: name:wlan0 index:7 flags:0x00001002 
Jan 18 17:13:43 no vmnetBridge: Can't remove interface wlan0 7 (does not exist). 
Jan 18 17:13:43 no avahi-daemon[4990]: Withdrawing address record for fe80::21d:60ff:feb0:a1cc on wlan0.
Jan 18 17:13:44 no vmnetBridge: RTM_DELLINK: name:eth0 index:8 flags:0x00001002 
Jan 18 17:13:44 no vmnetBridge: Can't remove interface eth0 8 (does not exist). 
Jan 18 17:13:44 no NetworkManager: <debug> [1232298824.089861] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_1c_23_a9_2f_f0'). 
Jan 18 17:13:44 no NetworkManager: <info>  Deactivating device eth0. 
Jan 18 17:13:44 no kernel: [ 8063.376862] ACPI: PCI interrupt for device 0000:08:00.0 disabled
Jan 18 17:13:44 no vmnetBridge: RTM_DELLINK: name:wlan0 index:7 flags:0x00001002 
Jan 18 17:13:44 no vmnetBridge: Can't remove interface wlan0 7 (does not exist). 
Jan 18 17:13:44 no kernel: [ 8063.448739] ndiswrapper: device wlan0 removed
Jan 18 17:13:44 no kernel: [ 8063.448761] ACPI: PCI interrupt for device 0000:05:00.0 disabled
Jan 18 17:13:44 no kernel: [ 8063.448907] usbcore: deregistering interface driver ndiswrapper
Jan 18 17:13:44 no NetworkManager: <debug> [1232298824.279412] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/ssb__null_'). 
Jan 18 17:13:44 no NetworkManager: <debug> [1232298824.279505] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/ssb__null_'). 
Jan 18 17:13:44 no NetworkManager: <debug> [1232298824.279540] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_1d_60_b0_a1_cc'). 
Jan 18 17:13:44 no NetworkManager: <info>  Deactivating device wlan0. 
Jan 18 17:13:44 no NetworkManager: <WARN>  nm_device_802_11_wireless_get_mode(): error getting card mode on wlan0: No such device 
...

```

on resume:
```

...
Jan 18 17:17:48 no kernel: [    4.595183] Restarting tasks ... done.
Jan 18 17:17:48 no gnome-power-manager: (mwood) Resuming computer
Jan 18 17:17:48 no NetworkManager: <info>  Waking up from sleep. 
Jan 18 17:17:51 no anacron[7065]: Anacron 2.3 started on 2009-01-18
Jan 18 17:17:51 no anacron[7065]: Normal exit (0 jobs run)
Jan 18 17:17:52 no kernel: [    8.437711] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Jan 18 17:17:52 no kernel: [    8.472080] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
Jan 18 17:17:52 no kernel: [    8.473884] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Jan 18 17:17:52 no kernel: [    8.474149] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Jan 18 17:17:52 no kernel: [    8.474190] PCI: Setting latency timer of device 0000:05:00.0 to 64
Jan 18 17:17:52 no kernel: [    8.477545] ndiswrapper: using IRQ 18
Jan 18 17:17:52 no vmnetBridge: RTM_NEWLINK: name:wlan0 index:9 flags:0x00001002 
Jan 18 17:17:52 no vmnetBridge: Can't remove interface wlan0 9 (does not exist). 
Jan 18 17:17:52 no kernel: [    8.822359] wlan0: ethernet device 00:1d:60:b0:a1:cc using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
Jan 18 17:17:52 no kernel: [    8.822402] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Jan 18 17:17:52 no kernel: [    8.829058] usbcore: registered new interface driver ndiswrapper
Jan 18 17:17:52 no NetworkManager: <debug> [1232299072.410211] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_1d_60_b0_a1_cc'). 
Jan 18 17:17:52 no vmnetBridge: RTM_NEWLINK: name:wlan0 index:9 flags:0x00001003 
Jan 18 17:17:52 no vmnetBridge: Can't remove interface wlan0 9 (does not exist). 
Jan 18 17:17:52 no kernel: [    8.840384] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 18 17:17:52 no kernel: [    8.844725] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 21 (level, low) -> IRQ 21
Jan 18 17:17:52 no NetworkManager: <info>  wlan0: Device is fully-supported using driver 'ndiswrapper'. 
Jan 18 17:17:52 no NetworkManager: <info>  wlan0: driver does not support SSID scans (scan_capa 0x00). 
Jan 18 17:17:52 no NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jan 18 17:17:52 no NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jan 18 17:17:52 no NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Jan 18 17:17:52 no NetworkManager: <info>  Deactivating device wlan0. 
Jan 18 17:17:52 no kernel: [    8.861916] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
Jan 18 17:17:52 no kernel: [    8.861933] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
Jan 18 17:17:52 no kernel: [    8.861941] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
Jan 18 17:17:52 no NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Jan 18 17:17:52 no kernel: [    8.902126] ssb: Sonics Silicon Backplane found on PCI device 0000:08:00.0
Jan 18 17:17:52 no kernel: [    8.902159] b44.c:v2.0
Jan 18 17:17:52 no vmnetBridge: RTM_NEWLINK: name:eth0 index:10 flags:0x00001002 
Jan 18 17:17:52 no vmnetBridge: Can't remove interface eth0 10 (does not exist). 
Jan 18 17:17:52 no kernel: [    8.925662] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1c:23:a9:2f:f0
Jan 18 17:17:52 no NetworkManager: <debug> [1232299072.526021] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/ssb__null_'). 
Jan 18 17:17:52 no NetworkManager: <debug> [1232299072.551082] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_1c_23_a9_2f_f0'). 
Jan 18 17:17:52 no vmnetBridge: RTM_NEWLINK: name:eth0 index:10 flags:0x00001043 
Jan 18 17:17:52 no kernel: [    8.987245] /dev/vmnet: open called by PID 5059 (vmnet-bridge)
Jan 18 17:17:52 no kernel: [    8.987259] /dev/vmnet: hub 0 does not exist, allocating memory.
Jan 18 17:17:52 no kernel: [    8.987272] /dev/vmnet: port on hub 0 successfully opened
Jan 18 17:17:52 no kernel: [    8.987285] bridge-eth0: up
Jan 18 17:17:52 no kernel: [    8.991983] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 18 17:17:52 no vmnetBridge: Started bridge eth0 to virtual network 0. 
Jan 18 17:17:52 no kernel: [    8.992825] bridge-eth0: attached
Jan 18 17:17:52 no NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Jan 18 17:17:52 no NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jan 18 17:17:52 no NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jan 18 17:17:52 no NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Jan 18 17:17:52 no NetworkManager: <info>  Deactivating device eth0. 
Jan 18 17:17:52 no NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Jan 18 17:17:52 no NetworkManager: <debug> [1232299072.594699] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/ssb__null_'). 
Jan 18 17:17:52 no NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Jan 18 17:17:52 no dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jan 18 17:17:52 no NetworkManager: <info>  Will activate connection 'eth0'. 
Jan 18 17:17:52 no NetworkManager: <info>  Device eth0 activation scheduled... 
Jan 18 17:17:52 no NetworkManager: <info>  Activation (eth0) started... 
Jan 18 17:17:52 no NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 18 17:17:52 no NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Jan 18 17:17:52 no NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Jan 18 17:17:52 no NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Jan 18 17:17:52 no NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Jan 18 17:17:52 no NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Jan 18 17:17:52 no NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan 18 17:17:52 no NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Jan 18 17:17:52 no NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Jan 18 17:17:53 no kernel: [    9.640416] bridge-eth0: disabling the bridge
...

```


after all that and a bunch more, the computer comes up with a working connection to wlan and internet, right where I left off.

So looks like my problem is happening when the kernel is loading the driver?  any thoughts?  

Thanks!

---

