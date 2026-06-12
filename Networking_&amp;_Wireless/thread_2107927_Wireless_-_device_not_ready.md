---
title: "Wireless - device not ready"
date: 2013-01-23
forum: Networking &amp; Wireless
---

### Post by Narciso91 on 2013-01-23
Hello everybody,
I am trying to use wireless connection on my old pc, but without success.
Everything works like  a charm but wifi. In network manager it says "device not ready" and sometimes, after a reboot, "disabled".
I am really going crazy, because I can't understand what the problem is!
Here are some informations which might be helpful

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
Linux karl-pc 3.2.0-36-generic-pae #57-Ubuntu SMP Tue Jan 8 22:01:06 UTC 2013 i686 i686 i386 GNU/Linux

``````
04:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:0241]
    Kernel driver in use: 8139too
--
04:09.0 Network controller [0280]: Ralink corp. RT2500 Wireless 802.11bg [1814:0201] (rev 01)
    Kernel driver in use: rt2500pci
    Kernel modules: rt2500pci

``````
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0db0:a970 Micro Star International Bluetooth dongle
Bus 002 Device 003: ID 13ee:0003 MosArt Optical Mouse

``````
karl@karl-pc:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

``````
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``````
Module                  Size  Used by
usbhid                 41937  0 
hid                    77428  1 usbhid
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
arc4                   12473  2 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   174313  1 
pcmcia                 39826  0 
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  5 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
btusb                  17948  1 
bluetooth             158479  13 rfcomm,bnep,btusb
radeon                737926  2 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
rt2500pci              22948  0 
rt2x00pci              14202  1 rt2500pci
rt2x00lib              48875  2 rt2500pci,rt2x00pci
mac80211              436493  2 rt2x00pci,rt2x00lib
ttm                    65344  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              178877  2 rt2x00lib,mac80211
psmouse                86520  0 
drm_kms_helper         45466  1 radeon
serio_raw              13027  0 
drm                   197641  4 radeon,ttm,drm_kms_helper
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
snd_timer              28931  2 snd_pcm,snd_seq
eeprom_93cx6           12687  1 rt2500pci
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13199  1 radeon
video                  19068  0 
shpchp                 32325  0 
ati_agp                13242  0 
snd                    62218  18 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4              13093  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56940  1 firewire_ohci
8139too                23283  0 
sdhci_pci              18324  0 
crc_itu_t              12627  1 firewire_core
sdhci                  28241  1 sdhci_pci
8139cp                 26759  0 
pata_atiixp            12999  2 

```Thank you very much and sorry for any grammar mistake!

---

### Post by jonobr on 2013-01-23
try opening a terminal

enter ```
echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

restart

see how that works

---

### Post by Narciso91 on 2013-03-18
Hello!
I am sorry if I just answer now, but I've been very busy.
Unfortunately this command was not enough, nothing happened!

---

