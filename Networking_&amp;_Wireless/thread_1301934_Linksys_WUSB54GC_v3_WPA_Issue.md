---
title: "Linksys WUSB54GC v3 WPA Issue"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by SideSwipe on 2009-10-26
Hey guys,

I hope you can help. I'm currently setting up an old Dell Optiplex GX260 as a low powered and thankfully very quiet HTPC using XBMC. At the moment I've been able to get everything working, except for the USB wireless adapter I purchased for the computer. Thanks to this guide: [http://ubuntuforums.org/showpost.php?p=7262158&postcount=2](http://ubuntuforums.org/showpost.php?p=7262158&postcount=2) I've managed to get NetworkManager to be able to "see" the device as ra0, it is able to scan and detect all the networks within range of the computer, but it is not able to join any of them irregardless of what security is set (I've tried Open, WEP and WPA). Below is all the information set out in the "How To post a Wireless issue" thread.

```
Bus 001 Device 004: ID 1737:0077 Linksys 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1737 Linksys
  idProduct          0x0077 
  bcdDevice            1.01
  iManufacturer           1 Ralink
  iProduct                2 802.11 g WLAN
  iSerial                 3 1.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           67
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              450mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           7
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5 1.0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)
```Wireless adapter is Linksys WUSB54GC v3 with Ralink RT2870 chipset.

iwconfig ra0
```
ra0       RT2870 Wireless  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.462 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:-74 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```lsmod | grep rt2870sta
```
rt2870sta             502740  1
```dmesg | grep ra0
```
[   24.267778] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[   24.267829] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[   24.267880] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[   24.267931] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[   34.956036] ra0: no IPv6 routers present
[ 1305.443787] I/F(ra0) Key1Str is Invalid key length! KeyLen = 12!
[ 1305.443839] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[ 1305.443891] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[ 1305.443942] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[ 1315.620019] ra0: no IPv6 routers present
```dmesg | grep rt2870sta returns nothing

sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 02
       serial: 00:08:74:fb:6d:89
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI duplex=full firmware=N/A ip=192.168.137.171 latency=64 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=1GB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 00:23:69:e3:a6:9d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT2870 Wireless
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: be:7f:1f:6e:09:41
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```iwlist scan
```
ra0       Scan completed :
          Cell 01 - Address: 00:1F:33:CF:BD:E8
                    ESSID:"NolNicAshVic"
                    Mode:Managed
                    Channel:6
                    Quality:65/100  Signal level:-64 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:26:F2:01:AD:3A
                    ESSID:"LandseerLads"
                    Mode:Managed
                    Channel:6
                    Quality:10/100  Signal level:-86 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:26:F2:02:3B:C2
                    ESSID:"AaronRathmore"
                    Mode:Managed
                    Channel:6
                    Quality:0/100  Signal level:-92 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:1E:E5:45:94:92
                    ESSID:"scarycats"
                    Mode:Managed
                    Channel:11
                    Quality:55/100  Signal level:-68 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```Note that scarycats is my house network

Ubuntu release and kernel:
```
Description:    Ubuntu 9.04
2.6.28-16-generic i686
```Network restart:
```
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.
```I've reached the extent of my own resources, searching these forums and Google aren't showing up anything new to try, but are showing that some people have managed to get this adapter working perfectly :(

I hope you can help as I'd love to get this computer up an running (as would the people I live with). If you need any more information, ask away!

---

### Post by willrockformilk on 2009-12-11
I am in the EXACT same boat as you bud. Installed on an optiplex gx260 and ran to office depot and bought the cheapest one. Then follow that exact same thread and am at the exact same point as you. Kinda Scary actually. 

tail -100 /var/log/syslog

```
Dec 11 10:14:54 laroom-desktop avahi-daemon[2451]: Registering new address record for fe80::225:9cff:fe7c:bb3c on ra0.*.
Dec 11 10:15:03 laroom-desktop kernel: [ 1537.528010] ra0: no IPv6 routers present
Dec 11 10:15:11 laroom-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Dec 11 10:15:11 laroom-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Dec 11 10:15:11 laroom-desktop dhclient: All rights reserved.
Dec 11 10:15:11 laroom-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Dec 11 10:15:11 laroom-desktop dhclient: 
Dec 11 10:15:12 laroom-desktop dhclient: Listening on LPF/ra0/00:25:9c:7c:bb:3c
Dec 11 10:15:12 laroom-desktop dhclient: Sending on   LPF/ra0/00:25:9c:7c:bb:3c
Dec 11 10:15:12 laroom-desktop dhclient: Sending on   Socket/fallback
Dec 11 10:15:13 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
Dec 11 10:15:17 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
Dec 11 10:15:22 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
Dec 11 10:15:31 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 19
Dec 11 10:15:50 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 17
Dec 11 10:16:07 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
Dec 11 10:16:14 laroom-desktop dhclient: No DHCPOFFERS received.
Dec 11 10:16:14 laroom-desktop dhclient: No working leases in persistent database - sleeping.
Dec 11 10:16:14 laroom-desktop avahi-autoipd(ra0)[5900]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Dec 11 10:16:14 laroom-desktop avahi-autoipd(ra0)[5900]: Successfully called chroot().
Dec 11 10:16:14 laroom-desktop avahi-autoipd(ra0)[5900]: Successfully dropped root privileges.
Dec 11 10:16:14 laroom-desktop avahi-autoipd(ra0)[5900]: Starting with address 169.254.6.234
Dec 11 10:16:19 laroom-desktop avahi-autoipd(ra0)[5900]: Callout BIND, address 169.254.6.234 on interface ra0
Dec 11 10:16:19 laroom-desktop avahi-daemon[2451]: Joining mDNS multicast group on interface ra0.IPv4 with address 169.254.6.234.
Dec 11 10:16:19 laroom-desktop avahi-daemon[2451]: New relevant interface ra0.IPv4 for mDNS.
Dec 11 10:16:19 laroom-desktop avahi-daemon[2451]: Registering new address record for 169.254.6.234 on ra0.IPv4.
Dec 11 10:16:23 laroom-desktop avahi-autoipd(ra0)[5900]: Successfully claimed IP address 169.254.6.234
Dec 11 10:16:48 laroom-desktop kernel: [ 1642.642546] Terminate the TimerQThr_pid=5780!
Dec 11 10:16:48 laroom-desktop kernel: [ 1642.642597] Terminate the MLMEThr_pid=5778!
Dec 11 10:16:48 laroom-desktop kernel: [ 1642.642614] Terminate the RTUSBCmdThr_pid=5779!
Dec 11 10:16:48 laroom-desktop avahi-daemon[2451]: Interface ra0.IPv4 no longer relevant for mDNS.
Dec 11 10:16:48 laroom-desktop avahi-daemon[2451]: Leaving mDNS multicast group on interface ra0.IPv4 with address 169.254.6.234.
Dec 11 10:16:48 laroom-desktop avahi-autoipd(ra0)[5900]: SIOCSIFFLAGS failed: Permission denied
Dec 11 10:16:48 laroom-desktop avahi-autoipd(ra0)[5900]: Callout STOP, address 169.254.6.234 on interface ra0
Dec 11 10:16:48 laroom-desktop dhclient: receive_packet failed on ra0: Network is down
Dec 11 10:16:48 laroom-desktop kernel: [ 1642.649576] ---> RTMPFreeTxRxRingMemory
Dec 11 10:16:48 laroom-desktop kernel: [ 1642.649624] <--- ReleaseAdapter
Dec 11 10:16:48 laroom-desktop avahi-daemon[2451]: Withdrawing address record for fe80::225:9cff:fe7c:bb3c on ra0.
Dec 11 10:16:48 laroom-desktop avahi-daemon[2451]: Withdrawing address record for 169.254.6.234 on ra0.
Dec 11 10:16:48 laroom-desktop avahi-autoipd(ra0)[5901]: client: RTNETLINK answers: No such process
Dec 11 10:16:56 laroom-desktop dhclient: There is already a pid file /var/run/dhclient.pid with pid 5917
Dec 11 10:16:56 laroom-desktop dhclient: killed old client process, removed PID file
Dec 11 10:16:56 laroom-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Dec 11 10:16:56 laroom-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Dec 11 10:16:56 laroom-desktop dhclient: All rights reserved.
Dec 11 10:16:56 laroom-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Dec 11 10:16:56 laroom-desktop dhclient: 
Dec 11 10:16:56 laroom-desktop dhclient: Listening on LPF/ra0/00:25:9c:7c:bb:3c
Dec 11 10:16:56 laroom-desktop dhclient: Sending on   LPF/ra0/00:25:9c:7c:bb:3c
Dec 11 10:16:56 laroom-desktop dhclient: Sending on   Socket/fallback
Dec 11 10:17:02 laroom-desktop /USR/SBIN/CRON[5978]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.114076] <-- RTMPAllocTxRxRingMemory, Status=0
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.117070] -->RTUSBVenderReset
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.117191] <--RTUSBVenderReset
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.395631] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.395673] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.395714] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.395757] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.406851] 1. Phy Mode = 5
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.406856] 2. Phy Mode = 5
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.437770] RTMPSetPhyMode: channel is out of range, use first channel=1 
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.451138] 3. Phy Mode = 9
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.459139] MCS Set = ff 00 00 00 01
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.531880] <==== RTMPInitialize, Status=0
Dec 11 10:17:15 laroom-desktop kernel: [ 1669.533498] 0x1300 = 00064300
Dec 11 10:17:17 laroom-desktop avahi-daemon[2451]: Registering new address record for fe80::225:9cff:fe7c:bb3c on ra0.*.
Dec 11 10:17:26 laroom-desktop kernel: [ 1679.888011] ra0: no IPv6 routers present
Dec 11 10:18:56 laroom-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Dec 11 10:18:56 laroom-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Dec 11 10:18:56 laroom-desktop dhclient: All rights reserved.
Dec 11 10:18:56 laroom-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Dec 11 10:18:56 laroom-desktop dhclient: 
Dec 11 10:18:57 laroom-desktop dhclient: Listening on LPF/ra0/00:25:9c:7c:bb:3c
Dec 11 10:18:57 laroom-desktop dhclient: Sending on   LPF/ra0/00:25:9c:7c:bb:3c
Dec 11 10:18:57 laroom-desktop dhclient: Sending on   Socket/fallback
Dec 11 10:18:58 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
Dec 11 10:19:04 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
Dec 11 10:19:15 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13
Dec 11 10:19:28 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 17
Dec 11 10:19:45 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
Dec 11 10:19:59 laroom-desktop dhclient: No DHCPOFFERS received.
Dec 11 10:19:59 laroom-desktop dhclient: No working leases in persistent database - sleeping.
Dec 11 10:19:59 laroom-desktop avahi-autoipd(ra0)[6290]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Dec 11 10:19:59 laroom-desktop avahi-autoipd(ra0)[6290]: Successfully called chroot().
Dec 11 10:19:59 laroom-desktop avahi-autoipd(ra0)[6290]: Successfully dropped root privileges.
Dec 11 10:19:59 laroom-desktop avahi-autoipd(ra0)[6290]: Starting with address 169.254.6.234
Dec 11 10:20:01 laroom-desktop /USR/SBIN/CRON[6302]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 11 10:20:04 laroom-desktop avahi-autoipd(ra0)[6290]: Callout BIND, address 169.254.6.234 on interface ra0
Dec 11 10:20:04 laroom-desktop avahi-daemon[2451]: Joining mDNS multicast group on interface ra0.IPv4 with address 169.254.6.234.
Dec 11 10:20:04 laroom-desktop avahi-daemon[2451]: New relevant interface ra0.IPv4 for mDNS.
Dec 11 10:20:04 laroom-desktop avahi-daemon[2451]: Registering new address record for 169.254.6.234 on ra0.IPv4.
Dec 11 10:20:08 laroom-desktop avahi-autoipd(ra0)[6290]: Successfully claimed IP address 169.254.6.234
Dec 11 10:26:08 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
Dec 11 10:26:11 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
Dec 11 10:26:19 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 21
Dec 11 10:26:40 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
Dec 11 10:26:48 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
Dec 11 10:26:56 laroom-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
Dec 11 10:27:09 laroom-desktop dhclient: No DHCPOFFERS received.
Dec 11 10:27:09 laroom-desktop dhclient: No working leases in persistent database - sleeping.
```dmesg | grep ra0

```
[   27.885285] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[   27.885326] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[   27.885367] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[   27.885409] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[   38.116030] ra0: no IPv6 routers present
[   77.423141] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[   77.423184] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[   77.423225] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[   77.423267] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[   88.500049] ra0: no IPv6 routers present
[  317.150146] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[  317.150189] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[  317.150230] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[  317.150272] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[  327.768023] ra0: no IPv6 routers present
[  394.851313] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[  394.851357] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[  394.851398] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[  394.851440] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[  405.816025] ra0: no IPv6 routers present
[  670.312094] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[  670.312136] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[  670.312177] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[  670.312219] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[  675.059914] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[  675.059957] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[  675.059998] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[  675.060061] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[  685.732016] ra0: no IPv6 routers present
[  873.875269] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[  873.875312] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[  873.875353] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[  873.875395] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[  884.644014] ra0: no IPv6 routers present
[ 1526.559231] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[ 1526.559273] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[ 1526.559315] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[ 1526.559357] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[ 1537.528010] ra0: no IPv6 routers present
[ 1669.395631] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[ 1669.395673] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[ 1669.395714] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[ 1669.395757] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[ 1679.888011] ra0: no IPv6 routers present
```I think the obvious problem is that our ra0 is not authenticating (obviously) and it has to do with:

```
I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
```I have tried wpa_supplicant to connect. And have even tried:

```
sudo ifconfig [interface] down
sudo dhclient -r [interface]
sudo ifconfig [interface] up
sudo iwconfig [inteface] essid “ESSID_IN_QUOTES”
sudo iwpriv [interface] set AuthMode=WPAPSK
sudo iwpriv [interface] set EncrypType=TKIP
sudo iwpriv [interface] set WPAPSK=”YOUR_WPA_PSK_KEY”
sudo dhclient [interface]
```Which was found here: [http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html/comment-page-1](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html/comment-page-1)

I believe there is something about the tutorial on [http://newyork.ubuntuforums.org/showthread.php?t=1155941](http://newyork.ubuntuforums.org/showthread.php?t=1155941) that overides normal authentication procedures and uses the /etc/Wireless/RT2870STA/RT2870STA.dat file for the source of authentication. However all my information in that file is correct and im somewhat at a loss as to what to do.

Which in that file i have tried both using the raw password and using the encrypted pass via:

```
wpa_passphrase your_essid your_passphrase
```RT2870STA.dat:

```
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=11n-AP
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=WPA2
EncrypType=TKIP
WPAPSK=036223a995db109fd2420d54f19f885fc87eb8c596d03299e60b0bc354bb6af3
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
FastRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=1
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
CarrierDetect=0
```Another problem i have picked up on looking at log files was that the default ESSID sometimes replaces what i have entered into this .dat file for example in the code i just put up there 11n-AP is being used instead of my ESSID. However i have SET this variable and for some reason the system overwrites it. 

Anyone else have any ideas?

---

