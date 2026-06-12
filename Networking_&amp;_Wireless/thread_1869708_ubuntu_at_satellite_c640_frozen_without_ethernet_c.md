---
title: "ubuntu at satellite c640 frozen without ethernet connection"
date: 2011-10-26
forum: Networking &amp; Wireless
---

### Post by zhu1 on 2011-10-26
Hay guy's.. please help me.
I am use ubuntu 11.10amd64 at my Thosiba satellite c640. but without internet connection, the system just "frozen" after a few minutes not connected. 

this is screen lspci -c | less at terminal :

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Lite-On Communications Inc Device 6613
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at 90200000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k

06:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)
        Subsystem: Toshiba America Info Systems Device ff1e
        Flags: bus master, fast devsel, latency 0, IRQ 41
        Memory at 90100000 (64-bit, non-prefetchable) [size=256K]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>
        Kernel driver in use: atl1c
        Kernel modules: atl1c

at nm-tool :

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        68:A3:C4:AA:A9:31

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        00:26:6C:BE:41:E6

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             50.23.239.24
    DNS:             208.67.222.222

and this at var/log/syslog

Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]:    SCPlugin-Ifupdown: init!
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]:    SCPlugin-Ifupdown: update_system_hostname
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]:    SCPluginIfupdown: management mode: unmanaged
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:15.0/0000:02:00.0/net/wlan0, iface: wlan0)
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:15.0/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.:(
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:15.1/0000:06:00.0/net/eth0, iface: eth0)
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:15.1/0000:06:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]:    SCPlugin-Ifupdown: end _init.
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]: <info> Loaded plugin :confused:ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]:    Ifupdown: get unmanaged devices count: 0
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]:    SCPlugin-Ifupdown: (11428656) ... get_connections.
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]:    SCPlugin-Ifupdown: (11428656) ... get_connections (managed=false): return empty list.
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]:    keyfile: parsing SMC ... 
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]:    keyfile:     read connection 'SMC'
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]:    keyfile: parsing Auto Ethernet ... 
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]:    keyfile:     read connection 'Auto Ethernet'
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]:    Ifupdown: get unmanaged devices count: 0
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]: <info> modem-manager is now available
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]: <info> monitoring kernel firmware directory '/lib/firmware'.
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:15.0/0000:02:00.0/ieee80211/phy0/rfkill0) (driver (unknown))
Oct 26 08:54:59 rizqycom-Satellite-C640D udev-configure-printer: add /module/lp
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]: <info> WiFi enabled by radio killswitch; disabled by state file
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]: <info> WWAN enabled by radio killswitch; enabled by state file
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]: <info> WiMAX enabled by radio killswitch; enabled by state file
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]: <info> Networking is disabled by state file
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 3)
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]: <info> (eth0): carrier is OFF
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]: <info> (eth0): new Ethernet device (driver: 'atl1c' ifindex: 2)
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Oct 26 08:54:59 rizqycom-Satellite-C640D udev-configure-printer: Failed to get parent
Oct 26 08:54:59 rizqycom-Satellite-C640D NetworkManager[908]: <warn>:confused: bluez error getting default adapter: The name org.bluez was not provided by any .service files.

can anyone help me???

---

### Post by praseodym on 2011-10-26
Hi,

please show:

```
iwconfig
lsmod
sudo iwlist scan
cat /var/lib/NetworkManager/NetworkManager.state
rfkill list
```

---

