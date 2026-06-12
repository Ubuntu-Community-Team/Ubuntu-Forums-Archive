---
title: "Ubuntu 12.04.2 vs. 13.04 Download Speeds"
date: 2013-07-07
forum: Networking &amp; Wireless
---

### Post by jdrichardson on 2013-07-07
I have a strange situation happening with an HP AMD 64bit, quad4 CPU, wifi connection computer. When I run 12.04 my wifi connection is great - I typically see 900-1200 Mbps; however, when I try to use 13.04, everything slows to a crawl. It takes forever, it seems, just to install 13.04 - any downloading is slowwww! I can run other distro's - PCLinuxOS, Mageia with no ill effects. Performance is comparable to what I see on 12.04. So the problem seems to be only with 13.04. By the way, I see the same thing with Kubuntu and Linux Mint which are, of course, 13.04 derivatives.

Googling led me to disabling IPV6, but that didn't do much for me. I think the problem is network manager and/or wifi driver related, but I haven't seen any fix suggested. What I'm thinking of trying is replacing 13.04's firmware folder with the one from 12.04 ans see what happens. I might try the same thing with Network Manager. I know this a brute-force approach but i can't think/find any alternatives.

Any suggestions out there? Anyone else have this problem? I'd sure appreciate some help!

---

### Post by varunendra on 2013-07-08
My personal suggestion to you - just stick with 12.04 as it is LTS. 13.04 will reach its "End Of Life" in January next year.

If, for some reason you still want to go with 13.04, please download and run "wireless_script" on it as mentioned [here]("http://ubuntuforums.org/showpost.php?p=12350385") and post back the report it generates.

---

### Post by jdrichardson on 2013-07-08
Thanks for the reply. Yes, it occurs to me that I should just continue with 12.04 since it has log-term support, but I'm just curious as to what's wrong. I think a driver firmware file is kaput. I ran your script, and here are the results:


*************** info trace ***************

***** uname -a *****

Linux basement 3.5.0-36-generic #57~precise1-Ubuntu SMP Thu Jun 20 18:21:09 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.2 LTS
Release:	12.04
Codename:	precise

***** lspci *****

02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
	Subsystem: Lite-On Communications Inc Device [11ad:6632]
	Kernel driver in use: rt2800pci
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Hewlett-Packard Company Pavillion p6774 [103c:2ab1]
	Kernel driver in use: r8169

***** lsusb *****

Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 003 Device 002: ID 03f0:0705 Hewlett-Packard ScanJet 4400c
Bus 005 Device 002: ID 0461:4d0f Primax Electronics, Ltd 
Bus 005 Device 003: ID 04ca:0040 Lite-On Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"2WIRE581"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC address removed>   
          Bit Rate=18 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:38   Missed beacon:0


***** rfkill *****

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

***** lsmod *****

rt2800pci              18751  0 
rt2800lib              59396  1 rt2800pci
crc_ccitt              12708  1 rt2800lib
rt2x00pci              14621  1 rt2800pci
rt2x00lib              55575  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              555272  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              208382  2 rt2x00lib,mac80211
eeprom_93cx6           13345  1 rt2800pci

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [2WIRE581] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
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
    anthony:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WEP
    *2WIRE581:       Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 61 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.68
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254



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
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"2WIRE581"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000019b6c26d181
                    Extra: Last beacon: 528ms ago
                    IE: Unknown: 00083257495245353831
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030103
                    IE: Unknown: 0706555320010B1B
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
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"anthony"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000005de8108b9af
                    Extra: Last beacon: 20844ms ago
                    IE: Unknown: 0007616E74686F6E79
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180203F4010000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001300000000000000000000000000000000000000


***** resolv.conf *****

nameserver 127.0.0.1
search gateway.2wire.net

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

[   11.212501] Registered led device: rt2800pci-phy0::radio
[   11.212516] Registered led device: rt2800pci-phy0::assoc
[   11.212532] Registered led device: rt2800pci-phy0::quality
[   18.965111] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.965672] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.525847] wlan0: authenticate with <MAC address removed>
[   22.573525] wlan0: send auth to <MAC address removed> (try 1/3)
[   22.574825] wlan0: authenticated
[   22.601274] wlan0: associate with <MAC address removed> (try 1/3)
[   22.602939] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[   22.603087] wlan0: associated
[   22.603473] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

****************** done ******************

---

### Post by jdrichardson on 2013-07-08
Whoops!

The wireless.txt file is from my setup on ubuntu 12.04. I'll reinstall 13.04 and post its file shortly.

Sorry about that!

---

### Post by jdrichardson on 2013-07-08
I reinstalled 13.04 and reran your wireless script. Here are the results:


*************** info trace ***************

***** uname -a *****

Linux basement 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring

***** lspci *****

02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
	Subsystem: Lite-On Communications Inc Device [11ad:6632]
	Kernel driver in use: rt2800pci
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Hewlett-Packard Company Pavillion p6774 [103c:2ab1]
	Kernel driver in use: r8169

***** lsusb *****

Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 003 Device 002: ID 03f0:0705 Hewlett-Packard ScanJet 4400c
Bus 005 Device 002: ID 0461:4d0f Primax Electronics, Ltd HP Optical Mouse
Bus 005 Device 003: ID 04ca:0040 Lite-On Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"2WIRE581"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC address removed>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:561  Invalid misc:7   Missed beacon:0


***** rfkill *****

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

***** lsmod *****

rt2800pci              18582  0 
rt2800lib              66507  1 rt2800pci
rt2x00pci              14519  1 rt2800pci
rt2x00lib              54869  3 rt2x00pci,rt2800lib,rt2800pci
mac80211              606457  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              510937  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [2WIRE581] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *2WIRE581:       Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 61 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.68
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254



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

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"2WIRE581"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000019c98f6a181
                    Extra: Last beacon: 536ms ago
                    IE: Unknown: 00083257495245353831
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030103
                    IE: Unknown: 0706555320010B1B
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


***** resolv.conf *****

nameserver 127.0.1.1
search gateway.2wire.net

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

[   14.483830] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.484173] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.873454] wlan0: authenticate with <MAC address removed>
[   17.920990] wlan0: send auth to <MAC address removed> (try 1/3)
[   17.922286] wlan0: authenticated
[   17.922472] rt2800pci 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   17.922477] rt2800pci 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   17.924954] wlan0: associate with <MAC address removed> (try 1/3)
[   17.926626] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[   17.926771] wlan0: associated
[   17.926779] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  332.506471] wlan0: authenticate with <MAC address removed>
[  332.529903] wlan0: send auth to <MAC address removed> (try 1/3)
[  332.531141] wlan0: authenticated
[  332.531627] rt2800pci 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  332.531642] rt2800pci 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  332.533728] wlan0: associate with <MAC address removed> (try 1/3)
[  332.535563] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[  332.535979] wlan0: associated

****************** done ******************

---

### Post by varunendra on 2013-07-08
First of all, please use code tags for posting commands and their outputs (follow the link in my signature to see an elaborated example).

> **jdrichardson said:**
> 
  Wireless Access Points (* = current AP)
    *2WIRE581:       Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 61 WPA WPA2


Even though the same settings work well on your 12.04 installation, it is strongly recommended to NOT use WPA/WPA2 mixed mode. Change the encryption settings in your router/access-point to pure WPA2-PSK with AES, no mixed mode, no TKIP.

With (or without) that change, please try -
```
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y
```
and post back the effect on performance.

---

### Post by jdrichardson on 2013-07-08
First off, I ran your script and posted the results per your request (which did not request code tags - I wouldn't know how to add them).

Secondly, I ran the commands that you suggested, but did not see any performance increase.

Thirdly, I took your recommendation and re-installed 12.04.2. Ubuntu 13.04 (and its derivatives) is the first distribution I've seen in  7 years that acted this way. It's as if a governor was placed on my WiFi channel. In the printouts I sent you I did see a 10-to-one difference in stated frequency capability. Weird! Hopefully 13.10 won't be this way.

Thanks again for your help.

---

### Post by varunendra on 2013-07-08
> **jdrichardson said:**
> First off, I ran your script and posted the results per your request (which did not request code tags - I wouldn't know how to add them).
Was requested in the post that you followed to run the script, highlighted and in the very same lines that tell what, how and where to upload the report -
> Either attach this file *(**wireless-info.txt** or **wireless-info.txt.tar.gz**, whichever is created)*, or even better, copy-paste its contents in your next post. [COLOR=Navy](**Do remember to paste the contents between '[Code]("http://ubuntuforums.org/showpost.php?p=12368389")' tags** generated by clicking on **#** button located at the top of edit box, in which you create new posts. Doing so will preserve its formatting and make your post more readable)[/COLOR].
....
.... Once again, **do not forget to [COLOR=Navy]wrap the output in '[Code]("http://ubuntuforums.org/showpost.php?p=12368389")' tags[/COLOR]** if you copy-paste the output here.

Anyway, based on the dmesg part of the report -
```
[ 332.531627] rt2800pci 0000:02:00.0 wlan0: **[COLOR="#FF0000"]disabling HT[/COLOR]** as WMM/QoS is not supported by the AP
[ 332.531642] rt2800pci 0000:02:00.0 wlan0: [COLOR="#FF0000"]disabling VHT[/COLOR] as WMM/QoS is not supported by the AP
```
there is a slight chance that disabling the N-channel in the router itself could help since the above messages mean you could not use it anyway. Also, there is always the option of compiling the proprietary driver if the native one fails.

But it is good to stick with the latest LTS if it works better without workarounds. In fact the latest non-LTS is only recommended if there is something important that the LTS can't offer while the non-LTS can.

Unless there is something like that in your wish-list, I'd suggest to skip even 13.10, and directly upgrade to the next LTS (of course unless the interim release(s) perform significantly better). :)

---

### Post by jdrichardson on 2013-07-09
My apologies. My eyes didn't get past the data file and script command (which I was looking for). Next time I'll be more vigilant. Thanks again.

---

### Post by varunendra on 2013-07-09
No problem! :)

I have edited that post many times trying to make it less wordy for the same reason, But I also have to keep it easy to understand for inexperienced users, thus had to include some explanations, which are probably making it bloated. Well.. as long as it serves the main purpose.. :P

---

