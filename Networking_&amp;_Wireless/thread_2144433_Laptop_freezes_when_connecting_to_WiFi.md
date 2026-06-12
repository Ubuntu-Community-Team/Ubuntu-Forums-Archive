---
title: "Laptop freezes when connecting to WiFi"
date: 2013-05-12
forum: Networking &amp; Wireless
---

### Post by Mc837 on 2013-05-12
Hi everyone,

So I recently upgraded my [old Core 2 Duo laptop]("http://www.asus.com/Notebooks_Ultrabooks/X71SL/#specifications") from Vista to Ubuntu 13.04 as I would like to learn how to use Linux. Everything works fine until I try to connect to WiFi (ethernet works fine though). I saw another [similar post]("http://ubuntuforums.org/showthread.php?t=1733714") but I'm not sure if it can apply to me as well, and I don't know if it worked for the guy.

Anyway, here's the catch: I have 2 wireless adapters. The internal PCI-E one is an Atherox AR928X, while the PCMCIA one uses a Realtek 8176 chip (I keep this card as it also doubles as a USB3 port). So, when I try to connect to WiFi, or when the laptop tells me I'm disconnected, everything just freezes and I have to reboot.

Could it be an issue with drivers? Or are two wireless cards too many? I'm pretty sure the laptop itself is good enough since it ran Vista and Win7 flawlessly. Also, I tried Mint for a short while, but didn't have WiFi problems. Any ideas? Thanks in advance!

Additional info: the primary disk is a 64gb Kingston ssd (upgraded), secondary drive slot is empty, and to run any linux distro I have to boot with ACPI off.
Thanks again! :D

---

### Post by praseodym on 2013-05-12
Please open a terminal with CTRL+ALT+T and show these outputs:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by Mc837 on 2013-05-12
Sorry it took so long, it was a race against time. Also, it seems like the graphics driver crashed when everything froze. Yay! Funky colours!

 ```

mc837@Mc837-X71SL:~$ lspci -nnk | grep -iA2 net

00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1815]
    Kernel driver in use: sis190
--
02:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
    Subsystem: AzureWave AW-NE771 802.11bgn Wireless Mini PCIe Card [AR9281] [1a3b:1067]
    Kernel driver in use: ath9k



mc837@Mc837-X71SL:~$ lsusb

Bus 001 Device 002: ID 04f2:b012 Chicony Electronics Co., Ltd 1.3 MPixel UVC Webcam
Bus 001 Device 004: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
Bus 001 Device 005: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 003 Device 002: ID 0b05:1751 ASUSTek Computer, Inc. BT-253 Bluetooth Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub



mc837@Mc837-X71SL:~$ lsmod

Module                  Size  Used by
nls_iso8859_1          12713  1 
usb_storage            57204  1 
parport_pc             32688  0 
ppdev                  17073  0 
rfcomm                 42641  12 
bnep                   18036  2 
arc4                   12615  4 
joydev                 17377  0 
coretemp               13355  0 
ath9k                 149924  0 
ath9k_common           14055  1 ath9k
snd_hda_codec_realtek    78399  1 
snd_hda_intel          39619  3 
ath9k_hw              413680  2 ath9k_common,ath9k
uvcvideo               80847  0 
snd_hda_codec         136128  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
rtl8192cu              67699  0 
snd_pcm                97451  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
rtlwifi                79673  1 rtl8192cu
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
videobuf2_vmalloc      13056  1 uvcvideo
rtl8192c_common        48779  1 rtl8192cu
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
videobuf2_memops       13202  1 videobuf2_vmalloc
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
mac_hid                13205  0 
videobuf2_core         40513  1 uvcvideo
mac80211              606411  4 ath9k,rtlwifi,rtl8192c_common,rtl8192cu
r852                   18241  0 
videodev              129260  2 uvcvideo,videobuf2_core
ttm                    83187  0 
sm_common              16860  1 r852
snd                    68876  15 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
cfg80211              510937  4 ath,ath9k,mac80211,rtlwifi
btusb                  18334  0 
nand                   58949  2 r852,sm_common
microcode              22881  0 
nand_ecc               13273  1 nand
psmouse                95870  0 
drm_kms_helper         49394  0 
drm                   286313  2 ttm,drm_kms_helper
bluetooth             228619  22 bnep,btusb,rfcomm
serio_raw              13215  0 
i2c_algo_bit           13413  0 
nand_bch               13147  1 nand
bch                    17434  1 nand_bch
nand_ids               12723  1 nand
r592                   18019  0 
mtd                    45202  2 nand,sm_common
soundcore              12680  1 snd
memstick               16554  1 r592
sis_agp                13327  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
sdhci_pci              18590  0 
sdhci                  32522  1 sdhci_pci
firewire_ohci          40103  0 
firewire_core          64508  1 firewire_ohci
sata_sis               12823  2 
sis190                 22625  0 
crc_itu_t              12707  1 firewire_core



mc837@Mc837-X71SL:~$ iwconfig

wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


 mc837@Mc837-X71SL:~$ rfkill list

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no



mc837@Mc837-X71SL:~$ sudo iwlist scan

wlan1     No scan results

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0B:3B:22:87:6E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"devolo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002bc51579fe
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 00066465766F6C6F
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 02 - Address: 00:1E:52:7C:16:D2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"Apple Network Paola"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000927cf47e48
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 00134170706C65204E6574776F726B2050616F6C61
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706415420010D1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A0C501BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000400000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301690120
                    IE: Unknown: DD0E0017F20700010106001E527C16D2
                    IE: Unknown: DD0B0017F20100010100000003
          Cell 03 - Address: 00:90:D0:DB:F4:30
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"WLan748FEB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009278d4c354
                    Extra: Last beacon: 4120ms ago
                    IE: Unknown: 000A574C616E373438464542
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 04 - Address: 00:0B:3B:3E:67:00
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"devolo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a44073215e
                    Extra: Last beacon: 680ms ago
                    IE: Unknown: 00066465766F6C6F
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C

```

Thanks again!

---

### Post by praseodym on 2013-05-12
Try to update the rtl8188cus driver:
```

sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb
sudo dpkg -i rtl8192cu*.deb
echo -e "blacklist rtl8192cu\nblacklist rtl8192c_common\nblacklist rtlwifi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

Do you use a proprietary VGA driver?

Edit: Please show:

```
lspci -nnk | grep -iA2 VGA
```

---

### Post by Mc837 on 2013-05-12
Trying to update the drivers now, difficult since ethernet is giving problems too now. Could I perhaps download the packages from my desktop and install them manually?

Meanwhile, the VGA info.
```

mc837@Mc837-X71SL:~$ lspci -nnk | grep -iA2 VGA
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G98 [GeForce 9300M GS] [10de:06e9] (rev a1)
    Subsystem: ASUSTeK Computer Inc. U6V laptop [1043:19b2]
02:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)

```

Will update about the drivers ASAP.

---

### Post by praseodym on 2013-05-12
Boot into the recovery mode with networking and install the VGA driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential nvidia-current dkms
```
Reboot.

---

### Post by Mc837 on 2013-05-13
> **praseodym said:**
> 
```

sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb
sudo dpkg -i rtl8192cu*.deb
 echo -e "blacklist rtl8192cu\nblacklist rtl8192c_common\nblacklist rtlwifi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential nvidia-current dkms
```
 

 Had to boot in recovery mode with generic display drivers AND networking, but managed to do all of the above. Rebooted and logged in and everything works perfectly now, a lot faster and responsive, and no freezing. Thank you so much! :D

---

### Post by praseodym on 2013-05-13
Please check now:

"uname -a"

---

### Post by Mc837 on 2013-05-13
```

Linux Mc837-X71SL 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:35:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by praseodym on 2013-05-13
Ok, no need to do more.

Have fun.

---

### Post by Mc837 on 2013-05-13
Awesome, thanks! :D

---

### Post by Mc837 on 2013-05-13
Awesome, thanks! :D

---

