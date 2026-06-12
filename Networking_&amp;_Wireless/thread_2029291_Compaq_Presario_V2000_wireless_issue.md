---
title: "Compaq Presario V2000 wireless issue"
date: 2012-07-19
forum: Networking &amp; Wireless
---

### Post by bradley21073 on 2012-07-19
Greetings,
I recently installed Ubuntu 10.04 on my old Compaq Presario V2000. The wireless worked with Windows before I wiped it and installed Ubuntu.
I have looked around a bit and just cannot seem to get the wireless working. The wireless light also does not respond when I push the button (light up).
Any help would greatly appreciated!

---

### Post by praseodym on 2012-07-19
Hi,

please show the terminal (CTRL+ALT+T) outputs of:

```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
```

---

### Post by bradley21073 on 2012-07-19
brad@brad-linux:~$ uname -a
Linux brad-linux 2.6.32-41-generic #91-Ubuntu SMP Wed Jun 13 11:44:43 UTC 2012 i686 GNU/Linux

brad@brad-linux:~$ lspci -nnk | grep -ia2 net
    Kernel driver in use: radeon
    Kernel modules: radeonfb, radeon
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

brad@brad-linux:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
brad@brad-linux:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_atiixp_modem        9103  5 
snd_atiixp             12446  2 
snd_ac97_codec        100646  2 snd_atiixp_modem,snd_atiixp
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  6 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
arc4                    1153  2 
pcmcia                 30784  0 
snd_seq_oss            26722  0 
radeon                678607  3 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
ttm                    49847  1 radeon
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
drm_kms_helper         29329  1 radeon
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           20408  1 
video                  17375  0 
drm                   163779  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
i2c_piix4               8335  0 
snd                    54244  23 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                  3152  0 
sdhci_pci               5470  0 
rsrc_nonstatic         10015  1 yenta_socket
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
output                  1871  1 video
b43                   163556  0 
mac80211              205434  1 b43
joydev                  8740  0 
soundcore               6620  1 snd
sdhci                  15494  1 sdhci_pci
cfg80211              126528  2 b43,mac80211
ati_agp                 5094  0 
tifm_7xx1               3690  0 
snd_page_alloc          7076  3 snd_atiixp_modem,snd_atiixp,snd_pcm
tifm_core               6045  1 tifm_7xx1
led_class               2864  2 b43,sdhci
agpgart                31724  3 ttm,drm,ati_agp
shpchp                 28835  0 
psmouse                63677  0 
serio_raw               3978  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
8139too                18545  0 
ohci1394               26950  0 
8139cp                 16186  0 
pata_atiixp             3148  2 
ieee1394               81181  1 ohci1394
ssb                    38934  1 b43
mii                     4381  2 8139too,8139cp

brad@brad-linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by praseodym on 2012-07-20
You need to install the missing firmware. In 10.04:

```
sudo apt-get install b43-fwcutter
```

---

### Post by bradley21073 on 2012-07-20
Thank you very much! It is working as I type.:D

---

### Post by bradley21073 on 2012-07-20
And now its not? Same situation as before. The only thing has happened since my last message was I closed the laptop and reopened it, the wifi LED is not lit anymore and is unresponsive once again. And the it states "Networking has been disabled":(

---

### Post by bradley21073 on 2012-07-20
Okay, disregard. I figured out to rt click the network symbol.

Sorry to bother.

---

