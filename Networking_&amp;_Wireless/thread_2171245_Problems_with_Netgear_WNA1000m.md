---
title: "Problems with Netgear WNA1000m"
date: 2013-08-29
forum: Networking &amp; Wireless
---

### Post by superluigibro7 on 2013-08-29
Hi,

I recently installed Ubuntu 13.04, and I'm having trouble with my wireless card, a Netgear WNA1000m. I've searched the internet for solutions, but none seem to work.

The problem isn't that the card is not recognized, but that it drops the connection every few minutes and is sometimes unable to reconnect to my network. Also, when it is connected, wifi performance is usually very slow.

Any help would be appreciated. Thanks.

---

### Post by kurt18947 on 2013-08-29
Perhaps you can be a guinea pig to try something.  I was using another RTL8188CUs powered device and having the same issue, the adapter would work for a few minutes and then just quit.  It never disconnected from the router, there was always a wifi signal but no data.  I was checking this device on Ubuntu13.10 and it worked for a few minutes then ceased responding. This time when I checked 'dmesg', there was a clue.  It said I needed to install a package "nss-myhostname".  Other versions/distros may not have that package in their repository but may instead have "libnss-myhostname" or similar.    I installed that package, rebooted, reconnected and had no more drops.  It will be interesting to see if you and others have the same experience.  I've not had a signal strength issue with that adapter, the signal has been remarkably strong for such a little device.  Speed was not as good as with the driver from RealTek but still not bad, about 72 mb./sec according to iwconfig vs. 135-150 using RealTek's driver.    I've only tried this on one machine/install so my experience may be an outlier, or only works with the newest kernels or releases.

---

### Post by superluigibro7 on 2013-08-29
Thanks for the help, but while I was able to install the package, I found that I was still having problems. Sometimes it works perfectly fine for a few minutes, but then it slows down or disconnects altogether. The package I installed was "libnss-myhostname" in case that makes a difference; "mss-myhostname" did not seem to be available through the terminal.

---

### Post by kurt18947 on 2013-08-30
> **superluigibro7 said:**
> Thanks for the help, but while I was able to install the package, I found that I was still having problems. Sometimes it works perfectly fine for a few minutes, but then it slows down or disconnects altogether. The package I installed was "libnss-myhostname" in case that makes a difference; "mss-myhostname" did not seem to be available through the terminal.

Yes, I think that's the equivalent in 13.04, I didn't find "mss-myhostname" in 13.04 either, that was in 13.10.  My fix seems to work in 12.04.3 which uses a 3.5.x kernel but the other packages are probably different than 13.04.  I tried my fix on 13.04 that previously had Tim Phillips' modified Realtek driver installed.  I couldn't get it to work well either but thought that may have been due to remnants or changes from the Tim Phillips/RealTek driver.  Perhaps not, maybe it just doesn't work on 13.04.    It looks like this is not a universal fix which is what I was wondering.  What happens if you unplug the dongle, wait a second and plug it back in?  I did that once on 13.10.

---

### Post by superluigibro7 on 2013-08-30
> **kurt18947 said:**
> Yes, I think that's the equivalent in 13.04, I didn't find "mss-myhostname" in 13.04 either, that was in 13.10.  My fix seems to work in 12.04.3 which uses a 3.5.x kernel but the other packages are probably different than 13.04.  I tried my fix on 13.04 that previously had Tim Phillips' modified Realtek driver installed.  I couldn't get it to work well either but thought that may have been due to remnants or changes from the Tim Phillips/RealTek driver.  Perhaps not, maybe it just doesn't work on 13.04.    It looks like this is not a universal fix which is what I was wondering.  What happens if you unplug the dongle, wait a second and plug it back in?  I did that once on 13.10.

When I unplug it and plug it back in, nothing different really seems to happen. Sometimes it'll connect, sometimes it won't, and sometimes it connects but without any internet.

---

### Post by kurt18947 on 2013-08-30
> **superluigibro7 said:**
> When I unplug it and plug it back in, nothing different really seems to happen. Sometimes it'll connect, sometimes it won't, and sometimes it connects but without any internet.

Hmm, you're having different symptoms than I've had.  I've never had a problem connecting to the router, my issue was with internet connectivity.  I wonder if there's something with 13.04 that is problematic.   I thought 12.04.3 is pretty similar to 13.04 but perhaps not.  The adapter seems to work very well with 12.04.3 with no stoppages.  I did have to do the unplug/replug routine a couple times with 13.10 but being a work in progress, I don't expect a smooth ride.

---

### Post by varunendra on 2013-08-31
First off, Welcome to the forums superluigibro7 !

To provide us technical details of your wireless setup, please follow the "Wireless Script" link in my signature, follow the instructions in the linked post and post back the result file that the script creates.

Hopefully, we may get some useful clues to be able to fix the problem.

---

### Post by superluigibro7 on 2013-09-01
> **varunendra said:**
> First off, Welcome to the forums superluigibro7 !

To provide us technical details of your wireless setup, please follow the "Wireless Script" link in my signature, follow the instructions in the linked post and post back the result file that the script creates.

Hopefully, we may get some useful clues to be able to fix the problem.

Alright, here are the results:

```


*************** info trace ***************


***** uname -a *****


Linux jeremy-Inspiron-530 3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 23:12:18 UTC 2013 i686 i686 i686 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring


***** lspci *****


00:19.0 Ethernet controller [0200]: Intel Corporation 82562V-2 10/100 Network Connection [8086:10c0] (rev 02)
    Subsystem: Dell Inspiron 530 [1028:020d]
    Kernel driver in use: e1000e


***** lsusb *****


Bus 001 Device 013: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 002 Device 002: ID 046d:0825 Logitech, Inc. Webcam C270
Bus 005 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 007 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan2     IEEE 802.11bgn  ESSID:"Nostrings3"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0




***** rfkill *****


6: phy6: Wireless LAN
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


- Device: wlan2  [Nostrings3] --------------------------------------------------
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
    75ZP3:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    VLPX9:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    BOJLQWQ4:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    *Nostrings3:     Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2


  IPv4 Settings:
    Address:         10.0.0.15
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1


    DNS:             10.0.0.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
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


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****


wlan2     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"Nostrings3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000bdece1d
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 000A4E6F737472696E677333
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030102
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1602001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: DD820050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F593111021000D4E6574676561722C20496E632E10230007574E523230303010240007574E523230303010420004353637381054000800060050F204000110110007574E5232303030100800020084103C000103




***** resolv.conf *****


nameserver 127.0.1.1


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


filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     B60B278C1942CBFF27FC8A0
alias:          usb:v7392p7822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p624Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p330Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3309d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0061d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8186d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17ABd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0056d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p341Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp2103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp2102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p1201d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp317Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v9846p9041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4855p0091d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4855p0090d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3359d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3358d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p648Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p4902d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3308d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3357d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v103Cp1629d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4856p0091d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0EB0p9071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0052d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp5088d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8189d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8188d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE033d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp11F2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8178d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8754d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp819Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp818Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8170d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp018Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8191d*dc*dsc*dp*ic*isc*ip*in*
depends:        rtlwifi,mac80211,rtl8192c-common
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 686 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     FA8C819FC50E5EFF6562FED
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E6FCDEDFF185E90DD643BE4
depends:        mac80211
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 686 




***** udev rules *****


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x0846:0x9041 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x0846:0x9041 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


# USB device 0x0846:0x9041 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"


***** dmesg *****


[  343.604689] rtl8192cu: Chip version 0x10
[  343.686801] rtl8192cu: MAC address: <MAC address removed>
[  343.686806] rtl8192cu: Board Type 0
[  343.687047] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[  343.687086] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[  343.726227] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  343.728564] rtlwifi: wireless switch is on
[  343.744430] rtl8192cu: MAC auto ON okay!
[  343.784554] rtl8192cu: Tx queue select: 0x05
[  344.180551] rtlwifi: reg 0x32, usbctrl_vendorreq TimeOut! status:0xffffffb9 value=0xa200
[  344.227300] rtlwifi: reg 0x33, usbctrl_vendorreq TimeOut! status:0xffffffb9 value=0xa301
[  344.274050] rtlwifi: reg 0x33, usbctrl_vendorreq TimeOut! status:0xffffffb9 value=0xa402
[  344.316550] rtlwifi: reg 0x33, usbctrl_vendorreq TimeOut! status:0xffffffb9 value=0x30005
[  345.578883] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  345.579608] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  370.518237] rtl8192cu: Chip version 0x10
[  370.600449] rtl8192cu: MAC address: <MAC address removed>
[  370.600453] rtl8192cu: Board Type 0
[  370.600694] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[  370.600734] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[  370.600944] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[  370.601828] rtlwifi: wireless switch is on
[  370.639073] rtl8192cu: MAC auto ON okay!
[  370.678454] rtl8192cu: Tx queue select: 0x05
[  371.777676] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  371.778372] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  373.412504] wlan2: authenticate with <MAC address removed>
[  373.438395] wlan2: send auth to <MAC address removed> (try 1/3)
[  373.451278] wlan2: authenticated
[  373.452175] wlan2: associate with <MAC address removed> (try 1/3)
[  373.465244] wlan2: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=8)
[  373.465290] wlan2: associated
[  373.465335] IPv6: ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[  373.510318] wlan2: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC address removed>
[  427.327128] wlan2: deauthenticating from <MAC address removed> by local choice (reason=3)
[  436.502260] rtl8192cu: Chip version 0x10
[  436.585090] rtl8192cu: MAC address: <MAC address removed>
[  436.585095] rtl8192cu: Board Type 0
[  436.585334] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[  436.585380] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[  436.585584] ieee80211 phy2: Selected rate control algorithm 'rtl_rc'
[  436.587783] rtlwifi: wireless switch is on
[  436.627478] rtl8192cu: MAC auto ON okay!
[  436.663591] rtl8192cu: Tx queue select: 0x05
[  437.025989] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  437.027442] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  438.633695] wlan2: authenticate with <MAC address removed>
[  438.661780] wlan2: send auth to <MAC address removed> (try 1/3)
[  438.674005] wlan2: authenticated
[  438.676025] wlan2: associate with <MAC address removed> (try 1/3)
[  438.681886] wlan2: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=8)
[  438.681935] wlan2: associated
[  438.681977] IPv6: ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[  438.739027] wlan2: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC address removed>
[  507.034410] wlan2: deauthenticating from <MAC address removed> by local choice (reason=3)
[  517.430257] rtl8192cu: Chip version 0x10
[  517.513209] rtl8192cu: MAC address: <MAC address removed>
[  517.513215] rtl8192cu: Board Type 0
[  517.513454] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[  517.513498] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[  517.513706] ieee80211 phy3: Selected rate control algorithm 'rtl_rc'
[  517.515900] rtlwifi: wireless switch is on
[  517.551714] rtl8192cu: MAC auto ON okay!
[  517.592838] rtl8192cu: Tx queue select: 0x05
[  517.952620] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  517.953685] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  519.596499] wlan2: authenticate with <MAC address removed>
[  519.621264] wlan2: send auth to <MAC address removed> (try 1/3)
[  519.623626] wlan2: authenticated
[  519.624058] wlan2: associate with <MAC address removed> (try 1/3)
[  519.630756] wlan2: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=8)
[  519.630803] wlan2: associated
[  519.630844] IPv6: ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[  519.635016] wlan2: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC address removed>
[  565.105017] wlan2: deauthenticating from <MAC address removed> by local choice (reason=3)
[  685.366328] rtl8192cu: Chip version 0x10
[  685.448325] rtl8192cu: MAC address: <MAC address removed>
[  685.448330] rtl8192cu: Board Type 0
[  685.448571] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[  685.448615] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[  685.448825] ieee80211 phy4: Selected rate control algorithm 'rtl_rc'
[  685.451025] rtlwifi: wireless switch is on
[  685.487704] rtl8192cu: MAC auto ON okay!
[  685.526706] rtl8192cu: Tx queue select: 0x05
[  687.136595] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  687.137358] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  689.104545] wlan2: authenticate with <MAC address removed>
[  689.132505] wlan2: send auth to <MAC address removed> (try 1/3)
[  689.148865] wlan2: authenticated
[  689.152025] wlan2: associate with <MAC address removed> (try 1/3)
[  689.194761] wlan2: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=8)
[  689.194811] wlan2: associated
[  689.194857] IPv6: ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[  689.209139] wlan2: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC address removed>
[  771.440653] wlan2: deauthenticating from <MAC address removed> by local choice (reason=3)
[  776.474325] rtl8192cu: Chip version 0x10
[  776.557448] rtl8192cu: MAC address: <MAC address removed>
[  776.557454] rtl8192cu: Board Type 0
[  776.557692] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[  776.557736] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[  776.557943] ieee80211 phy5: Selected rate control algorithm 'rtl_rc'
[  776.560236] rtlwifi: wireless switch is on
[  776.597491] rtl8192cu: MAC auto ON okay!
[  776.636088] rtl8192cu: Tx queue select: 0x05
[  776.993590] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  776.994303] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  778.644471] wlan2: authenticate with <MAC address removed>
[  778.669510] wlan2: send auth to <MAC address removed> (try 1/3)
[  778.671990] wlan2: authenticated
[  778.676113] wlan2: associate with <MAC address removed> (try 1/3)
[  778.684125] wlan2: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=8)
[  778.684178] wlan2: associated
[  778.684222] IPv6: ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[  778.706630] wlan2: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC address removed>
[  825.941415] wlan2: deauthenticating from <MAC address removed> by local choice (reason=3)
[  829.156533] wlan2: authenticate with <MAC address removed>
[  829.190407] wlan2: send auth to <MAC address removed> (try 1/3)
[  829.194146] wlan2: authenticated
[  829.196183] wlan2: associate with <MAC address removed> (try 1/3)
[  829.205286] wlan2: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=8)
[  829.205345] wlan2: associated
[  829.292336] wlan2: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC address removed>
[ 1015.243297] wlan2: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1018.032620] wlan2: authenticate with <MAC address removed>
[ 1018.057655] wlan2: send auth to <MAC address removed> (try 1/3)
[ 1018.060517] wlan2: authenticated
[ 1018.064081] wlan2: associate with <MAC address removed> (try 1/3)
[ 1018.080518] wlan2: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=8)
[ 1018.080566] wlan2: associated
[ 1018.119151] wlan2: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC address removed>
[ 1057.637265] wlan2: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1072.790205] rtl8192cu: Chip version 0x10
[ 1072.872423] rtl8192cu: MAC address: <MAC address removed>
[ 1072.872428] rtl8192cu: Board Type 0
[ 1072.872669] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 1072.872715] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[ 1072.872916] ieee80211 phy6: Selected rate control algorithm 'rtl_rc'
[ 1072.873802] rtlwifi: wireless switch is on
[ 1072.911839] rtl8192cu: MAC auto ON okay!
[ 1072.950804] rtl8192cu: Tx queue select: 0x05
[ 1073.310280] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 1073.311043] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 1092.364318] rtl8192cu: MAC auto ON okay!
[ 1092.397452] rtl8192cu: Tx queue select: 0x05
[ 1092.767904] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 1094.428491] wlan2: authenticate with <MAC address removed>
[ 1094.472736] wlan2: send auth to <MAC address removed> (try 1/3)
[ 1094.487631] wlan2: authenticated
[ 1094.492017] wlan2: associate with <MAC address removed> (try 1/3)
[ 1094.497478] wlan2: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[ 1094.497526] wlan2: associated
[ 1094.497569] IPv6: ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[ 1094.561628] wlan2: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC address removed>


****************** done ******************



```

---

### Post by praseodym on 2013-09-01
Update the driver according to this:

[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107)

---

### Post by superluigibro7 on 2013-09-01
> **praseodym said:**
> Update the driver according to this:

[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107)

Well, after trying that, the device does not seem to be recognized at all. The light on the card does not turn on like it previously did, and it is unable to find any networks.

---

### Post by praseodym on 2013-09-01
Check now:
```

iwconfig
rfkill list
lsmod
dmesg | grep 8192
```

---

### Post by superluigibro7 on 2013-09-02
> **praseodym said:**
> Check now:
```

iwconfig
rfkill list
lsmod
dmesg | grep 8192
```

It still isn't working...

Here are the results of the above code:

```
jeremy@jeremy-Inspiron-530:~$ iwconfiglo        no wireless extensions.


eth0      no wireless extensions.


jeremy@jeremy-Inspiron-530:~$ rfkill list
jeremy@jeremy-Inspiron-530:~$ lsmod
Module                  Size  Used by
coretemp               13131  0 
uvcvideo               71279  0 
parport_pc             27504  0 
ppdev                  12817  0 
videobuf2_vmalloc      12920  1 uvcvideo
dcdbas                 14021  0 
bnep                   17669  2 
videobuf2_memops       13042  1 videobuf2_vmalloc
rfcomm                 37420  0 
bluetooth             202109  10 bnep,rfcomm
videobuf2_core         39161  1 uvcvideo
snd_hda_codec_realtek    63791  1 
snd_usb_audio         114925  1 
snd_hda_intel          38307  3 
microcode              18286  0 
videodev               95806  2 uvcvideo,videobuf2_core
snd_usbmidi_lib        24210  1 snd_usb_audio
snd_hda_codec         117580  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  2 snd_usb_audio,snd_hda_codec
psmouse                81065  0 
serio_raw              13031  0 
snd_pcm                80890  3 snd_usb_audio,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  2 snd_usbmidi_lib,snd_seq_midi
i915                  535544  3 
lpc_ich                16925  0 
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
video                  18894  1 i915
mac_hid                13037  0 
drm_kms_helper         47545  1 i915
snd_timer              24411  2 snd_pcm,snd_seq
drm                   228489  4 i915,drm_kms_helper
snd                    56485  19 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12600  1 snd
i2c_algo_bit           13197  1 i915
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
hid_logitech_dj        18172  0 
hid_generic            12484  0 
usbhid                 41805  1 hid_logitech_dj
hid                    82666  3 hid_generic,usbhid,hid_logitech_dj
floppy                 55441  0 
e1000e                174556  0 
jeremy@jeremy-Inspiron-530:~$ dmesg | grep 8192
[    0.136084] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.136111] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.136135] TCP: Hash tables configured (established 8192 bind 8192)
[    0.490912] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
jeremy@jeremy-Inspiron-530:~$ 
```

---

### Post by praseodym on 2013-09-02
The driver is not loaded:
```

sudo modprobe -v 8192cu
```
If it works, make it permanent with:
```

echo 8192cu | sudo tee -a /etc/modules
```

---

### Post by superluigibro7 on 2013-09-02
> **praseodym said:**
> The driver is not loaded:
```

sudo modprobe -v 8192cu
```
If it works, make it permanent with:
```

echo 8192cu | sudo tee -a /etc/modules
```

That didn't seem to do anything. I didn't make it permanent though since it's not working, so should I still try that?

---

### Post by praseodym on 2013-09-02
Check now:
```

lsmod
iwconfig
sudo iwlist scan
ifconfig -a
cat /etc/resolv.conf
route -n
```

---

### Post by superluigibro7 on 2013-09-02
> **praseodym said:**
> Check now:
```

lsmod
iwconfig
sudo iwlist scan
ifconfig -a
cat /etc/resolv.conf
route -n
```

Alright, here it is:

```
jeremy@jeremy-Inspiron-530:~$ lsmodModule                  Size  Used by
parport_pc             27504  0 
ppdev                  12817  0 
rfcomm                 37420  0 
bnep                   17669  2 
bluetooth             202109  10 bnep,rfcomm
snd_hda_codec_realtek    63791  1 
coretemp               13131  0 
dcdbas                 14021  0 
snd_usb_audio         114925  1 
snd_hda_intel          38307  3 
snd_hda_codec         117580  2 snd_hda_codec_realtek,snd_hda_intel
snd_usbmidi_lib        24210  1 snd_usb_audio
snd_hwdep              13272  2 snd_usb_audio,snd_hda_codec
snd_seq_midi           13132  0 
microcode              18286  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  2 snd_usbmidi_lib,snd_seq_midi
i915                  535544  3 
uvcvideo               71279  0 
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
videobuf2_core         39161  1 uvcvideo
video                  18894  1 i915
drm_kms_helper         47545  1 i915
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
snd_pcm                80890  3 snd_usb_audio,snd_hda_codec,snd_hda_intel
hid_logitech_dj        18172  0 
videodev               95806  2 uvcvideo,videobuf2_core
mac_hid                13037  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_timer              24411  2 snd_pcm,snd_seq
drm                   228489  4 i915,drm_kms_helper
snd                    56485  19 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
lpc_ich                16925  0 
i2c_algo_bit           13197  1 i915
psmouse                81065  0 
soundcore              12600  1 snd
lp                     13299  0 
serio_raw              13031  0 
parport                40753  3 lp,ppdev,parport_pc
hid_generic            12484  0 
usbhid                 41805  1 hid_logitech_dj
hid                    82666  3 hid_generic,usbhid,hid_logitech_dj
floppy                 55441  0 
e1000e                174556  0 
jeremy@jeremy-Inspiron-530:~$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.


jeremy@jeremy-Inspiron-530:~$ sudo iwlist scan
[sudo] password for jeremy: 
lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


jeremy@jeremy-Inspiron-530:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:21:70:5a:fe:43  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fdfc0000-fdfe0000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17400 (17.4 KB)  TX bytes:17400 (17.4 KB)


jeremy@jeremy-Inspiron-530:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
jeremy@jeremy-Inspiron-530:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
jeremy@jeremy-Inspiron-530:~$ 



```

---

### Post by praseodym on 2013-09-02
Obviously, the driver is not installed. Download these files and save them in "Downloads":

[https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb](https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu2_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu2_all.deb)

Installation via:
```

sudo dpkg -i ~/Downloads/*.deb
sudo modprobe -v 8192cu
```

---

### Post by superluigibro7 on 2013-09-02
> **praseodym said:**
> Obviously, the driver is not installed. Download these files and save them in "Downloads":

[https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb](https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu2_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu2_all.deb)

Installation via:
```

sudo dpkg -i ~/Downloads/*.deb
sudo modprobe -v 8192cu
```

Strange, the installation seemed to go fine, yet it still isn't working.

---

### Post by varunendra on 2013-09-02
While praseodym comes back, please run the 'wireless_script' again and post back the new report.

---

### Post by superluigibro7 on 2013-09-03
> **varunendra said:**
> While praseodym comes back, please run the 'wireless_script' again and post back the new report.

Okay, here it is:

```


*************** info trace ***************


***** uname -a *****


Linux jeremy-Inspiron-530 3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 23:12:18 UTC 2013 i686 i686 i686 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring


***** lspci *****


00:19.0 Ethernet controller [0200]: Intel Corporation 82562V-2 10/100 Network Connection [8086:10c0] (rev 02)
    Subsystem: Dell Inspiron 530 [1028:020d]
    Kernel driver in use: e1000e


***** lsusb *****


Bus 001 Device 005: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 002 Device 002: ID 046d:0825 Logitech, Inc. Webcam C270
Bus 005 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 007 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** PCMCIA Card Info *****




***** iwconfig *****




***** rfkill *****




***** lsmod *****




***** nm-tool *****


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
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


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****




***** resolv.conf *****




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
blacklist rtl8192cu


***** modinfo *****




***** udev rules *****


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x0846:0x9041 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x0846:0x9041 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


# USB device 0x0846:0x9041 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"


***** dmesg *****




****************** done ******************



```

---

### Post by praseodym on 2013-09-03
Thats strange, no "lsmod" output:
```

lsmod
iwconfig
route -n
cat /etc/resolv.conf
rfkill list
dmesg | grep 8192
```

---

### Post by superluigibro7 on 2013-09-03
Ok,

```
jeremy@jeremy-Inspiron-530:~$ lsmodModule                  Size  Used by
nls_iso8859_1          12617  0 
usb_storage            47684  0 
coretemp               13131  0 
dcdbas                 14021  0 
snd_hda_codec_realtek    63791  1 
uvcvideo               71279  0 
snd_usb_audio         114925  1 
videobuf2_vmalloc      12920  1 uvcvideo
microcode              18286  0 
snd_hda_intel          38307  3 
bnep                   17669  2 
videobuf2_memops       13042  1 videobuf2_vmalloc
rfcomm                 37420  0 
parport_pc             27504  0 
snd_usbmidi_lib        24210  1 snd_usb_audio
ppdev                  12817  0 
bluetooth             202109  10 bnep,rfcomm
snd_hda_codec         117580  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  2 snd_usb_audio,snd_hda_codec
snd_seq_midi           13132  0 
videobuf2_core         39161  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
mac_hid                13037  0 
snd_rawmidi            25114  2 snd_usbmidi_lib,snd_seq_midi
videodev               95806  2 uvcvideo,videobuf2_core
i915                  535544  3 
snd_pcm                80890  3 snd_usb_audio,snd_hda_codec,snd_hda_intel
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
video                  18894  1 i915
drm_kms_helper         47545  1 i915
snd_timer              24411  2 snd_pcm,snd_seq
psmouse                81065  0 
snd                    56485  19 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
serio_raw              13031  0 
drm                   228489  4 i915,drm_kms_helper
lpc_ich                16925  0 
i2c_algo_bit           13197  1 i915
soundcore              12600  1 snd
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
hid_logitech_dj        18172  0 
hid_generic            12484  0 
usbhid                 41805  1 hid_logitech_dj
hid                    82666  3 hid_generic,usbhid,hid_logitech_dj
floppy                 55441  0 
e1000e                174556  0 
jeremy@jeremy-Inspiron-530:~$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.


jeremy@jeremy-Inspiron-530:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
jeremy@jeremy-Inspiron-530:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
jeremy@jeremy-Inspiron-530:~$ rfkill list
jeremy@jeremy-Inspiron-530:~$ dmesg | grep 8192
[    0.140099] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.140127] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.140150] TCP: Hash tables configured (established 8192 bind 8192)
[    0.494944] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.819233] i8042: PNP: No PS/2 controller found. Probing ports directly.
jeremy@jeremy-Inspiron-530:~$ 
```

---

### Post by praseodym on 2013-09-03
```

modprobe -c | grep -i "0846.*9041" 
modinfo rtl8192cu
modinfo 8192cu
locate 8192cu | grep lib
grep 8192 /etc/modprobe.d/*
```
please

---

### Post by superluigibro7 on 2013-09-03
Here it is:

```
jeremy@jeremy-Inspiron-530:~$ modprobe -c | grep -i "0846.*9041"alias usb:v0846p9041d*dc*dsc*dp*ic*isc*ip*in* rtl8192cu
jeremy@jeremy-Inspiron-530:~$ modinfo rtl8192cu
filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
srcversion:     B60B278C1942CBFF27FC8A0
alias:          usb:v7392p7822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p624Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p330Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3309d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0061d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8186d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17ABd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0056d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p341Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp2103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp2102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p1201d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp317Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v9846p9041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4855p0091d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4855p0090d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3359d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3358d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p648Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p4902d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3308d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3357d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v103Cp1629d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4856p0091d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0EB0p9071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0052d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp5088d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8189d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8188d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE033d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp11F2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8178d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8754d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp819Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp818Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8170d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp018Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8191d*dc*dsc*dp*ic*isc*ip*in*
depends:        rtlwifi,mac80211,rtl8192c-common
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 686 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
jeremy@jeremy-Inspiron-530:~$ modinfo 8192cu
filename:       /lib/modules/3.8.0-29-generic/updates/dkms/8192cu.ko
version:        v3.4.4_4749.20121105
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     F74B758873092476C5A3F15
alias:          usb:v0BDAp8186d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17ABd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0061d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p624Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp2103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp2102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4855p0091d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0056d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p341Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3309d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p330Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p1201d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3358d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3359d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp317Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p4902d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4856p0091d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp5088d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3357d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4855p0090d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p648Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3308d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v103Cp1629d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE033d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0EB0p9071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8189d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0052d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8178d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp018Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp818Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8754d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8170d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8191d*dc*dsc*dp*ic*isc*ip*in*
depends:        
vermagic:       3.8.0-29-generic SMP mod_unload modversions 686 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:charp
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_force_iol:Force to enable IOL (bool)
parm:           rtw_intel_class_mode:The intel class mode [0: off, 1: on] (uint)
parm:           rtw_mc2u_disable:int
jeremy@jeremy-Inspiron-530:~$ locate 8192cu | grep lib
/lib/firmware/rtlwifi/rtl8192cufw.bin
/lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu
/lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
/lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu
/lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
/lib/modules/3.8.0-29-generic/updates/dkms/8192cu.ko
/var/lib/dkms/rtl8192cu-tjp
/var/lib/dkms/rtl8192cu-tjp/1.6
/var/lib/dkms/rtl8192cu-tjp/kernel-3.8.0-29-generic-i686
/var/lib/dkms/rtl8192cu-tjp/1.6/3.8.0-29-generic
/var/lib/dkms/rtl8192cu-tjp/1.6/build
/var/lib/dkms/rtl8192cu-tjp/1.6/source
/var/lib/dkms/rtl8192cu-tjp/1.6/3.8.0-29-generic/i686
/var/lib/dkms/rtl8192cu-tjp/1.6/3.8.0-29-generic/i686/log
/var/lib/dkms/rtl8192cu-tjp/1.6/3.8.0-29-generic/i686/module
/var/lib/dkms/rtl8192cu-tjp/1.6/3.8.0-29-generic/i686/log/make.log
/var/lib/dkms/rtl8192cu-tjp/1.6/3.8.0-29-generic/i686/module/8192cu.ko
/var/lib/dkms/rtl8192cu-tjp/1.6/build/Kconfig
/var/lib/dkms/rtl8192cu-tjp/1.6/build/Makefile
/var/lib/dkms/rtl8192cu-tjp/1.6/build/clean
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core
/var/lib/dkms/rtl8192cu-tjp/1.6/build/dkms.conf
/var/lib/dkms/rtl8192cu-tjp/1.6/build/hal
/var/lib/dkms/rtl8192cu-tjp/1.6/build/ifcfg-wlan0
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include
/var/lib/dkms/rtl8192cu-tjp/1.6/build/os_dep
/var/lib/dkms/rtl8192cu-tjp/1.6/build/wlan0dhcp
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/efuse
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/rtw_br_ext.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/rtw_cmd.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/rtw_debug.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/rtw_eeprom.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/rtw_ieee80211.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/rtw_io.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/rtw_ioctl_query.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/rtw_ioctl_rtl.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/rtw_ioctl_set.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/rtw_iol.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/rtw_mlme.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/rtw_mlme_ext.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/rtw_mp.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/rtw_mp_ioctl.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/rtw_p2p.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/rtw_pwrctrl.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/rtw_recv.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/rtw_rf.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/rtw_security.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/rtw_sta_mgt.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/rtw_wlan_util.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/rtw_xmit.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/core/efuse/rtw_efuse.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/hal/hal_init.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/hal/rtl8192c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/hal/rtl8192c/rtl8192c_cmd.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/hal/rtl8192c/rtl8192c_dm.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/hal/rtl8192c/rtl8192c_hal_init.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/hal/rtl8192c/rtl8192c_mp.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/hal/rtl8192c/rtl8192c_phycfg.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/hal/rtl8192c/rtl8192c_rf6052.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/hal/rtl8192c/rtl8192c_rxdesc.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/hal/rtl8192c/rtl8192c_sreset.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/hal/rtl8192c/usb
/var/lib/dkms/rtl8192cu-tjp/1.6/build/hal/rtl8192c/usb/Hal8192CUHWImg.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/hal/rtl8192c/usb/Hal8192CUHWImg_wowlan.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/hal/rtl8192c/usb/rtl8192cu_led.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/hal/rtl8192c/usb/rtl8192cu_recv.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/hal/rtl8192c/usb/rtl8192cu_xmit.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/hal/rtl8192c/usb/usb_halinit.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/hal/rtl8192c/usb/usb_ops_ce.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/hal/rtl8192c/usb/usb_ops_linux.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/hal/rtl8192c/usb/usb_ops_xp.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/Hal8192CEHWImg.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/Hal8192CPhyCfg.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/Hal8192CPhyReg.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/Hal8192CUHWImg.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/Hal8192CUHWImg_wowlan.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/Hal8192DEHWImg.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/Hal8192DETestHWImg.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/Hal8192DPhyCfg.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/Hal8192DPhyReg.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/Hal8192DUHWImg.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/Hal8192DUHWImg_wowlan.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/Hal8192DUTestHWImg.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/autoconf.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/basic_types.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/byteorder
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/circ_buf.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/cmd_osdep.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/drv_conf.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/drv_types.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/drv_types_ce.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/drv_types_linux.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/drv_types_xp.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/ethernet.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/farray.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/h2clbk.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/hal_init.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/ieee80211.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/ieee80211_ext.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/if_ether.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/ioctl_cfg80211.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/ip.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/mlme_osdep.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/mp_custom_oid.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/nic_spec.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/osdep_ce_service.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/osdep_intf.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/osdep_service.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/pci_hal.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/pci_ops.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/pci_osintf.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/recv_osdep.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtl8192c_cmd.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtl8192c_dm.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtl8192c_event.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtl8192c_hal.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtl8192c_led.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtl8192c_recv.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtl8192c_rf.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtl8192c_spec.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtl8192c_sreset.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtl8192c_xmit.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtl8192d_cmd.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtl8192d_dm.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtl8192d_hal.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtl8192d_led.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtl8192d_recv.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtl8192d_rf.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtl8192d_spec.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtl8192d_xmit.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_android.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_br_ext.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_byteorder.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_cmd.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_debug.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_eeprom.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_efuse.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_event.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_ht.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_io.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_ioctl.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_ioctl_query.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_ioctl_rtl.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_ioctl_set.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_iol.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_led.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_mlme.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_mlme_ext.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_mp.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_mp_ioctl.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_mp_phy_regdef.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_p2p.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_pwrctrl.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_qos.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_recv.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_rf.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_security.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_version.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/rtw_xmit.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/sdio_hal.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/sdio_ops.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/sdio_ops_ce.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/sdio_ops_linux.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/sdio_ops_xp.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/sdio_osintf.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/sta_info.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/usb_hal.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/usb_ops.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/usb_osintf.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/usb_vendor_req.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/wifi.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/wlan_bssdef.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/xmit_osdep.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/byteorder/big_endian.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/byteorder/generic.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/byteorder/little_endian.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/byteorder/swab.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/include/byteorder/swabb.h
/var/lib/dkms/rtl8192cu-tjp/1.6/build/os_dep/linux
/var/lib/dkms/rtl8192cu-tjp/1.6/build/os_dep/osdep_service.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/os_dep/linux/ioctl_cfg80211.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/os_dep/linux/ioctl_linux.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/os_dep/linux/mlme_linux.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/os_dep/linux/os_intfs.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/os_dep/linux/pci_intf.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/os_dep/linux/recv_linux.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/os_dep/linux/rtw_android.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/os_dep/linux/sdio_intf.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/os_dep/linux/usb_intf.c
/var/lib/dkms/rtl8192cu-tjp/1.6/build/os_dep/linux/xmit_linux.c
/var/lib/dpkg/info/rtl8192cu-tjp-dkms.list
/var/lib/dpkg/info/rtl8192cu-tjp-dkms.md5sums
/var/lib/dpkg/info/rtl8192cu-tjp-dkms.postinst
/var/lib/dpkg/info/rtl8192cu-tjp-dkms.prerm
jeremy@jeremy-Inspiron-530:~$ grep 8192 /etc/modprobe.d/*
/etc/modprobe.d/blacklist.conf:blacklist rtl8192cu
jeremy@jeremy-Inspiron-530:~$ 



```

---

### Post by praseodym on 2013-09-03
Obviously, the driver does not include the product and vendor ID.

Try to add it by hand via:

```
echo 'install 8192cu modprobe --ignore-install 8192cu ; /bin/echo "0846 9041" > /sys/bus/usb/drivers/rtl8192cu/new_id' | sudo tee /etc/modprobe.d/8192cu.conf
```
This is one line, you better copy/paste it. Load the driver:
```

sudo modprobe -v 8192cu
```

---

### Post by superluigibro7 on 2013-09-03
> **praseodym said:**
> Obviously, the driver does not include the product and vendor ID.

Try to add it by hand via:

```
echo 'install 8192cu modprobe --ignore-install 8192cu ; /bin/echo "0846 9041" > /sys/bus/usb/drivers/rtl8192cu/new_id' | sudo tee /etc/modprobe.d/8192cu.conf
```
This is one line, you better copy/paste it. Load the driver:
```

sudo modprobe -v 8192cu
```

Works perfectly now! I really appreciate the help. Thanks!

---

### Post by praseodym on 2013-09-04
You're welcome.

Glad it worked.

---

