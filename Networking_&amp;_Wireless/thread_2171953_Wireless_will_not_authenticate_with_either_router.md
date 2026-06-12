---
title: "Wireless will not authenticate with either router"
date: 2013-09-02
forum: Networking &amp; Wireless
---

### Post by coolwood on 2013-09-02
My wireless adapter will not authenticate.  I keeps trying with and keeps getting the same error message. 
I have two wireless routers with the same broadcast name since one router will not cover the area I need covered.  
The setup works fine with my Windows computers.  
I suspect that this may be the problem I am having with Ubuntu 12.04.3.  

I ran the following command that I found on another post by Wild Man:

wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script

The gz file was too big to post in the dropbox so I have attached some of it here.
From what I can see it looks like the wireless card sees both routers.  I have not been able to see what this information looks like if my card connects so I am stuck.  

Does anyone else have a configuration similar to this that works?
I really don't want to change the router setups.
 
Any help will be appreciated.
Thanks 
  
```

*************** info trace ***************


***** uname -a *****


Linux ted-laptop 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 15:31:16 UTC 2013 i686 i686 i386 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise


***** lspci *****


02:08.0 Ethernet controller [0200]: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller [8086:1031] (rev 42)
    Subsystem: IBM ThinkPad A/T/X Series [1014:0209]
    Kernel driver in use: e100
--
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185]
    Kernel driver in use: rtl8180


***** lsusb *****


Bus 002 Device 002: ID 1d57:0008  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** PCMCIA Card Info *****


PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


***** iwconfig *****


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


***** rfkill *****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


***** lsmod *****


rtl8180                35838  0 
mac80211              541819  1 rtl8180
eeprom_93cx6           13168  1 rtl8180
cfg80211              453853  2 rtl8180,mac80211


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.120
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             68.105.28.11
    DNS:             68.105.29.11
    DNS:             68.105.28.12




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8180
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    Wireless@Home:   Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 26 WEP
    Wireless@Home:   Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 16 WEP






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


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=16/100  Signal level=16/100  
                    Encryption key:on
                    ESSID:"Wireless@Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004ef7108b037
                    Extra: Last beacon: 1140ms ago
                    IE: Unknown: 000D576972656C65737340486F6D65
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F010100060000
                    IE: Unknown: DD0C00037F020101000002A44000
          Cell 02 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=46/100  Signal level=46/100  
                    Encryption key:on
                    ESSID:"Wireless@Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000031038f0182
                    Extra: Last beacon: 896ms ago
                    IE: Unknown: 000D576972656C65737340486F6D65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030105
                    IE: Unknown: 0504FF010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1605051300000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180202F4010000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3405051300000000000000000000000000000000000000




***** resolv.conf *****


nameserver 127.0.0.1
search ri.cox.net


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


***** modinfo *****


filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rtl818x/rtl8180/rtl8180.ko
license:        GPL
description:    RTL8180 / RTL8185 PCI wireless driver
author:         Andrea Merello <andreamrl@tiscali.it>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     26D9F55E2AD0AC4518006B9
alias:          pci:v00001432d00007106sv*sd*bc*sc*i*
alias:          pci:v00001186d00003301sv*sd*bc*sc*i*
alias:          pci:v00001186d00003300sv*sd*bc*sc*i*
alias:          pci:v00001799d00006020sv*sd*bc*sc*i*
alias:          pci:v00001799d00006001sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008180sv*sd*bc*sc*i*
alias:          pci:v00001799d0000701Fsv*sd*bc*sc*i*
alias:          pci:v00001799d0000700Fsv*sd*bc*sc*i*
alias:          pci:v000010ECd00008185sv*sd*bc*sc*i*
depends:        mac80211,eeprom_93cx6,cfg80211
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 686 




***** udev rules *****


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:08.0 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:00.1/0000:07:00.0 (rtl8180)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[   12.007191] psmouse serio1: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   12.244888] thinkpad_acpi: WARNING: This firmware may be missing critical bug fixes and/or important features
[   14.394633] rtl8180 0000:07:00.0: enabling device (0000 -> 0003)
[   14.394678] rtl8180 0000:07:00.0: setting latency timer to 64
[   26.692163] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.692924] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.261222] wlan0: authenticate with <MAC address removed>
[   32.324176] wlan0: direct probe to <MAC address removed> (try 1/3)
[   32.528044] wlan0: direct probe to <MAC address removed> (try 2/3)
[   32.732107] wlan0: direct probe to <MAC address removed> (try 3/3)
[   32.936678] wlan0: authentication with <MAC address removed> timed out
[   39.404846] wlan0: authenticate with <MAC address removed>
[   39.436277] wlan0: direct probe to <MAC address removed> (try 1/3)
[   39.640121] wlan0: direct probe to <MAC address removed> (try 2/3)
[   39.844155] wlan0: direct probe to <MAC address removed> (try 3/3)
[   40.048177] wlan0: authentication with <MAC address removed> timed out
[   46.520866] wlan0: authenticate with <MAC address removed>
[   46.552234] wlan0: direct probe to <MAC address removed> (try 1/3)
[   46.756051] wlan0: direct probe to <MAC address removed> (try 2/3)
[   46.960050] wlan0: direct probe to <MAC address removed> (try 3/3)
[   47.164048] wlan0: authentication with <MAC address removed> timed out

```

---

