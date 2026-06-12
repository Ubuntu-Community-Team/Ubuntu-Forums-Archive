---
title: "Ubuntu 12.10 server wireless not working"
date: 2013-03-24
forum: Networking &amp; Wireless
---

### Post by mancora on 2013-03-24
Hi,

I just installed a new server and I need a wireless connection to make it work. I had been trying for 3 days to make it work without success and I am not sure what is the problem. I would appreciate some help.

Here under are all the details from the configuration and wireless details. Network manager is already uninstalled.

/etc/network/interfaces

auto wlan0
#iface wlan0 inet dhcp
iface wlan0 inet static
    address 192.168.1.201
        mask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.254
        dns-nameservers 8.8.8.8 8.8.4.4
        wpa-driver iwlwifi
    wpa-conf managed
        wpa-ssid SOHO
        wpa-ap-scan 1
        wpa-proto RSN
        wpa-pairwise CCMP
        wpa-group CCMP
        wpa-key-mgmt WPA-PSK
        wpa-psk PedroPicapiedra

WS01:~$ sudo hwinfo --wlan
> hal.1: read hal dataprocess 2883: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
20: PCI 300.0: 0282 WLAN controller                             
  [Created at pci.318]
  Unique ID: y9sn.fNsjQBRm576
  Parent ID: qTvu.mI4JwHLbTlD
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Intel WLAN controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x0085 
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x1311 
  Revision: 0x34
  Driver: "iwlwifi"
  Driver Modules: "iwlwifi"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xf3000000-0xf3001fff (rw,non-prefetchable)
  IRQ: 46 (no events)
  HW Address: 60:67:20:b8:58:98
  Link detected: no
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13 36 40 44 48 52 56 60 64 100 104 108 112 116 120 124 128 132 136 140
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472 5.18 5.2 5.22 5.24 5.26 5.28 5.3 5.32 5.5 5.52 5.54 5.56 5.58 5.6 5.62 5.64 5.66 5.68 5.7
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v00008086d00000085sv00008086sd00001311bc02sc80i00"
  Driver Info #0:
    Driver Status: iwlwifi is active
    Driver Activation Cmd: "modprobe iwlwifi"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #11 (PCI bridge)


WS01:~$ sudo lshw -C network

  *-network DISABLED      
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 3c:97:0e:10:99:55
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k duplex=full firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:44 memory:f3a00000-f3a1ffff memory:f3a3b000-f3a3bfff ioport:6080(size=32)
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6205
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: 60:67:20:b8:58:98
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-26-generic firmware=18.168.6.1 ip=192.168.1.201 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:f3000000-f3001fff

WS01:~$ sudo iwlist scan


          Cell 10 - Address: CC:5D:4E:AA:4D:24
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"SOHO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000087e4b204f
                    Extra: Last beacon: 3000ms ago
                    IE: Unknown: 0004534F484F
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1605000600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05040022127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 07064E4C20010D10

WS01:/etc/network$ ifconfig


wlan0     Link encap:Ethernet  HWaddr 60:67:20:b8:58:98  
          inet addr:192.168.1.201  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

WS01:/etc/network$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

WS01:/etc/network$ dmesg | grep wlan
[   13.285610] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by mancora on 2013-03-24
Thanks everybody but fortunately after a flashlight I got it working, I was using the wireless card driver as wpa-driver which was wrong in the configuration, after changing it to "WEXT" and restarted my computer I got connected to my wireless network.

WS01:/etc$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"SOHO"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: CC:5D:4E:AA:4D:24   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:779  Invalid misc:19   Missed beacon:0

It is quite confusing the different configuration options available on the web, I was not sure what is the function of the wpa_supplicant.conf and which of all the different options on the web to use. Under this configiration wpa_supplicant.conf is not necessary as I deleted and reboot the server after having the connection up and running without any problem after.

I think this configuration under the  /etc/network/interfaces file is the most simple and clear to use as everything is defined under one file. Below the parameters and how to use them.

    auto wlan0:
    Your network interface (e.g. wlan0, eth1, rausb0, ra0, etc.).

    iface wlan0 inet static:
    Self-explanatory... I am using a Static IP instead of DHCP. "iface wlan0" must correspond to your network interface (see above).

    address, netmask, [..], dns-nameservers:
    Also self-explanatory... Be aware that "broadcast" needs to end with ".255" for negotiation with the router. These lines need to be according to your own (static) network settings. For DHCP see further below.

    wpa-driver: (not the wireless car driver)
    Use "wext" only. All other drivers are outdated no longer used.
    [/QUOTE]

    wpa-ssid:
    Your network's ESSID (no quotes ""). Please avoid blanks/spaces as they will created problems during key generation (see below).

    wpa-ap-scan:
    "1" = Broadcast of ESSID.
    "2" = Hidden broadcast of ESSID.

    wpa-proto:
    "RSN" = WPA(2)
    "WPA" = WPA(1)

    wpa-pairwise & wpa-group:
    "CCMP" = AES cipher as part of WPA(2) standard.
    "TKIP" = TKIP cipher as part of WPA(1) standard.

    wpa-key-mgmt:
    "WPA-PSK" = Authentication via pre-shared key (see 'key generation' further below).
    "WPA-EAP" = Authentication via enterprise authentication server.

---

