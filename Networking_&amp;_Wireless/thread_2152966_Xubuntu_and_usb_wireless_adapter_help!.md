---
title: "Xubuntu and usb wireless adapter help!"
date: 2013-06-09
forum: Networking &amp; Wireless
---

### Post by anon17 on 2013-06-09
I am using xubuntu 13.04 and have a netgear wna1000m usb adapter. Right off the bat, the adapter found the wifi, and connected to it. Also, it worked for a little bit using firefox, but then quit. I pulled it out and put it back in, and it would work for like 5 minutes and quit again. The entire time, it has said that it connected to the network, but I would lose internet connection pretty quickly. Help?

---

### Post by varunendra on 2013-06-09
Welcome to the forums anon17 ! :)

While the adapter is plugged in, please follow the "Wireless Script" link in my signature and post back the contents (or pastebin link) of the wireless-info.txt file generated as per instructions there.

Thanks !

---

### Post by kurt18947 on 2013-06-10
I believe (but Varun's script should verify) that the Netgear wna 1000m uses a Realtek 8188CUs chipset.  If so, there is a very nice solution courtesy of Tim Phillips.

[http://ubuntuforums.org/showthread.php?t=2092934](http://ubuntuforums.org/showthread.php?t=2092934)

Posts 9, 10 & 13 in particular.

---

### Post by anon17 on 2013-06-10
```

*************** info trace ***************

***** uname -a *****

Linux anonymous-Dell-DV051 3.8.0-23-generic #34-Ubuntu SMP Wed May 29 20:24:54 UTC 2013 i686 i686 i686 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

***** lspci *****

03:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller [8086:1064] (rev 04)
    Subsystem: Dell Device [1028:01c4]
    Kernel driver in use: e100

***** lsusb *****

Bus 001 Device 008: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 003 Device 002: ID 1241:1177 Belkin F8E842-DL Mouse
Bus 003 Device 003: ID 04d9:1603 Holtek Semiconductor, Inc. Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"Poirier"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


***** rfkill *****

4: phy4: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

rtl8192cu              66659  0 
rtlwifi                69015  1 rtl8192cu
rtl8192c_common        47075  1 rtl8192cu
mac80211              526519  3 rtlwifi,rtl8192c_common,rtl8192cu
cfg80211              436177  2 mac80211,rtlwifi

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Poirier] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Poirier:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 73 WPA WPA2
    12FX03103935:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 92 WEP

  IPv4 Settings:
    Address:         192.168.0.116
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.1.1
    DNS:             192.168.0.1


- Device: eth0  [Auto Ethernet] ------------------------------------------------
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
    Address:         192.168.1.36
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1



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

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Poirier"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001664f8d3cde
                    Extra: Last beacon: 446132ms ago
                    IE: Unknown: 0007506F6972696572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B00010310470010F7A951DD1992F4A2EA44FAF0582AFCE910210005436973636F1023000D4C696E6B7379732045323530301024000776312E302E30321042000234321054000800060050F20400011011000D4C696E6B737973204532353030100800020084103C000103
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"12FX03103935"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000003492597
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 000C313246583033313033393335
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000


***** resolv.conf *****

nameserver 127.0.1.1
search westell.com

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

[   21.530643] rtl8192cu: Chip version 0x10
[   21.613992] rtl8192cu: MAC address: <MAC address removed>
[   21.614001] rtl8192cu: Board Type 0
[   21.614235] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   21.614290] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[   21.986352] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   21.987121] rtlwifi: wireless switch is on
[   30.550990] rtl8192cu: MAC auto ON okay!
[   30.583629] rtl8192cu: Tx queue select: 0x05
[   30.943090] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.943836] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.469282] wlan0: authenticate with <MAC address removed>
[   33.497268] wlan0: send auth to <MAC address removed> (try 1/3)
[   33.521410] wlan0: authenticated
[   33.524034] wlan0: associate with <MAC address removed> (try 1/3)
[   33.527557] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   33.527651] wlan0: associated
[   33.527706] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  125.632214] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  125.643071] rtlwifi: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x0
[  125.643080] rtlwifi: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x0
[  125.643087] rtlwifi: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x0
[  125.643095] rtlwifi: reg 0x608, usbctrl_vendorreq TimeOut! status:0xffffffed value=0xd38000
[ 2723.110296] rtl8192cu: Chip version 0x10
[ 2723.112673] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 2723.112737] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[ 2723.224410] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[ 2723.225671] rtlwifi: wireless switch is on
[ 2729.724925] rtl8192cu: MAC auto ON okay!
[ 2729.759189] rtl8192cu: Tx queue select: 0x05
[ 2730.117854] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 2730.118597] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 2778.058208] rtl8192cu: Chip version 0x10
[ 2778.140312] rtl8192cu: MAC address: <MAC address removed>
[ 2778.140320] rtl8192cu: Board Type 0
[ 2778.140557] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 2778.140614] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[ 2778.140980] ieee80211 phy2: Selected rate control algorithm 'rtl_rc'
[ 2778.141951] rtlwifi: wireless switch is on
[ 2778.198432] rtl8192cu: MAC auto ON okay!
[ 2778.240324] rtl8192cu: Tx queue select: 0x05
[ 2778.604170] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2778.605325] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2780.236885] wlan0: authenticate with <MAC address removed>
[ 2780.260519] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2780.266233] wlan0: authenticated
[ 2780.268052] wlan0: associate with <MAC address removed> (try 1/3)
[ 2780.293489] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[ 2780.293585] wlan0: associated
[ 2780.293641] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2810.325223] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2819.690258] rtl8192cu: Chip version 0x10
[ 2819.772506] rtl8192cu: MAC address: <MAC address removed>
[ 2819.772514] rtl8192cu: Board Type 0
[ 2819.772750] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 2819.772810] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[ 2819.773207] ieee80211 phy3: Selected rate control algorithm 'rtl_rc'
[ 2819.774136] rtlwifi: wireless switch is on
[ 2819.830998] rtl8192cu: MAC auto ON okay!
[ 2819.874657] rtl8192cu: Tx queue select: 0x05
[ 2820.238983] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2820.240482] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2821.856812] wlan0: authenticate with <MAC address removed>
[ 2821.881390] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2821.883846] wlan0: authenticated
[ 2821.888053] wlan0: associate with <MAC address removed> (try 1/3)
[ 2821.898555] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[ 2821.898633] wlan0: associated
[ 2821.898684] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2827.069663] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2833.034192] rtl8192cu: Chip version 0x10
[ 2833.116190] rtl8192cu: MAC address: <MAC address removed>
[ 2833.116198] rtl8192cu: Board Type 0
[ 2833.116434] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 2833.116499] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[ 2833.116861] ieee80211 phy4: Selected rate control algorithm 'rtl_rc'
[ 2833.117692] rtlwifi: wireless switch is on
[ 2833.174623] rtl8192cu: MAC auto ON okay!
[ 2833.218337] rtl8192cu: Tx queue select: 0x05
[ 2833.586942] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2833.587801] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2835.248831] wlan0: authenticate with <MAC address removed>
[ 2835.272647] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2835.278494] wlan0: authenticated
[ 2835.280046] wlan0: associate with <MAC address removed> (try 1/3)
[ 2835.299864] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[ 2835.299945] wlan0: associated
[ 2835.299998] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3628.738601] wlan0: deauthenticated from <MAC address removed> (Reason: 7)
[ 3629.573412] wlan0: authenticate with <MAC address removed>
[ 3629.588714] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3629.603851] wlan0: authenticated
[ 3629.608049] wlan0: associate with <MAC address removed> (try 1/3)
[ 3629.611513] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[ 3629.611603] wlan0: associated
[ 4037.065388] wlan0: deauthenticated from <MAC address removed> (Reason: 7)
[ 4043.657040] wlan0: authenticate with <MAC address removed>
[ 4043.670096] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4043.689701] wlan0: authenticated
[ 4043.692120] wlan0: associate with <MAC address removed> (try 1/3)
[ 4043.698402] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[ 4043.698497] wlan0: associated

****************** done ******************


```

---

### Post by anon17 on 2013-06-10
I attempted to follow Tim's directions, but came to many a dead end, as I am relatively new to Xubuntu.

---

### Post by varunendra on 2013-06-10
> **anon17 said:**
> I attempted to follow Tim's directions, but came to many a dead end, as I am relatively new to Xubuntu.

Let's try a couple of things with the native driver first.

You seem to be using encryption type WPA/WPA2 mixed mode in your router. Please change the encryption to pure WPA2-PSK (AES) only. Then in your xubuntu, open a terminal and run the following commands one-by-one (you may copy-paste them to avoid errors) -
```
sudo modprobe -rfv rtl8192cu
sudo modprobe -v rtl8192cu swenc=Y
```
Then try to connect and see if the connection quality improved. This is a temporary change that will be lost at reboot. We can make it permanent if it seems to help.

---

### Post by anon17 on 2013-06-10
That didn't do the trick...

---

### Post by varunendra on 2013-06-10
> **anon17 said:**
> That didn't do the trick...
Not surprised.

Please run the above two modprobe codes again, then run the wireless_script once more and post the current wireless-info it creates. Along with that, also post the result of -
```
grep -R [[:alnum:]] /sys/module/rtl8192cu/parameters/
```

---

### Post by anon17 on 2013-06-11
> **varunendra said:**
> Not surprised.

Please run the above two modprobe codes again, then run the wireless_script once more and post the current wireless-info it creates. Along with that, also post the result of -
```
grep -R [[:alnum:]] /sys/module/rtl8192cu/parameters/
```


```
*************** info trace ***************

***** uname -a *****


Linux anonymous-Dell-DV051 3.8.0-23-generic #34-Ubuntu SMP Wed May 29 20:24:54 UTC 2013 i686 i686 i686 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring


***** lspci *****


03:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller [8086:1064] (rev 04)
    Subsystem: Dell Device [1028:01c4]
    Kernel driver in use: e100


***** lsusb *****


Bus 001 Device 002: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 003 Device 002: ID 1241:1177 Belkin F8E842-DL Mouse
Bus 003 Device 003: ID 04d9:1603 Holtek Semiconductor, Inc. Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:"12FX03103935"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0




***** rfkill *****


1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


***** lsmod *****


rtl8192cu              66659  0 
rtlwifi                69015  1 rtl8192cu
rtl8192c_common        47075  1 rtl8192cu
mac80211              526519  3 rtlwifi,rtl8192c_common,rtl8192cu
cfg80211              436177  2 mac80211,rtlwifi


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0  [12FX03103935 1] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           18 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Poirier-guest:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    Poirier:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    *12FX03103935:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 78 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.30
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
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


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"12FX03103935"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000149c4e6183
                    Extra: Last beacon: 82676ms ago
                    IE: Unknown: 000C313246583033313033393335
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK




***** resolv.conf *****


nameserver 127.0.1.1
search westell.com


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


[   21.879431] rtl8192cu: Chip version 0x10
[   22.117748] rtl8192cu: MAC address: <MAC address removed>
[   22.117759] rtl8192cu: Board Type 0
[   22.118009] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   22.118068] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[   22.200169] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   22.203950] rtlwifi: wireless switch is on
[   26.367443] rtl8192cu: MAC auto ON okay!
[   26.400582] rtl8192cu: Tx queue select: 0x05
[   26.760176] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.761779] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.397070] wlan0: authenticate with <MAC address removed>
[   28.420661] wlan0: send auth to <MAC address removed> (try 1/3)
[   28.423005] wlan0: authenticated
[   28.424060] wlan0: associate with <MAC address removed> (try 1/3)
[   28.430743] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[   28.430819] wlan0: associated
[   28.430868] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   74.211723] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   77.788952] wlan0: authenticate with <MAC address removed>
[   77.802107] wlan0: send auth to <MAC address removed> (try 1/3)
[   77.873977] wlan0: authenticated
[   77.876034] wlan0: associate with <MAC address removed> (try 1/3)
[   77.882882] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[   77.882963] wlan0: associated
[  123.211895] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  160.685119] rtl8192cu: Chip version 0x10
[  160.767616] rtl8192cu: MAC address: <MAC address removed>
[  160.767625] rtl8192cu: Board Type 0
[  160.767860] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[  160.767915] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[  160.768364] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  160.771080] rtlwifi: wireless switch is on
[  160.795871] rtl8192cu: MAC auto ON okay!
[  160.841875] rtl8192cu: Tx queue select: 0x05
[  161.200911] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  161.201649] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  162.748871] wlan0: authenticate with <MAC address removed>
[  162.773581] wlan0: send auth to <MAC address removed> (try 1/3)
[  162.793250] wlan0: authenticated
[  162.796032] wlan0: associate with <MAC address removed> (try 1/3)
[  162.817033] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[  162.817111] wlan0: associated
[  162.817161] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  208.208999] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  211.784832] wlan0: authenticate with <MAC address removed>
[  211.797472] wlan0: send auth to <MAC address removed> (try 1/3)
[  211.823141] wlan0: authenticated
[  211.824038] wlan0: associate with <MAC address removed> (try 1/3)
[  211.854181] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[  211.854259] wlan0: associated
[  416.182626] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  418.417416] wlan0: authenticate with <MAC address removed>
[  418.431660] wlan0: send auth to <MAC address removed> (try 1/3)
[  418.446986] wlan0: authenticated
[  418.447291] rtl8192cu 1-1:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  418.447300] rtl8192cu 1-1:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  418.447307] rtl8192cu 1-1:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  418.448043] wlan0: associate with <MAC address removed> (try 1/3)
[  418.465619] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  418.465671] wlan0: associated
[  428.469695] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[  428.474096] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  433.224876] wlan0: authenticate with <MAC address removed>
[  433.237542] wlan0: send auth to <MAC address removed> (try 1/3)
[  433.242001] wlan0: authenticated
[  433.242293] rtl8192cu 1-1:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  433.242302] rtl8192cu 1-1:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  433.242308] rtl8192cu 1-1:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  433.244054] wlan0: associate with <MAC address removed> (try 1/3)
[  433.250995] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  433.251050] wlan0: associated


****************** done ******************



```



```
/sys/module/rtl8192cu/parameters/debug:0
/sys/module/rtl8192cu/parameters/swenc:Y
```

---

### Post by varunendra on 2013-06-12
> **anon17 said:**
> ```

  Wireless Access Points (* = current AP)
    Poirier-guest:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    Poirier:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    ***12FX03103935:**   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 78 **[COLOR="#FF0000"]WPA WPA2[/COLOR]**


***** iwlist *****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"**12FX03103935**"
.....
.....
                    IE: IEEE 802.11i/**[COLOR="#FF0000"]WPA2 Version 1[/COLOR]**
                        Group Cipher : **[COLOR="#FF0000"]TKIP[/COLOR]**
                        Pairwise Ciphers (1) : **[COLOR="#FF0000"]TKIP[/COLOR]**
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: **[COLOR="#FF0000"]WPA Version 1[/COLOR]**
                        Group Cipher : **[COLOR="#FF0000"]TKIP[/COLOR]**
                        Pairwise Ciphers (1) : **[COLOR="#FF0000"]TKIP[/COLOR]**
                        Authentication Suites (1) : PSK
```

You are still using WPA/WPA2 mixed mode with TKIP. Please change it to pure WPA2-PSK only with AES, not TKIP.
You will have to login to your router/access-point to change that setting. Don't forget to save the settings before closing the web console (log in again to check whether the settings were saved to pure WPA2-PSK (AES)).

Once this is done, disconnect and reconnect. Run the same two modprobe codes again if needed. Then post back the result.

Thanks.

---

### Post by anon17 on 2013-06-12
> **varunendra said:**
> You are still using WPA/WPA2 mixed mode with TKIP. Please change it to pure WPA2-PSK only with AES, not TKIP.
You will have to login to your router/access-point to change that setting. Don't forget to save the settings before closing the web console (log in again to check whether the settings were saved to pure WPA2-PSK (AES)).

Once this is done, disconnect and reconnect. Run the same two modprobe codes again if needed. Then post back the result.

Thanks.


I have two wireless routers, one of them is the modem, and one of them is a separate entity. I can only access the configuration panel for the modem/router, as they use the same 192.168.1.1. Inside the modem/router settings, I can view the devices, and one of them listed is the other router, which is labeled as a wired computer (probably because it is literally wired with an ethernet cable to the modem), and no way of changing its settings. The router that my wireless adapter continues to attempt to connect to is, of course, the router whose settings I cannot change. Is there some way around the modem?

---

### Post by varunendra on 2013-06-12
> **anon17 said:**
> Inside the modem/router settings, I can view the devices, and one of them listed is the other router, which is labeled as a wired computer (probably because it is literally wired with an ethernet cable to the modem), and **no way of changing its settings**. The router that my wireless adapter continues to attempt to connect to is, of course, the router whose settings I cannot change. Is there some way around the modem?
I'm afraid not.
While you can still use them as you are currently, the performance of the mixed mode is almost always buggy, as you are facing now.

But any device that can act as a wireless access-point or hotspot definitely gives you the control, among other settings, to decide which encryption type to use. Whether you can change it or not solely depends upon whether you have access to its admin control panel or not (that is, whether you have its admin id-password or not).

So, do you have admin access to these devices (web interface of their admin console)?

If yes, what are the exact model nos. of these two routers/access-points? I'd be interested in taking a look at their user manual.

---

### Post by anon17 on 2013-06-12
> **varunendra said:**
> I'm afraid not.
While you can still use them as you are currently, the performance of the mixed mode is almost always buggy, as you are facing now.

But any device that can act as a wireless access-point or hotspot definitely gives you the control, among other settings, to decide which encryption type to use. Whether you can change it or not solely depends upon whether you have access to its admin control panel or not (that is, whether you have its admin id-password or not).

So, do you have admin access to these devices (web interface of their admin console)?

If yes, what are the exact model nos. of these two routers/access-points? I'd be interested in taking a look at their user manual.

I have access to the modem's interface, which is a Westell model A90-750018-07. I don't have access to the router's interface, only because I can't even find it, (because they share the same address), which is a Linksys E2500.

---

### Post by gordintoronto on 2013-06-12
Turn off one device, and change the IP address of the other. Having two devices at 192.168.1.1 is sure to be a problem.

---

