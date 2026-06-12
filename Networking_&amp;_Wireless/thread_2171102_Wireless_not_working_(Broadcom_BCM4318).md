---
title: "Wireless not working? (Broadcom_BCM4318)"
date: 2013-08-29
forum: Networking &amp; Wireless
---

### Post by TBwbbnt on 2013-08-29
Sorry for this? but i don't understand where is the problem, i read many threads([http://ubuntuforums.org/showthread.php?t=1966633](http://ubuntuforums.org/showthread.php?t=1966633) , [http://ubuntuforums.org/showthread.php?t=1879096](http://ubuntuforums.org/showthread.php?t=1879096)) but its still not worked
```
lsmod
```:

```
Module                  Size  Used by
nls_iso8859_1          12617  1 
bnep                   17852  2 
rfcomm                 38400  0 
bluetooth             211435  10 bnep,rfcomm
parport_pc             27612  0 
ppdev                  12849  0 
arc4                   12509  2 
snd_hda_codec_realtek    65004  1 
snd_hda_codec_si3054    12864  1 
b43                   364596  0 
snd_hda_intel          38819  6 
snd_hda_codec         118613  3 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel
radeon                892298  3 
coretemp               13324  0 
mac80211              541819  1 b43
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  5 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
r852                   17873  0 
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
sm_common              16772  1 r852
nand                   54027  2 r852,sm_common
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17329  0 
ttm                    72088  1 radeon
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
cfg80211              453853  2 b43,mac80211
mtd                    38990  2 sm_common,nand
snd_timer              28931  2 snd_pcm,snd_seq
pcmcia                 39854  0 
nand_ids                8547  1 nand
drm_kms_helper         47749  1 radeon
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
nand_bch               13003  1 nand
drm                   233935  5 radeon,ttm,drm_kms_helper
bch                    21767  1 nand_bch
yenta_socket           27427  0 
r592                   17808  0 
microcode              18433  0 
samsung_laptop         18195  0 
pcmcia_rsrc            18367  1 yenta_socket
nand_ecc               13105  1 nand
memstick               15885  1 r592
psmouse                82769  0 
snd                    57014  20 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              13031  0 
i2c_algo_bit           13316  1 radeon
bcma                   39810  1 b43
video                  19116  1 samsung_laptop
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
i2c_piix4              13227  0 
shpchp                 32265  0 
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            48053  1 
8139too                27407  0 
pata_acpi              12886  0 
8139cp                 26728  0 
sdhci_pci              18265  0 
sdhci                  32339  1 sdhci_pci
ssb                    51554  1 b43
pata_atiixp            13058  2 
```

```
lspci -nnk | grep -iA2 net
```:
```
02:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c02b]
    Kernel driver in use: 8139too
--
02:07.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: ASUSTeK Computer Inc. A6U notebook embedded card [1043:120f]
    Kernel driver in use: b43-pci-bridge


```
```
iwconfig
```
```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.


```

```
rfkill list all
```

```
0: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```
](*,)
Drivers are installed, for bcm4318 from synaptic (b43-fwcutter, firmware-br43-installer)

---

### Post by 1/0 on 2013-08-29
Anything "SIOCSIFFLAGS: No such file or directory"?

Have you follewed [this document]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")?

---

### Post by TBwbbnt on 2013-08-29
> **1/0 said:**
> Anything "SIOCSIFFLAGS: No such file or directory"?

Have you follewed [this document]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")?

No errors like SIOCSIFFLAGS: No such file or directory
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) - i installed drivers from instructions of this page earlier

---

### Post by TBwbbnt on 2013-08-30
I have find chain, when i run 
```
sudo modprobe -r b43 ssb
sudo modprobe ssb
sudo modprobe b43
sudo /etc/init.d/networking restart

```
after 30 seconds wlan find my router, and internet working

---

