---
title: "Can't connect to &quot;N&quot; network"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by Tycho on 2009-05-09
Router: Netgear WNDR3300 with DD-WRT installed.
        Radio 0 is set to N only 20Mhz channel width wpa2(aes) ssid (BeleriandN)
        Radio 1 is set to mixed B and G wpa2(aes) ssid(Beleriand)

Clients: Lenovo X200 with intel 5300
         Homebuilt with ralink based pci card

Problem: Neither machine can connect to the routers "N" only radio when running ubuntu. I have a windowsxp partition on the machine with the ralink card and it connects at 135Mbps. Both machines can connect to the b/g radio fine. When i switch network manager to the "BeleriandN" ssid this is what happens on the desktop machine...
/var/log/wpa_supplicant.log:
```
    CTRL-EVENT-SCAN-RESULTS 
    Trying to associate with 00:1f:33:d2:0e:99 (SSID='BeleriandN' freq=2437 MHz)
    Authentication with 00:1f:33:d2:0e:99 timed out.
    CTRL-EVENT-SCAN-RESULTS 
    Trying to associate with 00:1f:33:d2:0e:99 (SSID='BeleriandN' freq=2437 MHz)
    Authentication with 00:1f:33:d2:0e:99 timed out.
```
dmesg:
```
    [ 2939.495177] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
    [ 2954.510756] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 382
    [ 2954.510919] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
    [ 2969.530142] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 382
```

Is there some ubuntu "N" mode that I have to enable somewhere?

REQUESTED INFORMATION:
1 ) Machine Brand and Model (PC/Laptop):
    Homebuilt nvida 650i motherboard with intel q6600
2 ) Wireless Brand, Model and Wireless Chipset:
    04:09.0 Network controller [0280]: RaLink RT2800 802.11n PCI [1814:0601]
3 ) check interface:
```
    ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
              Mode:Auto  Frequency=2.437 GHz  Access Point: 00:1F:33:D2:0E:99   
              Bit Rate=1 Mb/s   
              RTS thr:off   Fragment thr:off
              Link Quality=94/100  Signal level:-58 dBm  Noise level:-87 dBm
              Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
              Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
4 ) Check for modules:
    rt2860sta             522968  1
5 ) Kernel boot messages:
```
    [   13.522465] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
    [   13.525863] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
    [   13.525872] rt2860 0000:04:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
    [   13.526008] 
    [   13.526008] 
    [   13.526009] === pAd = f8da6000, size = 580788 ===
    [   13.526010] 
    [   13.526012] <-- RTMPAllocAdapterBlock, Status=0
    ...
    [ 1924.314683] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
    [ 1939.333705] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 382
    [ 1939.333895] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
    [ 1954.353406] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 382
```
6 ) Network configuration:
```
    *-network               
       description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:04:09.0
       logical name: ra0
       version: 00
       serial: 00:08:54:8a:13:0e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=32 maxlatency=4 mingnt=2 module=rt2860sta multicast=yes wireless=RT2860 Wireless
```
7 ) Scan for networks:
```
    ra0   Scan completed :
          Cell 01 - Address: 00:1F:33:D2:0E:97
                    ESSID:"Beleriand"
                    Mode:Managed
                    Channel:1
                    Quality:55/100  Signal level:-68 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:1F:33:D2:0E:99
                    ESSID:"BeleriandN"
                    Mode:Managed
                    Channel:6
                    Quality:81/100  Signal level:-58 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:1C:DF:A8:58:9D
                    ESSID:"EugeneCoker"
                    Mode:Managed
                    Channel:6
                    Quality:20/100  Signal level:-82 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```
8 ) Ubuntu Version:
    Description:    Ubuntu 9.04
9 ) Kernel/architecture (including 32 vs. 64 bit):
    2.6.28-11-generic i686
10 ) Restarting the network:
     * Reconfiguring network interfaces...
     Ignoring unknown interface ra0=ra0.

---

### Post by dbloom on 2009-05-17
bump! same problem here although i feel should be happy i can at least connect.

---

### Post by superprash2003 on 2009-05-18
you get connected and you get an ip??

---

