---
title: "Madwifi on ubuntu 13.04"
date: 2013-06-16
forum: Networking &amp; Wireless
---

### Post by Redstern on 2013-06-16
So after I installed ubuntu my network isn't working properly.  It only works half the time and is slow.  I read that installing madwifi driver should fix my problems but whenever I use the module-assistant to try to install it is says unable to locate package madwifi-source.  I know im supposed to add some kind of source to sources.list but I don't know exactly what to put in and where.  Everything I have tried has turned up an error when I update the sources.  Please help.

---

### Post by praseodym on 2013-06-16
Madwifi is not needed. Just deactivate the hardware encryption of the driver (here: example for ath9k, ath5k is similar)
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by Redstern on 2013-06-18
Still not working.  Stuff still only loads half the time.  I put in exactly what you said and it still doesn't work.

---

### Post by praseodym on 2013-06-18
Check:
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
sudo iwlist scan
```

---

### Post by Redstern on 2013-06-18
This is what all of them turned up


liam@liam-K53E:~$```
 lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6627]
    Kernel driver in use: ath9k
--
04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
    Kernel driver in use: atl1c
liam@liam-K53E:~$ lsmod
Module                  Size  Used by
ath9k                 149924  0 
ath9k_common           14055  1 ath9k
ath9k_hw              413680  2 ath9k_common,ath9k
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              606457  1 ath9k
cfg80211              510937  3 ath,ath9k,mac80211
nls_iso8859_1          12713  0 
usb_storage            57204  0 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228619  10 bnep,rfcomm
binfmt_misc            17500  1 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_realtek    78399  1 
joydev                 17377  0 
asus_nb_wmi            12854  0 
asus_wmi               24213  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
uvcvideo               80847  0 
aesni_intel            55399  1 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
videobuf2_vmalloc      13056  1 uvcvideo
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
videobuf2_memops       13202  1 videobuf2_vmalloc
wmi                    19070  1 asus_wmi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
videobuf2_core         40513  1 uvcvideo
arc4                   12615  2 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
videodev              129260  2 uvcvideo,videobuf2_core
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
mac_hid                13205  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
snd                    68876  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
i915                  600351  3 
video                  19390  2 i915,asus_wmi
microcode              22881  0 
drm_kms_helper         49394  1 i915
drm                   286313  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
soundcore              12680  1 snd
lpc_ich                17061  0 
mei                    41158  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
psmouse                95870  0 
serio_raw              13215  0 
ahci                   25731  2 
libahci                31364  1 ahci
atl1c                  41071  0 
liam@liam-K53E:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"AC SECURITY"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:CF:25:E7:C0   
          Bit Rate=65 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:23   Missed beacon:0

liam@liam-K53E:~$ sudo iwlist scan
[sudo] password for liam: 
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:CF:25:E7:C0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-33 dBm  
                    Encryption key:on
                    ESSID:"AC SECURITY"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001af690af09d
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 000B4143205345435552495459
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0E1017FFFFFF00010000000000000000000000000F0000000000
                    IE: Unknown: 3D1601000600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0509000C127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD7C0050F204104A0001101044000102103B000103104700102880288028801880A880001DCF25E7C0102100054152524953102300055447383532102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738353220526F75746572100800020084103C000101
          Cell 02 - Address: 00:1C:DF:38:4A:25
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"StebbimacWireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000a1c10e8fa5f
                    Extra: Last beacon: 200ms ago
                    IE: Unknown: 00115374656262696D6163576972656C657373
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000C4307000000
```

---

### Post by praseodym on 2013-06-18
Deactivate the power management```

sudo iwconfig wlan0 power off
```
and change the encryption in your router to WPA2-AES only instead of mixed WPA/WPA2

---

### Post by wildmanne39 on 2013-06-18
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

