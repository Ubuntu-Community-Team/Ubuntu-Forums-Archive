---
title: "Connected to network but no network access?"
date: 2011-12-20
forum: Networking &amp; Wireless
---

### Post by ZCDW9 on 2011-12-20
Hi all,

Recently installed 11.10 on a Dell Dimension 3100 with a ZyAir G260 USB wireless adapter.

After a bit of a struggle, I've got the device recognised with ndiswrapper and connecting at startup. I'm finding, however, that I may have network access for a short time, but it will then drop. Apparently I'm still connected to the network but I can't access anything on the web or even ping the router. 

First time using Ubuntu but reasonably techie-minded.

Bit confused, any help appreciated!

---

### Post by praseodym on 2011-12-20
Hi,

please show the terminal (CTRL+ALT+T) outputs of

```
lsusb
lsmod
iwconfig
sudo iwlist scan
rfkill list
```

---

### Post by ZCDW9 on 2011-12-20
Hello there,

As requested:

```
valerie@Desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04a9:1716 Canon, Inc. MP460 Composite
Bus 001 Device 005: ID 0586:3408 ZyXEL Communications Corp. 
Bus 002 Device 002: ID 413c:3200 Dell Computer Corp. Mouse
Bus 003 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 006: ID 0781:5567 SanDisk Corp. Cruzer Blade
valerie@Desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
rfcomm                 38408  0 
bnep                   17923  2 
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  2 
binfmt_misc            17292  1 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
i915                  505108  3 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
dcdbas                 14098  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         32889  1 i915
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  18160  0 
drm                   192226  4 i915,drm_kms_helper
bluetooth             148839  11 rfcomm,bnep,btusb
ndiswrapper           193669  0 
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
psmouse                73673  0 
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
parport                40930  3 parport_pc,ppdev,lp
serio_raw              12990  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
e100                   36289  0 
usb_storage            44173  1 
uas                    17699  0 
valerie@Desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"BTVOYAGER2110-D7"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:16:E3:E7:73:D7   
          Bit Rate=54 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:67/100  Signal level:-53 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

valerie@Desktop:~$ sudo iwlist scan
[sudo] password for valerie: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

rfwlan0     Scan completed :
          Cell 01 - Address: 00:16:E3:E7:73:D7
                    ESSID:"BTVOYAGER2110-D7"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:67/100  Signal level:-53 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 64:16:F0:B7:08:3D
                    ESSID:"Vodafone_083E"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 50:67:F0:9E:A9:D5
                    ESSID:"eircom46530232"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 40:4A:03:C1:89:86
                    ESSID:"eircom34605215"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

valerie@Desktop:~$ rfkill list
valerie@Desktop:~$ 

```

---

### Post by praseodym on 2011-12-20
Try another channel, e.g. channel 1. Can you use WPA2-AES encryption instead of WEP?

---

### Post by ZCDW9 on 2011-12-20
Appears to be working fine after doing both, thanks very much!

---

