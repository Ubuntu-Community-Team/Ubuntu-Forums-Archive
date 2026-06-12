---
title: "Netgear WG111v2 - driver loaded, but can't connect to wlan"
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by b0rsten on 2006-07-14
I've bought a netgear wg111v2 and installed the driver with ndiswrapper...
i "think" all settings are correct, but i cannot connect to my wlan

for testing i'm NOT using WEP or WPA or anything like that... my essid is  "mueller.wi" 

```

$ lsusb
Bus 005 Device 003: ID 0644:0200 TEAC Corp.
Bus 005 Device 002: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)

```

```

$ ndiswrapper -l
Installed ndis drivers:
net111v2                driver present, hardware present

```

when i plug in my usb-dongle:

```

$ dmesg
...
...
[17180678.524000] usb 5-2: new high speed USB device using ehci_hcd and address 6
[17180678.660000] rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
[17180678.772000] rtl8187: Card MAC address is 00:14:6c:6c:e9:de
[17180678.944000] rtl8187: Card reports RF frontend Realtek 8225
[17180678.944000] rtl8187: WW:This driver has EXPERIMENTAL support for this chipset.
[17180678.944000] rtl8187: WW:use it with care and at your own risk and
[17180678.944000] rtl8187: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO andreamrl@tiscali.it
[17180678.976000] rtl8187: This seems a legacy 1st version radio
[17180678.976000] rtl8187: PAPE from CONFIG2: 0
[17180678.976000] rtl8187: Driver probe completed
[17180678.976000]
[17180679.716000] rtl8187: Card successfully reset

```

```

$ lsmod | grep ndi
ndiswrapper           177364  0
usbcore               130692  7 ndiswrapper,r8187,usb_storage,usbhid,ehci_hcd,uhci_hcd

```

```

$ iwconfig
lan0     802.11b/g link..  ESSID:"mueller.wi"
          Mode:Managed  Channel=6  Access Point: 00:04:0E:4F:21:D2
          Bit Rate=11 Mb/s
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

$ ifconfig
wlan0     Protokoll:Ethernet  Hardware Adresse 00:14:6C:6C:E9:DE
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

```

$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:04:0E:4F:21:D2
                    ESSID:"mueller.wi"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54
                    Quality:24  Signal level:0  Noise level:4
                    Extra: Last beacon: 993ms ago

```

```

$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:14:6c:6c:e9:de
Sending on   LPF/wlan0/00:14:6c:6c:e9:de
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

my blacklist:

```

blacklist islsm
blacklist islsm_usb
blacklist islsm_device

blacklist bcm43xx

```

my "module-autoload"

```

lp
psmouse
sbp2
sr_mod
ndiswrapper

```

i think this is not correct:

```

$ dmesg
...
...
[17180616.908000] Linking with mueller.wi
[17180619.460000] Linking with mueller.wi
[17180622.012000] Linking with mueller.wi
[17180624.564000] Linking with mueller.wi
[17180627.116000] Linking with mueller.wi
[17180629.668000] Linking with mueller.wi
[17180632.220000] Linking with mueller.wi
[17180634.772000] Linking with mueller.wi
[17180637.324000] Linking with mueller.wi
[17180639.876000] Linking with mueller.wi
[17180642.428000] Linking with mueller.wi
[17180644.980000] Linking with mueller.wi
[17180647.532000] Linking with mueller.wi
[17180650.084000] Linking with mueller.wi
[17180652.636000] Linking with mueller.wi
[17180655.188000] Linking with mueller.wi
[17180657.740000] Linking with mueller.wi
[17180660.292000] Linking with mueller.wi
[17180662.844000] Linking with mueller.wi
[17180665.396000] Linking with mueller.wi
[17180667.948000] Linking with mueller.wi
[17180670.500000] Linking with mueller.wi
[17180673.052000] Linking with mueller.wi

```

---

### Post by eternalsword on 2006-07-15
blacklist r8187 and rtl8187 that's the experimental Realtek driver that Ubuntu loads for some.

---

