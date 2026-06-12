---
title: "After upgrading from Maverik to Natty wiffi won't connect"
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by jmvidalvia on 2011-07-13
Hi, 
I am sorry to come with so boring questions, but..
After upgrading my system, nm-applet is unable to connect to wifi networks.
I tried:
```
$sudo iwlist scan
```
And it shows all networks, so the card is working.
I did
```
$sudo ifconfig wlan0 up
```
But nothing happened.
In nm-applet, available ESSIDs are highlighted, but wireless connection is not.
Must add that with the migration from Maverik, I lost my previous ESSID configs, but now this is not important, as I am trying with a new one.
Any clues?
Thanks a lot!

EDIT:
```
$nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        00:1F:16:37:F2:29

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.103.166
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.103.100

    DNS:             192.168.103.100


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             disconnected
  Default:           no
  HW Address:        00:26:C6:8B:39:CC

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    WLAN5E9715:      Infra, 00:22:2D:45:E9:BB, Freq 2417 MHz, Rate 54 Mb/s, Strength 44 WEP
    GRACEVI1:        Infra, 00:01:38:E8:67:9A, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA
    ZIVGuest:        Infra, 04:FE:7F:93:C0:91, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA
    GrupoZIV:        Infra, 04:FE:7F:93:C0:90, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA


- Device: wwan0 ----------------------------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            cdc_ether
  State:             disconnected
  Default:           no

  Capabilities:



```

---

