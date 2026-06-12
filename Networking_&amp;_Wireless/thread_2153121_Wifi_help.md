---
title: "Wifi help"
date: 2013-06-10
forum: Networking &amp; Wireless
---

### Post by robbo87 on 2013-06-10
Hi, First of all I'm a complete noob with Ubuntu so sorry for my lack of knowledge.

I installed Ubuntu on my laptop last night and have had problems with my connection constantly dropping via wifi.

It will work for a few minutes then just stop. A simple disconnect and reconnect will get up up again but it will just drop again a few minutes later. 

I uninstalled network manager and installed wicd as most people with similar problems seem to have solved it doing that. 

After installing wicd I still had problems with authentication, but changing my wpa to wpa2 seemed to sort that, It connect's but is still constantly dropping after a few minutes. I'm using a usb edimax nano wifi adapter as my onboard wifi broke long ago. It worked perfectly on windows, but due to me stupidly installing it wrongly my windows partition is long gone :/..

anyone any idea's? I'm not really sure what to do next.

---

### Post by robbo87 on 2013-06-10
Just to add here is the script file. I've tried a few fixes so far including installing different drivers but nothing seems to be working 

```
*************** info trace ***************

***** uname -a *****

Linux martin-Presario-F500-RY574EA-ABU 3.5.0-32-generic  #53~precise1-Ubuntu SMP Wed May 29 20:35:31 UTC 2013 i686 athlon i386  GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

***** lspci *****

00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Kernel driver in use: forcedeth

***** lsusb *****

Bus 001 Device 002: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 002 Device 002: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 002 Device 003: ID 0c45:7000 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 045e:00b4 Microsoft Corp. 
Bus 002 Device 007: ID 15d9:0a4c Trust International B.V. USB+PS/2 Optical Mouse

***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"virginmedia4098985"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

rtl8192cu              67480  0 
rtl8192c_common        47696  1 rtl8192cu
rtlwifi                65304  1 rtl8192cu
mac80211              475546  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              181041  2 rtlwifi,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [virginmedia4098985] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *virginmedia4098985: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 76 WPA2

  IPv4 Settings:
    Address:         192.168.0.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             194.168.4.100
    DNS:             194.168.8.100


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"virginmedia4098985"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000567327b02
                    Extra: Last beacon: 688ms ago
                    IE: Unknown: 001276697267696E6D6564696134303938393835
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown:  DD7E0050F204104A0001101044000102103B0001031047001004AA7F10ED0680E162349311D137BD32102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F20400011011000743473331303144100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180201F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** dmesg *****

[   20.065466] rtl8192cu: Chip version 0x10
[   20.252932] rtl8192cu: MAC address: <MAC address removed>
[   20.252940] rtl8192cu: Board Type 0
[   20.253200] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   20.253310] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[   20.351463] Error: Driver 'rtl8192cu' is already registered, aborting...
[   20.644472] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   20.645200] rtlwifi: wireless switch is on
[   20.674707] rtl8192cu: MAC auto ON okay!
[   20.710971] rtl8192cu: Tx queue select: 0x05
[   21.162264] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.162958] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.716719] wlan0: authenticate with <MAC address removed>
[   24.740775] wlan0: send auth to <MAC address removed> (try 1/3)
[   24.743861] wlan0: authenticated
[   24.756039] wlan0: associate with <MAC address removed> (try 1/3)
[   24.761352] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   24.761391] wlan0: associated
[   24.761630] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1654.501830] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1659.667383] wlan0: authenticate with <MAC address removed>
[ 1659.695568] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1659.698183] wlan0: authenticated
[ 1659.724053] wlan0: associate with <MAC address removed> (try 1/3)
[ 1659.728431] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 1659.728505] wlan0: associated
[ 2050.393043] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2051.364498] wlan0: authenticate with <MAC address removed>
[ 2051.398334] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2051.400772] wlan0: authenticated
[ 2051.416116] wlan0: associate with <MAC address removed> (try 1/3)
[ 2051.421066] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 2051.421115] wlan0: associated

****************** done ******************

```

---

### Post by ahallubuntu on 2013-06-10
~

---

### Post by ahallubuntu on 2013-06-10
~

---

