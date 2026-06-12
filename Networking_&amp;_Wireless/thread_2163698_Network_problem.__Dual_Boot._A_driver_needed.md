---
title: "Network problem.  Dual Boot. A driver needed"
date: 2013-07-19
forum: Networking &amp; Wireless
---

### Post by Alxl on 2013-07-19
The owner of a Samsung laptop series 3 NP305E5A-A04US wants dual boot. 
 
So I used a DVD System Recovery Media to install Win7 Home Premium SP1 64bit without any problem. However DVD apparently did not have all drivers and internet access (wired and wireless) is not possible. 
 
So I searched the Samsung site and found 'Driver whiz' for searching/installing missing drivers. 
 
But after installing this 'Driver whiz' on the laptop, it promtly informed me that it needs internet access.  Needs a 'properly installed network adapter'. 
 
So at this point I just need one driver and don't know where to find it. 
 
A live-cd with Ubuntu 13.04 works fine with both wireless and wired connecions. 
 
Any suggestions appreciated

---

### Post by praseodym on 2013-07-19
Please show the output of these commands with Ubuntu Live-system:
```

lspci -nnk | grep -iA2 net
lsusb
pccardctl info
```

---

### Post by Alxl on 2013-07-19
Now it does not let me boot into the live-ubuntu-usb.
It lets me adjust the Boot to the USB and I save it but then it starts in Windows anyway.
I know that the live-USB is fine - I am writing this after startin desktop with it  
BTW I did not use the 'Driver whiz' as innitially thought but something called "Driver Tuner" apparently from Samsung.
Thank you very much.

---

### Post by praseodym on 2013-07-19
If Ubuntu boots, please take a screenshot from the commands

---

### Post by Alxl on 2013-07-19
Here are the outputs:
```
ubuntu@ubuntu:~$ lspci -nnk | grep -iA2 net 
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06) 
    Subsystem: Samsung Electronics Co Ltd Device [144d:c624] 
    Kernel driver in use: r8169 
-- 
04:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01) 
    Subsystem: Samsung Electronics Co Ltd Device [144d:4101] 
    Kernel driver in use: ath9k 
ubuntu@ubuntu:~$ lsusb 
Bus 001 Device 002: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive 
Bus 002 Device 002: ID 2232:1020   
Bus 004 Device 002: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader 
Bus 004 Device 003: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
ubuntu@ubuntu:~$ pccardctl info 
ubuntu@ubuntu:~$ pccardctl info 
ubuntu@ubuntu:~$
```

Wireless connection did not work.
Thanks

---

### Post by praseodym on 2013-07-19
Deactivate the hardware encryption of the driver:

```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k

```
Check:
```

iwconfig
lsmod
rfkill list
sudo iwlist scan
```

---

### Post by Alxl on 2013-07-19
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf 
options ath9k nohwcrypt=1 
 
sudo modprobe -rfv ath9k 
rmmod /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko 
rmmod /lib/modules/3.5.0-23-generic/kernel/net/mac80211/mac80211.ko 
rmmod /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
rmmod /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
rmmod /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/ath/ath.ko 
rmmod /lib/modules/3.5.0-23-generic/kernel/net/wireless/cfg80211.ko 
sudo modprobe -v ath9k 
insmod /lib/modules/3.5.0-23-generic/kernel/net/wireless/cfg80211.ko  
insmod /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/ath/ath.ko  
insmod /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko  
insmod /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko  
insmod /lib/modules/3.5.0-23-generic/kernel/net/mac80211/mac80211.ko  
insmod /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko nohwcrypt=1 
 
 
Check:Code: 
iwconfig 
wlan1     IEEE 802.11bgn  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on 
           
eth0      no wireless extensions. 
 
lo        no wireless extensions. 
 
lsmod 
ubuntu@ubuntu:~$ lsmod 
Module                  Size  Used by 
ath9k                 133133  0  
mac80211              555198  1 ath9k 
ath9k_common           14054  1 ath9k 
ath9k_hw              399665  2 ath9k,ath9k_common 
ath                    24124  3 ath9k,ath9k_common,ath9k_hw 
cfg80211              208382  3 ath9k,mac80211,ath 
dm_crypt               23126  0  
arc4                   12530  2  
snd_hda_codec_realtek    79756  1  
snd_hda_codec_hdmi     32476  1  
joydev                 17694  0  
snd_hda_intel          34117  5  
snd_hda_codec         135141  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel 
snd_hwdep              17765  1 snd_hda_codec 
uvcvideo               78117  0  
videobuf2_core         33025  1 uvcvideo 
videodev              125126  2 uvcvideo,videobuf2_core 
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
kvm_amd                56136  0  
kvm                   422160  1 kvm_amd 
snd_seq_midi           13325  0  
snd_rawmidi            30750  1 snd_seq_midi 
snd_seq_midi_event     14900  1 snd_seq_midi 
videobuf2_vmalloc      12861  1 uvcvideo 
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event 
snd_timer              29990  2 snd_pcm,snd_seq 
videobuf2_memops       13405  1 videobuf2_vmalloc 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq 
dm_multipath           23306  0  
microcode              23030  0  
psmouse               102075  0  
scsi_dh                14589  1 dm_multipath 
snd                    83674  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
samsung_laptop         18628  0  
i2c_piix4              13302  0  
serio_raw              13216  0  
k10temp                13174  0  
parport_pc             32867  0  
soundcore              15092  1 snd 
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm 
mac_hid                13254  0  
ppdev                  17114  0  
rfcomm                 47562  0  
bnep                   18240  2  
lp                     17800  0  
parport                46563  3 parport_pc,ppdev,lp 
bluetooth             211812  10 rfcomm,bnep 
squashfs               36801  1  
overlayfs              28353  1  
nls_utf8               12558  0  
isofs                  40307  0  
nls_iso8859_1          12714  2  
dm_raid45              78156  0  
xor                    17153  1 dm_raid45 
dm_mirror              22204  0  
dm_region_hash         20962  1 dm_mirror 
dm_log                 18565  3 dm_raid45,dm_mirror,dm_region_hash 
btrfs                 781017  0  
zlib_deflate           27140  1 btrfs 
libcrc32c              12645  1 btrfs 
hid_generic            12541  0  
usbhid                 47259  0  
hid                   100815  2 hid_generic,usbhid 
radeon                912794  3  
sdhci_pci              18749  0  
sdhci                  33145  1 sdhci_pci 
ttm                    88495  1 radeon 
drm_kms_helper         49259  1 radeon 
r8169                  62766  0  
drm                   290344  5 radeon,ttm,drm_kms_helper 
i2c_algo_bit           13565  1 radeon 
video                  19598  1 samsung_laptop 
usb_storage            49288  2  
ubuntu@ubuntu:~$  
 
rfkill list 
0: samsung-wlan: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
1: samsung-bluetooth: Bluetooth 
    Soft blocked: no 
    Hard blocked: no 
3: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
sudo iwlist scan 
 
 
0: samsung-wlan: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
1: samsung-bluetooth: Bluetooth 
    Soft blocked: no 
    Hard blocked: no 
3: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
ubuntu@ubuntu:~$ sudo iwlist scan 
wlan1     Scan completed : 
          Cell 01 - Address: 00:1D:etc 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=55/70  Signal level=-55 dBm   
                    Encryption key:on 
                    ESSID:"AirLink" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s 
                              18 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000000b8d53152 
                    Extra: Last beacon: 524ms ago 
                    IE: Unknown: 00074169724C696E6B 
                    IE: Unknown: 010882848B961224486C 
                    IE: Unknown: 030106 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 32040C183060 
                    IE: Unknown: 2D1A6E1013FFFF0000010000000000000000000000000C0000000000 
                    IE: Unknown: 3D1606070100000000000000000000000000000000000000 
                    IE: Unknown: 3E0100 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00 
                    IE: Unknown: 7F0101 
                    IE: Unknown: DD07000C4304000000 
                    IE: Unknown: 0706555320010B10 
                    IE: Unknown: DD1E00904C336E1013FFFF0000010000000000000000000000000C0000000000 
                    IE: Unknown: DD1A00904C3406070100000000000000000000000000000000000000 
          Cell 02 - Address: 48:F8etc 
                    Channel:1 
                    Frequency:2.412 GHz (Channel 1) 
                    Quality=28/70  Signal level=-82 dBm   
                    Encryption key:on 
                    ESSID:"AVPMayo2013" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000000a20d0519 
                    Extra: Last beacon: 76ms ago 
                    IE: Unknown: 000B4156504D61796F32303133 
                    IE: Unknown: 010882848B962430486C 
                    IE: Unknown: 030101 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32040C121860 
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000 
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000 
                    IE: Unknown: 4A0E14000A002C01C800140005001900 
                    IE: Unknown: 7F0101 
                    IE: Unknown: DD840050F204104A0001101044000102103B00010310470010B5BF9533408F72E9BFDB09A11F3FFDC810210005436973636F1023000D4C696E6B7379732045323530301024000776312E302E30371042000234321054000800060050F20400011011000D4C696E6B737973204532353030100800022688103C0001031049000600372A000120 
                    IE: Unknown: DD090010180201F0040000 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
          Cell 03 - Address: E0:91,,,,,,,,..... 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=29/70  Signal level=-81 dBm   
                    Encryption key:on 
                    ESSID:"Comphome" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000000b4fcd191 
                    Extra: Last beacon: 24332ms ago 
                    IE: Unknown: 0008436F6D70686F6D65 
                    IE: Unknown: 010882848B962430486C 
                    IE: Unknown: 030106 
                    IE: Unknown: 050400020000 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32040C121860 
                    IE: Unknown: DD270050F204104A0001101044000102104700103A235301C5D56D80B07F338F98A00303103C000103 
                    IE: Unknown: DD090010180200F0050000 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
 
eth0      Interface doesn't support scanning. 
 
lo        Interface doesn't support scanning. 
 
ubuntu@ubuntu:~$  

```

---

### Post by Alxl on 2013-07-19
In Ubuntu both wireless and wired work now.
But neither works in Windows.
Thank you very much for your help

---

