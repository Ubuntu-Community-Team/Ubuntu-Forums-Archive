---
title: "wpa_supplicant can't find my access point, kismet does!"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by wpa-psk on 2009-04-02
Hey all.

So i bought myself this rtl8085 card, which my xubuntu (8.10) recognizes:

```
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
	Flags: bus master, medium devsel, latency 32, IRQ 3
	I/O ports at 9800 [size=256]
	Memory at e1000000 (32-bit, non-prefetchable) [size=512]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: rtl8180
	Kernel modules: rtl8180

```

So i tried to connect to my Access Point using this network-manager-plugin, which didn't work since i can only choose between no encryption, WEP and WPA2 - i can't choose WPA, and my wireless router doesn't support WPA2.

So, i went on to try top set it up using wpa_supplicant.

This is my /etc/wpa_supplicant.conf:

```
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=0

network={
ssid="Slartibartfass"
bssid=00:0F:3D:98:8F:71
psk="passphrase"
proto=WPA
}
```

So i try to start it:

wpa_supplicant -Dwext -iwlan1 -c/etc/wpa_supplicant.conf -d

```
Initializing interface 'wlan1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
eapol_version=1
ap_scan=0
Priority group 0
   id=0 ssid='Slartibartfass'
Initializing interface (2) 'wlan1'
Interface wlan1 set UP - waiting a second for the driver to complete initialization
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:1f:1f:11:65:0e
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
Added interface wlan1
Ignore event for foreign ifindex 6
RTM_NEWLINK: operstate=0 ifi_flags=0x1103 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1103 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
Wireless event: cmd=0x8b19 len=8
Received 590 bytes of scan results (2 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1c:4a:03:e6:9c ssid='WLAN-001C4A03E69C' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
1: 00:04:0e:e9:2d:15 ssid='AnTev2009' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:1c:4a:03:e6:9c ssid='WLAN-001C4A03E69C' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
1: 00:04:0e:e9:2d:15 ssid='AnTev2009' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
**No suitable AP found.**
Setting scan request: 5 sec 0 usec
RTM_NEWLINK: operstate=0 ifi_flags=0x1103 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
Wireless event: cmd=0x8b06 len=8
EAPOL: disable timer tick
```

So it doesn't find my AP.

Then i went on to double-check my router's config. The ssid is NOT hidden and the MAC filters are disabled.

I then went on to install kismet and configure its scanning source:

```
source=rt8180,wlan1,wireless
```

I started kismet and it finds my access point.

So kismet finds my AP, wpa_supplicant doesn't.

Also, "iwlist wlan1 scan" also doesn't find my AP:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:04:0E:E9:2D:15
                    ESSID:"AnTev2009"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/100  Signal level:18/65  
                    Encryption key:on
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000043a6142233
                    Extra: Last beacon: 396ms ago
          Cell 02 - Address: 00:1F:3F:D3:31:5A
                    ESSID:"FRITZ!Box Fon WLAN 7170"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/100  Signal level:18/65  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000000d31d5234
                    Extra: Last beacon: 100ms ago
          Cell 03 - Address: 00:1C:4A:03:E6:9C
                    ESSID:"WLAN-001C4A03E69C"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=10/100  Signal level:17/65  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000323493e673c
                    Extra: Last beacon: 104ms ago
```

Note that i can connect to this ap with the exact same wpa_supplicant config with a laptop using a ipw2100 driver.

Any suggestions?

---

