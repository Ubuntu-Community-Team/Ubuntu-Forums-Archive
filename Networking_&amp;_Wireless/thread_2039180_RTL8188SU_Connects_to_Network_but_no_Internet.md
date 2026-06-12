---
title: "RTL8188SU Connects to Network but no Internet"
date: 2012-08-08
forum: Networking &amp; Wireless
---

### Post by sumps on 2012-08-08
I have a strange problem with my new RTL8188SU based USB wireless adaptor. I am running V12.04 (fully updated) on a netbook and when I plug the wireless adaptor in, it is detected and it connects to my home network (WPA PSK/WPA2-PSK with AES encryption). However when I run Firefox, I get an "Unable to Connect to Server" error.

The RTL8188SU uses the RTL8712 driver and when I do a dmesg | grep 8172 it appears that everything is OK - no errors or warnings.

I was previously using an RTL8187L adaptor and this still works fine on the same netbook connecting to the same network, as does my  wired connection.

The RTL8188SU adaptor is getting valid IP address, Subnet mask, Gateway and DNS server settings but something is stopping it from working correctly - I cannot even Ping the router.

Any ideas ? :confused:

---

### Post by praseodym on 2012-08-08
Please show:

```
lsusb
lsmod
iwconfig
route -n
sudo iwlist scan
iwlist chan
dmesg | egrep 'country|8712'
```
Which country do you live?

---

### Post by sumps on 2012-08-10
Hi thanks for the quick response, here are the outputs of the commands you suggested...[INDENT][I]paul@Pauls-Linux-Laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 2020:1005  
Bus 001 Device 004: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 005: ID 05e1:0100 Syntek Semiconductor Co., Ltd 802.11g + Bluetooth Wireless Adapter
Bus 001 Device 006: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter
paul@Pauls-Linux-Laptop:~$ lsmod
Module                  Size  Used by
snd_hda_codec_realtek   174134  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
r8712u                163845  0 
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
psmouse                87213  0 
serio_raw              13027  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  414668  3 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
topstar_laptop         12728  0 
sparse_keymap          13658  1 topstar_laptop
parport_pc             32114  0 
rfcomm                 38139  0 
bnep                   17830  2 
ppdev                  12849  0 
bluetooth             158438  10 bnep,rfcomm
video                  19068  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 
paul@Pauls-Linux-Laptop:~$ iwconfig
wlan2     IEEE 802.11bgn  ESSID:"TP-LINK_E136AE"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.427 GHz  Access Point: 74:EA:3A:E1:36:AE   
          Bit Rate:150 Mb/s   Sensitivity:0/0  
          Retryff   RTS thr off   Fragment thr off
          Power Management off
          Link Quality=98/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

paul@Pauls-Linux-Laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan2
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan2
paul@Pauls-Linux-Laptop:~$ sudo iwlist scan
[sudo] password for paul: 
wlan2     Scan completed :
          Cell 01 - Address: 74:EA:3A:E1:36:AE
                    ESSID:"TP-LINK_E136AE"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Encryption key on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Signal level=100/100  
          Cell 02 - Address: 84:1B:5E:9F:24:7C
                    ESSID:"virginmedia3838171"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    Signal level=26/100  
          Cell 03 - Address: 30:46:9A:7B:AF:31
                    ESSID:"Good"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Signal level=7/100  
          Cell 04 - Address: 00:24:B2:F8:27:7E
                    ESSID:"SKY99664"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd180050f20101000050f20201000050f20201000050f2020000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Signal level=7/100  
          Cell 05 - Address: A0:21:B7:EC:3E:42
                    ESSID:"nellys"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    Signal level=7/100  
          Cell 06 - Address: 00:1F:33:17:24:A9
                    ESSID:"Tresidder"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=7/100  

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

paul@Pauls-Linux-Laptop:~$ iwlist chan
wlan2     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.427 GHz (Channel 4)

lo        no frequency information.

eth0      no frequency information.

paul@Pauls-Linux-Laptop:~$ dmesg | egrep 'country|8712'
[    0.387128] pnp 00:02: [io  0x0000-0x001f]
[   21.187355] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   21.224536] r8712u: DriverVersion: v7_0.20100831
[   21.224585] r8712u: register rtl8712_netdev_ops to netdev_ops
[   21.224595] r8712u: USB_SPEED_HIGH with 4 endpoints
[   21.225333] r8712u: Boot from EFUSE: Autoload OK
[   22.807810] r8712u: CustomerID = 0x0000
[   22.807819] r8712u: MAC Address from efuse = 00:1a:ef:1a:55:aa
[   22.807825] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   22.811288] usbcore: registered new interface driver r8712u
[   23.880579] r8712u: 1 RCR=0x153f00e
[   23.881348] r8712u: 2 RCR=0x553f00e
[  375.093870] r8712u: [r8712_got_addbareq_event_callback] mac = 74:ea:3a:e1:36:ae, seq = 0, tid = 0
paul@Pauls-Linux-Laptop:~$ [/I]
[/INDENT]Hope you can spot something in these that I have missed. I live in the UK.

Look forward to any suggestions/ideas.

Best regards
Sumps

---

### Post by praseodym on 2012-08-10
Change the encryption mode to pure WPA2-AES (CCMP) if possible. Country settings:

> sudo apt-get install iw
iw reg get
sudo iw reg set UK
iw reg get
iwlist chan
dmesg | grep country

---

