---
title: "Huawei e3131 fails to switch on ubuntu 12.10"
date: 2013-02-19
forum: Networking &amp; Wireless
---

### Post by pkliczewski on 2013-02-19
Hello,

I have a problem using my Huawei e3131 modem on ubuntu 12.10.  When I connect my modem and switch to serial using:

[http://192.168.1.1/html/switchProjectMode.html](http://192.168.1.1/html/switchProjectMode.html)
Here is log from the switch:
```

NetworkManager[1412]: <info> (eth2): IP6 addrconf timed out or failed.
NetworkManager[1412]: <info> Activation (eth2) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
NetworkManager[1412]: <info> Activation (eth2) Stage 4 of 5 (IPv6 Configure Timeout) started...
NetworkManager[1412]: <info> Activation (eth2) Stage 4 of 5 (IPv6 Configure Timeout) complete.
kernel: [78230.258967] userif-2: sent link up event.<6>[78254.630787] usb 1-1.2: USB disconnect, device number 18
kernel: [78254.632717] cdc_ether 1-1.2:1.0 eth2: unregister 'cdc_ether' usb-0000:00:1a.0-1.2, CDC Ethernet Device
vmnet-natd: RTM_NEWLINK: name:eth2 index:14 flags:0x00001002
avahi-daemon[1243]: Interface eth2.IPv6 no longer relevant for mDNS.
vmnetBridge: RTM_NEWLINK: name:eth2 index:14 flags:0x00001002
avahi-daemon[1243]: Leaving mDNS multicast group on interface eth2.IPv6 with address fe80::5a2c:80ff:fe13:9263.
vmnetBridge: Removing interface eth2 index:14
NetworkManager[1412]: <info> (eth2): carrier now OFF (device state 100, deferring action for 4 seconds)
avahi-daemon[1243]: Interface eth2.IPv4 no longer relevant for mDNS.
avahi-daemon[1243]: Leaving mDNS multicast group on interface eth2.IPv4 with address 192.168.1.100.
dhclient: receive_packet failed on eth2: Network is down
kernel: [78254.633286] bridge-eth2: disabling the bridge on dev down
kernel: [78254.633387] bridge-eth2: down
kernel: [78254.633903] bridge-eth2: detached
kernel: [78254.633960] /dev/vmnet: open called by PID 1482 (vmnet-bridge)
kernel: [78254.633974] /dev/vmnet: hub 0 does not exist, allocating memory.
kernel: [78254.634018] /dev/vmnet: port on hub 0 successfully opened
kernel: [78254.634033] bridge-eth1: device is wireless, enabling SMAC
kernel: [78254.634037] bridge-eth1: up
kernel: [78254.634047] bridge-eth1: attached
vmnetBridge: Stopped bridge eth2 to virtual network 0.
avahi-daemon[1243]: Withdrawing address record for fe80::5a2c:80ff:fe13:9263 on eth2.
vmnetBridge: Started bridge eth1 to virtual network 0.
avahi-daemon[1243]: Withdrawing address record for 192.168.1.100 on eth2.
vmnetBridge: RTM_DELLINK: name:eth2 index:14 flags:0x00001002
avahi-daemon[1243]: Withdrawing workstation service for eth2.
NetworkManager[1412]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/net/eth2, iface: eth2)
NetworkManager[1412]: <info> (eth2): now unmanaged
NetworkManager[1412]: <info> (eth2): device state change: activated -> unmanaged (reason 'removed') [100 10 36]
vmnet-natd: RTM_DELLINK: name:eth2 index:14 flags:0x00001002
NetworkManager[1412]: <info> (eth2): deactivating device (reason 'removed') [36]
kernel: [78254.832796] userif-2: sent link down event.
NetworkManager[1412]: <info> (eth2): canceled DHCP transaction, DHCP client pid 12823
NetworkManager[1412]: <warn> (14) failed to find interface name for index
NetworkManager[1412]: nm_system_iface_flush_routes: assertion `iface != NULL' failed
NetworkManager[1412]: <warn> (14) failed to find interface name for index
vmnet-natd: RTM_NEWROUTE: index:3
NetworkManager[1412]: <info> Policy set 'none' (eth1) as default for IPv4 routing and DNS.
vmnetBridge: RTM_NEWROUTE: index:3
NetworkManager[1412]: <info> ((null)): writing resolv.conf to /sbin/resolvconf
dnsmasq[1914]: setting upstream servers from DBus
dnsmasq[1914]: using nameserver 192.168.1.1#53
NetworkManager[1412]: <info> (eth2): cleaning up...
NetworkManager[1412]: <warn> (14) failed to find interface name for index
NetworkManager[1412]: (nm-system.c:769):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
NetworkManager[1412]: <error> [1361292896.130768] [nm-system.c:771] nm_system_iface_get_flags(): (unknown): failed to get interface link object
dbus[1110]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
dbus[1110]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
kernel: [78254.832802] userif-2: sent link up event.userif-2: sent link down event.
kernel: [78255.111802] userif-2: sent link up event.<6>[78258.410993] usb 1-1.2: new high-speed USB device number 19 using ehci_hcd
kernel: [78258.504345] usb 1-1.2: New USB device found, idVendor=12d1, idProduct=1442
kernel: [78258.504352] usb 1-1.2: New USB device strings: Mfr=2, Product=1, SerialNumber=0
kernel: [78258.504356] usb 1-1.2: Product: HUAWEI HiLink
kernel: [78258.504359] usb 1-1.2: Manufacturer: HUAWEI
kernel: [78258.504949] option 1-1.2:1.0: GSM modem (1-port) converter detected
kernel: [78258.505255] usb 1-1.2: GSM modem (1-port) converter now attached to ttyUSB0
kernel: [78258.505515] option 1-1.2:1.1: GSM modem (1-port) converter detected
kernel: [78258.505782] usb 1-1.2: GSM modem (1-port) converter now attached to ttyUSB1
mtp-probe: checking bus 1, device 19: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2"
mtp-probe: bus: 1, device: 19 was not an MTP device
modem-manager[1163]: <info>  (ttyUSB1) opening serial port...
modem-manager[1163]: <warn>  (ttyUSB1): port attributes not fully set
modem-manager[1163]: <info>  (ttyUSB0) opening serial port...
modem-manager[1163]: <warn>  (ttyUSB0): port attributes not fully set
modem-manager[1163]: <info>  (ttyUSB0) closing serial port...
modem-manager[1163]: <info>  (ttyUSB0) serial port closed
modem-manager[1163]: <info>  (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2 claimed port ttyUSB0
modem-manager[1163]: <info>  (ttyUSB1) closing serial port...
modem-manager[1163]: <info>  (ttyUSB1) serial port closed
modem-manager[1163]: <info>  (ttyUSB1) opening serial port...
modem-manager[1163]: <info>  (ttyUSB1) closing serial port...
modem-manager[1163]: <info>  (ttyUSB1) serial port closed
modem-manager[1163]: <info>  (ttyUSB0) opening serial port...
modem-manager[1163]: <warn>  (ttyUSB0): port attributes not fully set
NetworkManager[1412]: <warn> (ttyUSB0): failed to look up interface index
NetworkManager[1412]: <info> WWAN now disabled by management service
NetworkManager[1412]: <info> (ttyUSB0): new GSM/UMTS device (driver: 'option1' ifindex: 0)
NetworkManager[1412]: <info> (ttyUSB0): exported as /org/freedesktop/NetworkManager/Devices/11
laptop NetworkManager[1412]: <info> (ttyUSB0): now managed
NetworkManager[1412]: <info> (ttyUSB0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
NetworkManager[1412]: <info> (ttyUSB0): deactivating device (reason 'managed') [2]
NetworkManager[1412]: <info> (ttyUSB0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
modem-manager[1163]: <info>  (ttyUSB0) closing serial port...
laptop modem-manager[1163]: <info>  (ttyUSB0) serial port closed

```When I try to connect I am getting:

```

pppd[12963]: Using interface ppp0
pppd[12963]: Connect: ppp0 <--> /dev/ttyUSB0
NetworkManager[1412]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
NetworkManager[1412]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
NetworkManager[1412]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...

```Can anyone help to solve it.

Thanks,
Piotr

---

### Post by jdthood on 2013-02-19
That model is not listed upstream

    [https://live.gnome.org/NetworkManager/MobileBroadband](https://live.gnome.org/NetworkManager/MobileBroadband)

as supported.

---

### Post by bmork on 2013-03-20
> **pkliczewski said:**
> Hello,

I have a problem using my Huawei e3131 modem on ubuntu 12.10.  When I connect my modem and switch to serial using:

[http://192.168.1.1/html/switchProjectMode.html](http://192.168.1.1/html/switchProjectMode.html)



Why do you do that?  You are of course free to use whatever unsupported mode you like, but don't be surprised if it doesn't work...

> 
Here is log from the switch:
```

kernel: [78254.632717] cdc_ether 1-1.2:1.0 eth2: unregister 'cdc_ether' usb-0000:00:1a.0-1.2, CDC Ethernet Device

```


Didn't the modem work as it should with the cdc_ether driver?  You could obviously connect to the webui.

> 
```

kernel: [78258.504345] usb 1-1.2: New USB device found, idVendor=12d1, idProduct=1442
kernel: [78258.504352] usb 1-1.2: New USB device strings: Mfr=2, Product=1, SerialNumber=0
kernel: [78258.504356] usb 1-1.2: Product: HUAWEI HiLink
kernel: [78258.504359] usb 1-1.2: Manufacturer: HUAWEI
kernel: [78258.504949] option 1-1.2:1.0: GSM modem (1-port) converter detected
kernel: [78258.505255] usb 1-1.2: GSM modem (1-port) converter now attached to ttyUSB0
kernel: [78258.505515] option 1-1.2:1.1: GSM modem (1-port) converter detected
kernel: [78258.505782] usb 1-1.2: GSM modem (1-port) converter now attached to ttyUSB1
mtp-probe: checking bus 1, device 19: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2"
mtp-probe: bus: 1, device: 19 was not an MTP device
modem-manager[1163]: <info>  (ttyUSB1) opening serial port...
modem-manager[1163]: <warn>  (ttyUSB1): port attributes not fully set
modem-manager[1163]: <info>  (ttyUSB0) opening serial port...
modem-manager[1163]: <warn>  (ttyUSB0): port attributes not fully set
modem-manager[1163]: <info>  (ttyUSB0) closing serial port...
modem-manager[1163]: <info>  (ttyUSB0) serial port closed
modem-manager[1163]: <info>  (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2 claimed port ttyUSB0
modem-manager[1163]: <info>  (ttyUSB1) closing serial port...
modem-manager[1163]: <info>  (ttyUSB1) serial port closed
modem-manager[1163]: <info>  (ttyUSB1) opening serial port...
modem-manager[1163]: <info>  (ttyUSB1) closing serial port...
modem-manager[1163]: <info>  (ttyUSB1) serial port closed
modem-manager[1163]: <info>  (ttyUSB0) opening serial port...
modem-manager[1163]: <warn>  (ttyUSB0): port attributes not fully set
NetworkManager[1412]: <warn> (ttyUSB0): failed to look up interface index
NetworkManager[1412]: <info> WWAN now disabled by management service
NetworkManager[1412]: <info> (ttyUSB0): new GSM/UMTS device (driver: 'option1' ifindex: 0)
NetworkManager[1412]: <info> (ttyUSB0): exported as /org/freedesktop/NetworkManager/Devices/11
laptop NetworkManager[1412]: <info> (ttyUSB0): now managed

```

I guess modem-manager doesn't really know how to use the two serial ports available in this mode.  And neither do I.  Maybe none of them support PPP?  You should probably test a bit manually using e.g. minicom to find out more about this if you really want to add support for this unsupported firmware mode.

---

