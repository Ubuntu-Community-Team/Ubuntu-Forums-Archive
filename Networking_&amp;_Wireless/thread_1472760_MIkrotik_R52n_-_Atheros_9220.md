---
title: "MIkrotik R52n - Atheros 9220"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by abudabi on 2010-05-04
Excuse the noobness... this is my 1st linux installation
 
I have this [miniPCI wireless card]("http://www.routerboard.com/pricelist.php?showProduct=72") plugged into this [riser card]("http://www.routerboard.com/pricelist.php?showProduct=74") which plugs into my HTPC that runs Karmic. 2 omni antennas are plugged into the card.
 
Network manager has got wireless enabled, but it can't seem to pick up any SSIDs? It looks like the ath9k driver is successfully loaded but no comms?
 
What am I doing wrong? 
 
 
lspci gives
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:06.0 Network controller: Atheros Communications Inc. AR922X Wireless Network Adapter (rev 01)
00:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:08.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

```
 
lsmod gives:
```
Module                  Size  Used by
binfmt_misc             8356  1 
vboxnetflt             84840  1 
vboxnetadp             78344  0 
vboxdrv               121160  2 vboxnetflt
snd_emu10k1_synth       6140  0 
snd_emux_synth         32860  1 snd_emu10k1_synth
snd_seq_virmidi         5628  1 snd_emux_synth
snd_seq_midi_emul       6332  1 snd_emux_synth
snd_emu10k1           135136  19 snd_emu10k1_synth
snd_ac97_codec        101216  1 snd_emu10k1
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  6 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          9156  2 snd_emu10k1,snd_pcm
snd_util_mem            4156  2 snd_emux_synth,snd_emu10k1
snd_hwdep               7200  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      6940  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                50224  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  14 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          6920  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  35 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iptable_filter          3100  0 
arc4                    1660  2 
nvidia               9586440  48 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
lp                      8964  0 
ecb                     2524  2 
ath9k                 258744  0 
mac80211              181236  1 ath9k
led_class               4096  1 ath9k
ath                     8060  1 ath9k
ppdev                   6688  0 
soundcore               7264  1 snd
parport_pc             31940  1 
parport                35340  3 lp,ppdev,parport_pc
cfg80211               93052  3 ath9k,mac80211,ath
psmouse                56180  0 
serio_raw               5280  0 
joydev                 10272  0 
shpchp                 32272  0 
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usbhid                 38208  1 
ums_cypress             3100  0 
usb_storage            52544  4 ums_cypress
floppy                 54916  0 
8139too                22620  0 
sis_agp                 6972  1 
8139cp                 19260  0 
agpgart                34988  2 nvidia,sis_agp
mii                     5212  2 8139too,8139cp

```
 
 
iwconfig gives:
```
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
vboxnet0  no wireless extensions.

```
 
 
and lastly cat /proc/net/dev gives
```
Inter-|   Receive                                                |  Transmit
 face |bytes    packets errs drop fifo frame compressed multicast|bytes    packets errs drop fifo colls carrier compressed
    lo:2743215341 3728893    0    0    0     0          0         0 2743215341 3728893    0    0    0     0       0          0
  eth0:682808607 25938459    3    0    0     0          0         0 2161784893 34415245    0    0   20     0       0          0
wmaster0:       0       0    0    0    0     0          0         0        0       0    0    0    0     0       0          0
 wlan0:       0       0    0    0    0     0          0         0        0       0    0    0    0     0       0          0
vboxnet0:       0       0    0    0    0     0          0         0  3171732    9753    0    0    0     0       0          0

```
 
 
Hope someone can help me decipher this mystery. I ultimately want to use this wireless card as an AP that my laptop can connect to, but 1st I need it to function properly.
 
 
Thanks

---

### Post by abudabi on 2010-05-05
sorry.. forgot to add.. iwlist scan gives no results

---

