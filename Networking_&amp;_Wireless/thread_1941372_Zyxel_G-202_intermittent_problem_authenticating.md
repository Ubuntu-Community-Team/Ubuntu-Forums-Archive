---
title: "Zyxel G-202 intermittent problem authenticating"
date: 2012-03-15
forum: Networking &amp; Wireless
---

### Post by samuelsimon on 2012-03-15
Plenty of wireless networks appear in the menu and sometimes it connects but more frequently I'm asked for my WEP password again and again. Restarting sometimes solves it but I can't see what I'm doing differently. It's not a great physical distance from the computer to the modem. Below is the output of "nm-tool" when I'm successfully connected. Any suggestions would be appreciated.




NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:12:79:66:E9:48

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [SpeedTouchA2CF20] --------------------------------------------
  Type:              802.11 WiFi
  Driver:            zd1211rw
  State:             connected
  Default:           yes
  HW Address:        00:13:49:8E:DD:A5

  Capabilities:
    Speed:           48 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *SpeedTouchA2CF20: Infra, 00:90:D0:EE:26:D1, Freq 2437 MHz, Rate 54 Mb/s, Strength 41 WEP
    colinr:          Infra, 00:1D:0F:ED:60:26, Freq 2437 MHz, Rate 54 Mb/s, Strength 5 WEP
    paulnet:         Infra, 14:D6:4D:74:1A:7C, Freq 2432 MHz, Rate 54 Mb/s, Strength 3 WEP
    belkin54g:       Infra, 00:11:50:93:54:3C, Freq 2462 MHz, Rate 54 Mb/s, Strength 4
    BTFON:           Infra, 12:FE:F4:2E:10:50, Freq 2412 MHz, Rate 54 Mb/s, Strength 31
    BTOpenzone-H:    Infra, 02:FE:F4:2E:10:50, Freq 2412 MHz, Rate 54 Mb/s, Strength 32
    Orange-77c2c3:   Infra, E0:46:9A:B0:37:F6, Freq 2412 MHz, Rate 54 Mb/s, Strength 1 WPA WPA2
    Phoebe's House:  Infra, 30:46:9A:7E:9B:0C, Freq 2422 MHz, Rate 54 Mb/s, Strength 2 WPA WPA2
    BTHub3-59NH:     Infra, 00:FE:F4:2E:10:50, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    monkeyballz:     Infra, 00:01:E3:F4:15:0B, Freq 2452 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    SKY61161:        Infra, 00:1F:33:1A:7A:C9, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA

  IPv4 Settings:
    Address:         192.168.1.64
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

---

