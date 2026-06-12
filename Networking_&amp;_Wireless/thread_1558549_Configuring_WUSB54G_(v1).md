---
title: "Configuring WUSB54G (v1)"
date: 2010-08-22
forum: Networking &amp; Wireless
---

### Post by wand3r3r on 2010-08-22
I have an old desktop that I recently converted from windows to ubuntu 10.04 server.  I connect to my wireless router using the subject wireless adapter.  After scouring websites I've installed the appropriate drivers using ndiswrapper.  I've been able to configure and connect to the network using Gnome Network Manager (System->Prefrences->Network Connections)  However when I try to configure using /etc/network/interfaces it will not connect.  The client continuously probes for DHCP offers and eventually responsd with no DHCP offers returned.

output of ndiswrapper -l is
```

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
wusb54g : driver installed
    device (1915:2234) present (alternate driver: p54usb)

```iwlist wlan0 scan finds my network
```

wlan0     Scan completed :
          Cell 01 - Address: XX:XX:XX:XX:XX:XX
                    ESSID:"XXXXXX"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1
[\CODE]

When using the gnome NM dmesg prompts
[CODE]
[ 1042.320517] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1050.511284] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1051.805180] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1062.068031] wlan0: no IPv6 routers present
[\CODE]
When using ifupdown dmesg does not log the ndiswrapper line above.

I've tired modifying /etc/network/interfaces several times here is what I have currently
[CODE]allow-hotplug wlan0
iface wlan0 inet dhcp
    wireless-channel 4
    wireless-essid MD_TK_MG
    wireless-key1 VVVVVVVVVV
    wireless-key2 XXXX-XXXX-XX
    wireless-key3 YYYY-YYYY-YY
    wireless-key4 ZZZZ-ZZZZ-ZZ
    wireless-defaultkey 1
    wireless-keymode open
    wireless-mode managed
```

---

### Post by wand3r3r on 2010-08-24
It appears all I had to do was uninstall network-manager.

---

