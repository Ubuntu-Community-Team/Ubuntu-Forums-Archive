---
title: "Wrong Connection Information"
date: 2013-02-01
forum: Networking &amp; Wireless
---

### Post by bj44 on 2013-02-01
Hi,

Not quite understand this. The Network Manager "Connection Information" shows the speed of 150 Mb/s instead of 300 Mb/s for my wireless card that is N300.
I do recall up to Ubuntu 11.10 the speed was always 300 Mb/s. Now that I have moved to Ubuntu 12.10 I am only getting half of what I actually should be getting (I am only 4 ft from the router). 
Does anyone have any idea what's going on here?

TYIA!

---

### Post by praseodym on 2013-02-02
Hi,

150M is the theoretical maximum in the 2,4 GHz region. For "full draft-N" you need the 5GHz region. "300M" is also only theoretical.

---

### Post by bj44 on 2013-02-02
Hi,

I am not sure this is the actual or theoretical value. As I indicated my wireless N300 adaptor is 4 ft from the router and Network Manager "Connection Information" as well as "iwconfig" Bit Rate output both show 150 Mb/s.
If I move further from the router this value drops to lower number, that is why I think it is the actual value.

---

### Post by praseodym on 2013-02-02
Please show:
```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
iwlist chan
sudo iwlist scan
```

---

### Post by bj44 on 2013-02-02
Here they are and thanks for your help...
BTW, can not get the Centrino 6150 to work so I am using Belkin USB N300 adaptor.


# lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0885] (rev 67)
	Subsystem: Intel Corporation Centrino Wireless-N + WiMAX 6150 BGN [8086:1305]
	Kernel modules: iwlwifi
--
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
	Kernel driver in use: atl1c
#


# lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:07d6 Intel Corp. 
Bus 001 Device 004: ID 058f:a014 Alcor Micro Corp. Asus Integrated Webcam
Bus 002 Device 003: ID 050d:845a Belkin Components F7D2101 802.11n Surf & Share Wireless Adapter v1000 [Realtek RTL8192SU]
#


# lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78048  1 
coretemp               13401  0 
kvm_intel             132760  0 
kvm                   414071  1 kvm_intel
ghash_clmulni_intel    13221  0 
aesni_intel            51038  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
asus_nb_wmi            12711  0 
asus_wmi               24089  1 asus_nb_wmi
sparse_keymap          13891  1 asus_wmi
microcode              22804  0 
r8712u                187939  0 
lpc_ich                17062  0 
snd_hda_intel          33492  3 
psmouse                95595  0 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
serio_raw              13216  0 
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
joydev                 17458  0 
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
snd_seq_midi_event     14900  1 snd_seq_midi
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
mac_hid                13206  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  520621  4 
wmi                    19071  1 asus_wmi
drm_kms_helper         49113  1 i915
drm                   288721  5 i915,drm_kms_helper
bnep                   18141  2 
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13414  1 i915
rfcomm                 46620  0 
parport_pc             32689  0 
soundcore              15048  1 snd
video                  19336  1 i915
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
bluetooth             209249  10 bnep,rfcomm
ppdev                  17074  0 
mei                    40691  0 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
nls_iso8859_1          12714  1 
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
atl1c                  41102  0 
#

---

### Post by bj44 on 2013-02-02
Here is the rest. Sorry could not send it in one post.

# iwconfig
wlan1     IEEE 802.11bgn  ESSID:"------"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 28:10:7B:F2:D9:5C   
          Bit Rate:150 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-****-****   Security mode:open
          Power Management:off
          Link Quality=96/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

#


# iwlist chan
wlan1     14 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)

eth0      no frequency information.

lo        no frequency information.

#


# iwlist scan
wlan1     Scan completed :
          Cell 01 - Address: 28:10:7B:F2:D9:5C
                    ESSID:"------"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
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
                    Signal level=100/100  
          Cell 02 - Address: 00:26:F3:7C:98:48
                    ESSID:"------"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A8800026F37C9848103C000101
                    Signal level=44/100  
          Cell 03 - Address: 00:26:F3:7C:98:49
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=43/100  
          Cell 04 - Address: 00:26:F3:7C:98:4A
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Signal level=44/100  
          Cell 05 - Address: 00:26:F3:7C:98:4B
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Signal level=43/100  

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

#

---

### Post by praseodym on 2013-02-02
For the Centrino: 

Deactivate the N-mode of the driver:
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

In general:

Update your country code settings:
```

sudo apt-get install iw
iw reg get
sudo iw reg set DE [COLOR="Red"]#change DE for Germany with your country code[/COLOR]
iw reg get
```
Check:
```

iwlist chan
```
As you see, only 2,4GHz region is shown!

---

### Post by bj44 on 2013-02-02
Thanks again, deactivating of the N-mode of the driver did not help. Still Centrino wireless card communicates with router via N-mode. Added an option to conf file "bt_coex_active=0"  and that helped to connect. Still very slow wireless, and the cause I think is the Intel card inside of this ASUS laptop.  I don't think iwlwifi driver is the problem because it is fine on my other laptop and is pulling fast.
Changed the country code to US and not sure why that was not there at first place. I'll be monitoring this for further errors and messages...

---

