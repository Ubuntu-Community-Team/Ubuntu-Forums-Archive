---
title: "Ubuntu 12.10 running cinnamon wifi stops working"
date: 2013-04-20
forum: Networking &amp; Wireless
---

### Post by deppgirl on 2013-04-20
I am running Ubuntu 12.10 with cinnamon along side Windows 8. My wifi will randomly stop working, when it does work it's fairly fast but then it will stop working out of no where but still say its connected and the rest of the household has no wifi issues. 

here's some info: 


```




**** uname -a ****




Linux becky-PC 3.5.0-27-generic #46-Ubuntu SMP Mon Mar 25 19:58:17 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux




**** lsb-release ****




DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"




**** lspci ****




02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8181]
	Kernel driver in use: rtl8192ce
--
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
	Subsystem: Toshiba America Info Systems Device [1179:fd50]
	Kernel driver in use: atl1c




**** lsusb ****




Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 003: ID 04f2:b1d6 Chicony Electronics Co., Ltd 




**** iwconfig ****




wlan0     IEEE 802.11bgn  ESSID:"Depp Family"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:22:6B:55:9D:06   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0






**** rfkill ****




0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no




**** lsmod ****




Module                  Size  Used by
nls_iso8859_1          12714  0 
bnep                   18141  2 
rfcomm                 46620  0 
bluetooth             209249  10 bnep,rfcomm
snd_hda_codec_conexant    61898  1 
parport_pc             32689  0 
ppdev                  17074  0 
snd_hda_intel          33492  3 
snd_hda_codec         134213  2 snd_hda_codec_conexant,snd_hda_intel
arc4                   12530  2 
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
i915                  520615  3 
rtl8192ce              53641  0 
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
rtl8192c_common        48780  1 rtl8192ce
videodev              120310  2 uvcvideo,videobuf2_core
drm_kms_helper         49113  1 i915
rtlwifi                74788  1 rtl8192ce
drm                   288721  4 i915,drm_kms_helper
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
coretemp               13401  0 
joydev                 17458  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              540032  3 rtl8192ce,rtl8192c_common,rtlwifi
i2c_algo_bit           13414  1 i915
psmouse                95595  0 
microcode              22804  0 
toshiba_acpi           18727  0 
video                  19391  1 i915
snd                    78921  15 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13216  0 
sparse_keymap          13891  1 toshiba_acpi
mac_hid                13206  0 
mei                    40691  0 
wmi                    19071  1 toshiba_acpi
intel_ips              18244  0 
soundcore              15048  1 snd
cfg80211              206797  2 rtlwifi,mac80211
lpc_ich                17062  0 
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
ums_realtek            17950  0 
usb_storage            48834  1 ums_realtek
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
atl1c                  41102  0 
ahci                   25721  2 
libahci                31192  1 ahci




**** nm-tool ****






NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        60:EB:69:BC:4B:8C


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- Device: wlan0  [Depp Family] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        1C:65:9D:FC:3E:39


  Capabilities:
    Speed:           72 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *Depp Family:    Infra, 00:22:6B:55:9D:06, Freq 2462 MHz, Rate 54 Mb/s, Strength 63 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             207.255.176.37
    DNS:             207.255.176.40








**** NetworkManager.state ****




[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true




**** NetworkManager.conf ****




[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false




**** NetworkManager.conf-10.04 ****








**** interfaces ****




# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback




**** iwlist ****



```

---

