---
title: "Cannot connect or authenticate to 802.1x (PEAP) WiFi Network"
date: 2013-08-16
forum: Networking &amp; Wireless
---

### Post by U&amp;?@&lt;i5}-+ on 2013-08-16
Hey everyone,

I recently received a username and password to use on our corporate WiFi however I am unable to connect to it from my laptop running Ubuntu Raring 64-bit. I can connect to it using my Android phone since it has an option to specify the inner authentication as none however on Ubuntu it keeps prompting me for my password. :(

What I have tried thus far is a fair amount of searching which eventually led me to this [unresolved thread]("http://ubuntuforums.org/showthread.php?t=1726522") where a few users are having the same problem. I also found another thread that suggested I remove the system-ca-certs=true line from the config file in /etc/NetworkManager/system-connections/ but alas that did not help either.

In the aforementioned unresolved thread it says something about manually editing the wpa-supplicant.conf file to get it to connect but I'm not exactly too sure how to go about doing this. If anyone could provide me with some guidance I would be greatly appreciative! :)

Cheers!
Xiph

---

### Post by varunendra on 2013-08-16
Welcome to the forums Xiphan !
> **Xiphan said:**
> I also found another thread that suggested I remove the system-ca-certs=true line from the config file in /etc/NetworkManager/system-connections/ but alas that did not help either.
What are the contents of your current key file? Please post the output of -
```
sudo cat /etc/NetworkManager/system-connections/<your connection's key-file>
```
**[COLOR="#FF0000"]Caution !! The above output will also contain your connections Security Key if you have saved it. So remove it before posting here. Same with your mac ID if you consider it sensitive.[/COLOR]**

---

### Post by U&amp;?@&lt;i5}-+ on 2013-08-16
> **varunendra said:**
> Welcome to the forums Xiphan !
Thanks for the welcome. :)

> **varunendra said:**
> What are the contents of your current key file? Please post the output of -
```
sudo cat /etc/NetworkManager/system-connections/<your connection's key-file>
```
**[COLOR=#FF0000]Caution !! The above output will also contain your connections Security Key if you have saved it. So remove it before posting here. Same with your mac ID if you consider it sensitive.[/COLOR]**

```

[ipv6]
method=auto

[connection]
id=CORP
uuid=[COLOR=#0000ff][removed][/COLOR]
type=802-11-wireless

[802-11-wireless]
ssid=CORP
mode=infrastructure
mac-address=[COLOR=#0000ff][removed][/COLOR]
security=802-11-wireless-security

[802-1x]
eap=peap;
identity=[COLOR=#0000ff][my username][/COLOR]
phase2-auth=mschapv2
password-flags=1
system-ca-certs=true

[ipv4]
method=auto

[802-11-wireless-security]
key-mgmt=wpa-eap
auth-alg=open

```

---

### Post by varunendra on 2013-08-16
> **Xiphan said:**
> 
```

[802-1x]
system-ca-certs=**[COLOR="#FF0000"]true[/COLOR]**

```

Evidently, the line has been created again if you ever deleted it, and that's exactly what I was suspecting (not that I'm confident about it being the culprit though..).

Accordingly, please try changing its value from "true" to "false" this time. To do so, open the file with root access -
```
gksu gedit /etc/NetworkManager/system-connections/CORP
```
..and change the value of "system-ca-certs" from "true" to "false". Proofread, save and close the file. Try to re-connect (reboot if immediate attempt fails) and let us know if you could.

---

### Post by U&amp;?@&lt;i5}-+ on 2013-08-19
> **varunendra said:**
> Evidently, the line has been created again if you ever deleted it, and that's exactly what I was suspecting (not that I'm confident about it being the culprit though..).

Accordingly, please try changing its value from "true" to "false" this time. To do so, open the file with root access -
```
gksu gedit /etc/NetworkManager/system-connections/CORP
```
..and change the value of "system-ca-certs" from "true" to "false". Proofread, save and close the file. Try to re-connect (reboot if immediate attempt fails) and let us know if you could.

Sorry I forgot to mention the line came back because I decided to recreate the connection so I could troubleshoot from the start without any of the changes I had made. I have since changed that setting to false (which seems to remove the line altogether from the file) but it did not resolve the problem as I am still prompted for my password after it makes several attempts to connect.

Is this perhaps not a fault that should be logged with Network Manager as the same thing happens when I use a Linux Mint and Fedora Live CD, both of which use Network Manager to manage WiFi connections?

Lastly if it is a fault with Network Manager what other options do I have to establish a connection?

---

### Post by varunendra on 2013-08-19
> **Xiphan said:**
> Lastly if it is a fault with Network Manager what other options do I have to establish a connection?

In the hasty reply I can manage at the moment, I can answer only this part. You can try [wicd]("https://help.ubuntu.com/community/WICD") instead of Network Manager.

But I think we may get better hints if you can run "wireless_script" and post its result here. You can find the script and instructions on how to run it in the "Wireless Script" link in my signature.

---

### Post by U&amp;?@&lt;i5}-+ on 2013-08-22
Here is the contents created by Wireless Script:

```


*************** info trace ***************

***** uname -a *****

Linux LAP-Julian 3.8.0-27-generic #40-Ubuntu SMP Tue Jul 9 00:17:05 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

***** lspci *****

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21f3]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2200 [8086:0891] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2200 BGN [8086:4222]
    Kernel driver in use: iwlwifi

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 006: ID 0bb4:0fb4 HTC (High Tech Computer Corp.) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 147e:2020 Upek 
Bus 001 Device 006: ID 0a5c:21e6 Broadcom Corp. 
Bus 001 Device 004: ID 04f2:b2ea Chicony Electronics Co., Ltd 

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

rndis_wlan             36998  0 
rndis_host             13855  1 rndis_wlan
usbnet                 31879  3 rndis_host,rndis_wlan,cdc_ether
iwldvm                241872  0 
mac80211              606457  1 iwldvm
iwlwifi               173477  1 iwldvm
cfg80211              510937  4 iwlwifi,mac80211,rndis_wlan,iwldvm

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: usb0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    EE-CORP:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA2 Enterprise
    Control_SyS:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    EE-GUEST:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60
    HP-nomodel.60AF36: Ad-Hoc, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52
    ZaneT:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA2
    dogtown:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
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
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Control_SyS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002b4986148d
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 000B436F6E74726F6C5F537953
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601051600000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"EE-CORP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000072dea50af26
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 000745452D434F5250
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 07065A4120010D14
                    IE: Unknown: 0B050200178D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 851E08008F000F00FF0359004943542D41503100000000000000000002000036
                    IE: Unknown: 9606004096001100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:off
                    ESSID:"\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000072dea522978
                    Extra: Last beacon: 260ms ago
                    IE: Unknown: 000100
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 07065A4120010D14
                    IE: Unknown: 0B050200178D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 851E08008F000F00FF0359004943542D41503100000000000000000002000036
                    IE: Unknown: 9606004096001100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:off
                    ESSID:"EE-GUEST"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000072dea51f174
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 000845452D4755455354
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 07065A4120010D14
                    IE: Unknown: 0B050200178D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 9606004096001100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"ZaneT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000176de7e84
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 00055A616E6554
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 07065A4120010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2C0000FF00000000000000000000008000000000000000000000
                    IE: Unknown: 3D1601000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000072de9ff4977
                    Extra: Last beacon: 5704ms ago
                    IE: Unknown: 000100
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 07065A4120010D14
                    IE: Unknown: 0B0502001E8D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E08008F000F00FF0359004943542D41503100000000000000000002000036
                    IE: Unknown: 9606004096001100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 07 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:off
                    ESSID:"HP-nomodel.60AF36"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000007a27c1546fd
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 001148502D6E6F6D6F64656C2E363041463336
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 08 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002b49865984
                    Extra: Last beacon: 452ms ago
                    IE: Unknown: 0006000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601051600000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b872d77183
                    Extra: Last beacon: 352ms ago
                    IE: Unknown: 000700000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050402030008
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180205F02C0000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 10 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"dogtown"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001862f72663
                    Extra: Last beacon: 5664ms ago
                    IE: Unknown: 0007646F67746F776E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406080800000000000000000000000000000000000000
                    IE: Unknown: 3D1606080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000


***** resolv.conf *****

nameserver 127.0.1.1
search elec.durban.gov.za

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

filename:       /lib/modules/3.8.0-27-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2012 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     8FAC5D54523380931B0EE42
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.8.0-27-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-27-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2012 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-3160-6.ucode
firmware:       iwlwifi-7260-6.ucode
srcversion:     592C37DA54115B8D5FB3D55
alias:          pci:v00008086d000008B3sv*sd00008070bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004070bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000462bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000262bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000062bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000822bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000222bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00005260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004860bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004462bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004062bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004822bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004422bc*sc*i*
alias:          pci:v00008086d00000891sv*sd00004222bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004022bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005027bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005025bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005017bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005015bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005007bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005005bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001027bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001025bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001017bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001015bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001007bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001005bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001317bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001327bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005226bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005225bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005221bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005207bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005206bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005205bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005201bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005215bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005317bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005315bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005327bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005325bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005307bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00004820bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d00000082sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
depends:        cfg80211
intree:         Y
vermagic:       3.8.0-27-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: agg TX, 4: agg RX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Enable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           auto_agg:enable agg w/o check traffic load (default: enable) (bool)
parm:           5ghz_disable:disable 5GHz band (default: 0 [enabled]) (bool)


***** udev rules *****

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   11.053938] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X
[   11.223479] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1
[   11.236033] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   11.236036] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   11.236037] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   11.236038] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   11.236039] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[   11.236041] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 2200 BGN, REV=0x104
[   11.236146] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   11.258236] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   11.607918] Bluetooth: can't load firmware, may not work correctly
[   14.161773] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   14.169604] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   14.539885] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   14.547318] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   14.749767] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.750028] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.763789] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   48.650200] Bluetooth: can't load firmware, may not work correctly

****************** done ******************


```

Something interesting that I discovered today is that on another laptop with a different wireless card I was able to connect using a LiveCD that previously failed on my laptop. I don't know if that gives you any idea on what might be wrong with my laptop? :confused:

---

### Post by Josh_Wold on 2013-09-03
Sooo, is there any update to this issue? I'm pretty sure this is a fairly common occurrence. I'm having the exact same issues and have spent the last day or so looking for a solution. Here are my details:

wpa2-enterprise/peap/mschapv2
no certificates required

I'm the network administrator, so i can see any of the logs we might need to resolve this. The error I'm getting from the ISE server is this:
Extracted EAP-Response/NAK packet requesting to use unsupported EAP protocol; EAP-negotiation failed

Here is the explanation from the ISE:
"Extracted from the RADIUS message an EAP-Response/NAK packet, rejecting the previously-proposed EAP-based protocol, and requesting to use another protocol instead, per the configuration of the client's supplicant.  However, the requested EAP-based protocol is currently not supported by ISE."

And finally, here is the output from my wireless script:
[http://pastebin.ubuntu.com/6059319/](http://pastebin.ubuntu.com/6059319/) 

What can I do from here? It seems to me that there is an issue with how the OS is handling the EAP. This method works on all android, iphone/ipad, and windows based OS's without an issue. It also works on my colleagues' fedora install. While I can see his RADIUS logs (ISE), I can't see his /var/log's. 

Thanks,
Josh

---

### Post by xlash on 2014-05-07
> **varunendra said:**
> Evidently, the line has been created again if you ever deleted it, and that's exactly what I was suspecting (not that I'm confident about it being the culprit though..).

Accordingly, please try changing its value from "true" to "false" this time. To do so, open the file with root access -
```
gksu gedit /etc/NetworkManager/system-connections/CORP
```
..and change the value of "system-ca-certs" from "true" to "false". Proofread, save and close the file. Try to re-connect (reboot if immediate attempt fails) and let us know if you could.

I had the same issue, this answer solved it for me. (Removing the [802-1x] system-ca-certs=true line)

Thanks

PS: Those were the logs on a Cisco Wireless Controller 5508

*mmListen: DATE #MM-5-PMKCACHE_DEL_FAILED: mm_listen.c:8463 Failed to delete PMK cache entry for station MAC_ADDRESS with request from controller IP_ADDRESS
*mmListen: DATE #MM-5-PMKCACHE_DEL_FAILED: mm_listen.c:8463 Failed to delete PMK cache entry for station MAC_ADDRESS with request from controller IP_ADDRESS
*mmListen: DATE #MM-5-PMKCACHE_DEL_FAILED: mm_listen.c:8463 Failed to delete PMK cache entry for station MAC_ADDRESS with request from controller IP_ADDRESS
 *Dot1x_NW_MsgTask_0: May 07 15:00:34.215: #APF-6-MOBILE_EXCLUDED: apf_ms.c:4994 Excluded the mobile
*Dot1x_NW_MsgTask_0: DATE: #DOT1X-4-AAA_MAX_RETRY: 1x_bauth_sm.c:402 Max AAA authentication attempts exceeded for client MAC_ADDRESS

---

### Post by varunendra on 2014-05-07
Thanks for the feedback xlash! Hope the fix remains stable for you. :)

---

### Post by m4dm4n on 2014-05-26
I know the questions a tad old, but I had the exact same problem as the original poster and I managed to get around it. The settings I've been told to connect with on the Sydney Uni network were PEAP for authentication and "None" for Phase 2 authentication (which is called Inner authentication in the NetworkManager GUI). In Ubuntu the NetworkManager GUI did not offer "None" as an option for Phase 2. The solution seemed to be to simply force it by modifying the network configuration under /etc/NetworkManager/system-connections/<ConnectionName> (UniSydney in my case) and changing  phase2-auth to "none" in the [802-1x] group like so:

```

[802-1x]
eap=peap;
phase2-auth=none
password-flags=2

```

---

