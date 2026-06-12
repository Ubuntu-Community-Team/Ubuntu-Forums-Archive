---
title: "BCM4313, cannot connect to wireless network"
date: 2013-06-06
forum: Networking &amp; Wireless
---

### Post by szparson on 2013-06-06
Hi,

i got a problem, i just moved to UK from poland, today i just got internet in my house (TalkTalk network), any other device in home except my asus 1015p can connect via wifi, but my laptop cant, i changed the security mode in router, switched to just B/G wifi, doesnt help, i can see a network but cant connect to it ([COLOR=#000000] 'Authentication required by wireless network'.)[/COLOR]

this the log, im connected via cable to router

```
karola@LucyFord:~$ lspci -vnn | grep Network03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
karola@LucyFord:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
Linux LucyFord 3.5.0-32-generic #53-Ubuntu SMP Wed May 29 20:23:04 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
karola@LucyFord:~$ 
karola@LucyFord:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8131 Gigabit Ethernet [1969:1063] (rev c0)
 Subsystem: ASUSTeK Computer Inc. Device [1043:83fe]
 Kernel driver in use: atl1c
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
 Subsystem: AzureWave Device [1a3b:2047]
 Kernel driver in use: bcma-pci-bridge
karola@LucyFord:~$ 
karola@LucyFord:~$ nm-tool


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        20:CF:30:6B:EA:09


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        48:5D:60:2A:FF:87


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    Ambleside:       Infra, 5C:7D:5E:B7:2E:34, Freq 2462 MHz, Rate 54 Mb/s, Strength 84 WPA2
    SKY8FF58:        Infra, 7C:4C:A5:35:1B:AD, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA2
    BTHub3-PX3S:     Infra, 00:03:D8:E6:CD:0E, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    TALKTALK-C01B54: Infra, 90:94:E4:C0:1B:54, Freq 2452 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    TALKTALK-376980: Infra, 88:53:D4:37:69:88, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    virginmedia5053879: Infra, 84:1B:5E:BC:48:BC, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    BTHub3-9J6K:     Infra, 00:FE:F4:43:9F:B8, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    SKYE3FDA:        Infra, 4C:17:EB:BE:3F:DB, Freq 2427 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    BTWiFi:          Infra, 02:03:D8:E6:CD:0E, Freq 2412 MHz, Rate 54 Mb/s, Strength 47
    BTOpenzone-B:    Infra, 12:03:D8:E6:CD:0E, Freq 2412 MHz, Rate 54 Mb/s, Strength 47
    BTWiFi:          Infra, 02:FE:F4:43:9F:B8, Freq 2462 MHz, Rate 54 Mb/s, Strength 30
    BTWiFi-with-FON: Infra, 12:FE:F4:43:9F:B8, Freq 2462 MHz, Rate 54 Mb/s, Strength 37
    BTWiFi-with-FON: Infra, 4A:96:A0:32:52:80, Freq 2462 MHz, Rate 54 Mb/s, Strength 29
    O2wirelessF78B01:Infra, 00:26:44:F7:8B:01, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    BTHub3-97SH:     Infra, CC:96:A0:32:52:86, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    BTWiFi:          Infra, 4A:96:A0:32:52:87, Freq 2462 MHz, Rate 54 Mb/s, Strength 27
    Home:            Infra, 7C:D1:C3:CB:ED:AA, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    BTWiFi-with-FON: Infra, 12:81:D8:60:36:D2, Freq 2437 MHz, Rate 54 Mb/s, Strength 32
    SKY7101A:        Infra, 7C:4C:A5:2E:5C:1D, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA2
    TALKTALK-7AF6B8: Infra, 1C:AF:F7:7A:F6:B8, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    SKY2A543:        Infra, 90:01:3B:32:A5:44, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2




karola@LucyFord:~$ 
karola@LucyFord:~$ lsusb
Bus 001 Device 002: ID 13d3:5702 IMC Networks UVC VGA Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
karola@LucyFord:~$ 
karola@LucyFord:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
karola@LucyFord:~$ 
karola@LucyFord:~$ rfkill list all
0: asus-wlan: Wireless LAN
 Soft blocked: no
 Hard blocked: no
1: asus-bluetooth: Bluetooth
 Soft blocked: yes
 Hard blocked: no
2: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: no
karola@LucyFord:~$
```

---

### Post by szparson on 2013-06-07
WICD solved the case.

---

