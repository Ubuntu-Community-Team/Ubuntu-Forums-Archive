---
title: "Sitecom WL-608 / wpa supplicant on Ubuntu Maverick"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by Cheezzhead on 2011-07-19
I've been trying to get my USB adapter, a Sitecom WL-608, working on my Macbook with Ubuntu Maverick (10.10) for the past 2 days now. Reason is that my wireless device (broadcom 4331 chipset) is as of yet unsupported on Ubuntu. I first used this: [http://johnsunixtips.blogspot.com/2010/08/sitecom-wireless-wl-608-54g-usb-dongle.html](http://johnsunixtips.blogspot.com/2010/08/sitecom-wireless-wl-608-54g-usb-dongle.html), which went fine: the adapter is recognised by Network Manager (under wlan0) and starts scanning for wireless connections. 

Connecting to my home network, however, didn't yield to a result: I filled in the WPA2-PSK password, after which it tried to connect for about a minute and then showed the key-input screen again. 

To fix this, I eventually installed wpa_supplicant and tried to set it up. So far, it hasn't given any result. I even tried installing wpa_gui - which worked for the first time but after a reboot gave the message "could not get status from wpa_supplicant" (if anyone knows how to fix that it would be great, although it's not of primary concern). 

/etc/wpa_supplicant.conf: 
```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
ap_scan=1

network={
        ssid="Veulen32"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        psk=76db7b255aebaecc3f16f9efb3e533da22a87b4e3db1216eea8bc9d07c2ced19
        pairwise=CCMP
        group=CCMP
} 
```I retrieved psk with wpa_passphrase, as usual. I just filled in the WPA2-PSK key for the network, that's correct right? 

After running 'sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd', I get this: 

```
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group='0'
ap_scan=1
Line: 5 - start of a new network block
ssid - hexdump_ascii(len=8):
     56 65 75 6c 65 6e 33 32                           Veulen32        
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
pairwise: 0x10
group: 0x10
Priority group 0
   id=0 ssid='Veulen32'
SIOCGIWRANGE: WE(compiled)=22 WE(source)=14 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:0c:f6:80:98:01
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): 0f 6a 09 11 2b 04 5f 70 aa b0 4a 40 47 5c d7 e0
WPS: Build Beacon and Probe Response IEs
WPS:  * Version
WPS:  * Wi-Fi Protected Setup State (0)
WPS:  * Version
WPS:  * Wi-Fi Protected Setup State (0)
WPS:  * Response Type (2)
WPS:  * UUID-E
WPS:  * Manufacturer
WPS:  * Model Name
WPS:  * Model Number
WPS:  * Serial Number
WPS:  * Primary Device Type
WPS:  * Device Name
WPS:  * Config Methods (0)
WPS:  * RF Bands (3)
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
ctrl_interface_group=0
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=8):
     56 65 75 6c 65 6e 33 32                           Veulen32        
Trying to get current scan results first without requesting a new scan to speed up initial association
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds
EAPOL: disable timer tick
Scan timeout - try to get results
Received 650 bytes of scan results (3 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: bc:05:43:f3:9c:cf ssid='Veulen32' wpa_ie_len=22 rsn_ie_len=20 caps=0x11
   skip WPA IE - PTK cipher mismatch
1: 00:18:f6:f1:57:a5 ssid='Thomson75ADFE' wpa_ie_len=28 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
2: 00:0f:66:d9:d4:48 ssid='['_*]Linksys[*_']' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: bc:05:43:f3:9c:cf ssid='Veulen32' wpa_ie_len=22 rsn_ie_len=20 caps=0x11
   skip - non-WPA network not allowed
1: 00:18:f6:f1:57:a5 ssid='Thomson75ADFE' wpa_ie_len=28 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
2: 00:0f:66:d9:d4:48 ssid='['_*]Linksys[*_']' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=8):
     56 65 75 6c 65 6e 33 32                           Veulen32        
Scan requested (ret=0) - scan timeout 5 seconds
Scan timeout - try to get results
Received 650 bytes of scan results (3 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:18:f6:f1:57:a5 ssid='Thomson75ADFE' wpa_ie_len=28 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
1: 00:0f:66:d9:d4:48 ssid='['_*]Linksys[*_']' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
2: bc:05:43:f3:9c:cf ssid='Veulen32' wpa_ie_len=22 rsn_ie_len=20 caps=0x11
   skip WPA IE - PTK cipher mismatch
Try to find non-WPA AP
0: 00:18:f6:f1:57:a5 ssid='Thomson75ADFE' wpa_ie_len=28 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
1: 00:0f:66:d9:d4:48 ssid='['_*]Linksys[*_']' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
2: bc:05:43:f3:9c:cf ssid='Veulen32' wpa_ie_len=22 rsn_ie_len=20 caps=0x11
   skip - non-WPA network not allowed
No suitable AP found.
Setting scan request: 5 sec 0 usec

```At least, that's the first part (at some point it just keeps rescanning all the available networks). Thing that's going wrong, I think, is that it says "PTK cipher mismatch" when it scans the intended network. I hope anyone can help, as the only way I can get internet now is with an ethernet cable, and that's not really optimal. 

Some more info: 
Machine brand / model: MacBook 8,2 
lsb_release -d: Ubuntu 10.04.3 
LTS uname -mr: 2.6.32-28-generic x86_64 

lsusb | grep Sitecom: 
```
Bus 002 Device 004: ID 0df6:003f Sitecom Europe B.V. 
```ifconfig wlan0 && ifconfig wlan0:avahi: 
```
wlan0     Link encap:Ethernet  HWaddr 00:0c:f6:80:98:01  
          inet6 addr: fe80::20c:f6ff:fe80:9801/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7980 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4772 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1629770 (1.6 MB)  TX bytes:327164 (327.1 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:0c:f6:80:98:01  
          inet addr:169.254.6.222  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
```iwconfig wlan0: 
```
wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.427 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```lsmod:
 ```
Module                  Size  Used by
b44                    30687  0 
ssb                    45427  1 b44
mii                     5237  1 b44
ndiswrapper           244800  0 
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_atihdmi     3023  1 
snd_hda_codec_cirrus    11825  1 
snd_hda_intel          25741  2 
snd_hda_codec          85759  3 snd_hda_codec_atihdmi,snd_hda_codec_cirrus,snd_hda_intel
snd_seq_dummy           1782  0 
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71251  16 snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
uvcvideo               62819  0 
lp                      9336  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
videodev               40518  1 uvcvideo
joydev                 11104  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  1 
rt2870sta             525366  1 
parport                37160  2 ppdev,lp
applesmc               29217  0 
v4l1_compat            15495  2 uvcvideo,videodev
vgastate                9857  1 vga16fb
v4l2_compat_ioctl32    11892  1 videodev
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
video                  20623  0 
led_class               3764  2 applesmc,sdhci
input_polldev           3106  1 applesmc
output                  2503  1 video
hid_apple               5418  0 
tg3                   142290  0 
usbhid                 41116  0 
ohci1394               30260  0 
hid                    83536  2 hid_apple,usbhid
ieee1394               94771  1 ohci1394
```dmesg | grep wlan: (I also saved full dmesg, but it might be too long to show here) 
```
[ 73.071522] wlan0: no IPv6 routers present 
[ 201.429890] wlan0: no IPv6 routers present 
[ 249.269559] wlan0: no IPv6 routers present 
[ 851.905600] wlan0: no IPv6 routers present
```sudo lshw -C network: ```
   *-network
       description: Ethernet interface
       product: NetXtreme BCM57765 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: c8:2a:14:26:05:fc
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116j duplex=full firmware=57765-v1.37 ip=192.168.178.33 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: irq:16 memory:b0400000-b040ffff(prefetchable) memory:b0410000-b041ffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:b0600000-b0603fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0c:f6:80:98:01
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RTxx70 Wireless
```iwlist scan: 
```
lo Interface doesn't support scanning. 

eth0 Interface doesn't support scanning. 

wlan0     Scan completed :
          Cell 01 - Address: 00:18:F6:F1:57:A5
                    Protocol:802.11b/g
                    ESSID:"Thomson75ADFE"
                    Mode:Managed
                    Channel:1
                    Quality:23/100  Signal level:-81 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 88:25:2C:BB:9E:40
                    Protocol:802.11b/g/n
                    ESSID:"ARV7519BB9E40"
                    Mode:Managed
                    Channel:1
                    Quality:2/100  Signal level:-89 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 03 - Address: 00:24:17:D5:07:03
                    Protocol:802.11b/g
                    ESSID:"Thomson7411F2"
                    Mode:Managed
                    Channel:1
                    Quality:18/100  Signal level:-83 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: BC:05:43:F3:9C:CF
                    Protocol:802.11g/n
                    ESSID:"Veulen32"
                    Mode:Managed
                    Channel:4
                    Quality:100/100  Signal level:-37 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:0F:66:D9:D4:48
                    Protocol:802.11b/g
                    ESSID:"['_*]Linksys[*_']"
                    Mode:Managed
                    Channel:6
                    Quality:23/100  Signal level:-81 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: 00:1B:FC:42:89:BE
                    Protocol:802.11b/g
                    ESSID:"DaanTink2.0"
                    Mode:Managed
                    Channel:8
                    Quality:0/100  Signal level:-91 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 07 - Address: 00:22:6B:74:0F:8A
                    Protocol:802.11b/g
                    ESSID:"Wolf"
                    Mode:Managed
                    Channel:11
                    Quality:2/100  Signal level:-89 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 08 - Address: 00:1A:70:A9:02:EC
                    Protocol:802.11b/g/n
                    ESSID:"Delta3"
                    Mode:Managed
                    Channel:3
                    Quality:2/100  Signal level:-89 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```sudo /etc/init.d/networking restart: 
```
 * Reconfiguring network interfaces...                                          WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.
                                                                         [ OK ]
```

---

### Post by Cheezzhead on 2011-07-19
Anyone?

---

