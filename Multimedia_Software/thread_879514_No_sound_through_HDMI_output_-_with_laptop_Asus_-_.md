---
title: "No sound through HDMI output - with laptop Asus - M50Sa"
date: 2008-08-04
forum: Multimedia Software
---

### Post by dobrichkia on 2008-08-04
Hi, my laptop is Asus - M50Sa
(
CPU T8300 - 2x2.4GHz
RAM - 4Gb
VIDEO - ATI HD3470
WIFI - Intel 4965AGN
......
)

```

# uname -a
Linux ilia-asus-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux

```

```

# lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
06:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
07:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
08:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
08:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

```

# cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebf8000 irq 22
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfdeec000 irq 17

```

```

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

# aplay -L
default:CARD=Intel
    HDA Intel, ALC883 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
front:CARD=HDMI
    HDA ATI HDMI
    Front speakers
surround40:CARD=HDMI
    HDA ATI HDMI
    4.0 Surround output to Front and Rear speakers
surround41:CARD=HDMI
    HDA ATI HDMI
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=HDMI
    HDA ATI HDMI
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=HDMI
    HDA ATI HDMI
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=HDMI
    HDA ATI HDMI
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers

```

```

# cat /proc/asound/card1/codec#*
Codec: Generic 1002 ATI R6xx HDMI
Address: 0
Vendor Id: 0x1002aa01
Subsystem Id: 0xaa0100
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x40]: 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x0894: OUT Detect R/L
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02

```

```

# speaker-test -D plughw:1,3

speaker-test 1.0.15

Playback device is plughw:1,3
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
Time per period = 2.729646
 0 - Front Left
Time per period = 2.986778
 0 - Front Left
Time per period = 2.986804
 0 - Front Left
Time per period = 2.986776
 0 - Front Left

```

```

# aplay -D default:CARD=Intel ./Noise.wav
Playing WAVE './Noise.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
# aplay -D front:CARD=HDMI ./Noise.wav
aplay: main:546: audio open error: No such file or directory

```

```

# modinfo snd-hda-intel
filename:       /lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
description:    Intel HDA driver
license:        GPL
srcversion:     788923729243CAF84C8707E
alias:          pci:v000010DEd00000AC3sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000AC2sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000AC1sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000AC0sv*sd*bc*sc*i*
alias:          pci:v000010DEd000007FDsv*sd*bc*sc*i*
alias:          pci:v000010DEd000007FCsv*sd*bc*sc*i*
alias:          pci:v000010DEd00000777sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000776sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000775sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000774sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000055Dsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000055Csv*sd*bc*sc*i*
alias:          pci:v000010DEd0000044Bsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000044Asv*sd*bc*sc*i*
alias:          pci:v000010DEd000003F0sv*sd*bc*sc*i*
alias:          pci:v000010DEd000003E4sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000371sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000026Csv*sd*bc*sc*i*
alias:          pci:v000010B9d00005461sv*sd*bc*sc*i*
alias:          pci:v00001039d00007502sv*sd*bc*sc*i*
alias:          pci:v00001106d00003288sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA48sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA40sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA38sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA30sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA28sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA20sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA18sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA10sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA08sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA00sv*sd*bc*sc*i*
alias:          pci:v00001002d0000960Fsv*sd*bc*sc*i*
alias:          pci:v00001002d00007919sv*sd*bc*sc*i*
alias:          pci:v00001002d0000793Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00004383sv*sd*bc*sc*i*
alias:          pci:v00001002d0000437Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000811Bsv*sd*bc*sc*i*
alias:          pci:v00008086d00003A6Esv*sd*bc*sc*i*
alias:          pci:v00008086d00003A3Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000293Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000293Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000284Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000269Asv*sd*bc*sc*i*
alias:          pci:v00008086d000027D8sv*sd*bc*sc*i*
alias:          pci:v00008086d00002668sv*sd*bc*sc*i*
depends:        snd-pcm,snd-page-alloc,snd,snd-hwdep
vermagic:       2.6.24-19-generic SMP mod_unload
parm:           power_save:Automatic power-saving timeout (in second, 0 = disable). (int)
parm:           index:Index value for Intel HD audio interface. (array of int)
parm:           id:ID string for Intel HD audio interface. (array of charp)
parm:           enable:Enable Intel HD audio interface. (array of bool)
parm:           model:Use the given board model. (array of charp)
parm:           position_fix:Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size). (array of int)
parm:           probe_mask:Bitmask to probe codecs (default = -1). (array of int)
parm:           single_cmd:Use single command to communicate with codecs (for debugging only). (bool)
parm:           enable_msi:Enable Message Signaled Interrupt (MSI) (int)
parm:           power_save_controller:Reset controller in power save mode. (bool)

```

```

# lsmod
Module                  Size  Used by
xt_TCPMSS               6272  1
xt_tcpmss               3840  1
xt_tcpudp               4992  1
iptable_mangle          4480  1
pppoe                  16896  2
pppox                   5784  1 pppoe
af_packet              27272  2
ppp_generic            33568  6 pppoe,pppox
slhc                    8192  1 ppp_generic
rfcomm                 47392  2
l2cap                  28800  13 rfcomm
ppdev                  11400  0
acpi_cpufreq           10832  2
cpufreq_userspace       6180  0
cpufreq_stats           8416  0
cpufreq_powersave       3200  0
cpufreq_ondemand       11152  1
freq_table              6464  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    10632  0
sbs                    17808  0
sbshc                   8960  1 sbs
container               6656  0
dock                   12960  0
iptable_filter          4608  0
ip_tables              24104  2 iptable_mangle,iptable_filter
x_tables               23560  4 xt_TCPMSS,xt_tcpmss,xt_tcpudp,ip_tables
aes_x86_64             26920  0
dm_crypt               16776  0
dm_mod                 71160  1 dm_crypt
ipv6                  311848  20
sbp2                   27272  0
parport_pc             41128  0
lp                     14916  0
parport                44300  3 ppdev,parport_pc,lp
arc4                    3456  2
ecb                     5248  2
blkcipher               9476  1 ecb
snd_seq_dummy           5764  0
snd_seq_oss            38912  0
snd_seq_midi           10688  0
snd_hda_intel         440408  2
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
joydev                 15488  0
snd_pcm_oss            47648  0
snd_mixer_oss          20224  1 snd_pcm_oss
iwl4965               118516  0
hci_usb                19228  2
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               62084  0
compat_ioctl32         11136  1 uvcvideo
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss
iwlwifi_mac80211      251876  1 iwl4965
videodev               30720  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              27912  2 snd_seq,snd_pcm
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
fglrx                1804800  24
bluetooth              67748  7 rfcomm,l2cap,hci_usb
video                  23444  0
cfg80211               17680  1 iwlwifi_mac80211
snd_hwdep              12552  1 snd_hda_intel
sky2                   53892  0
output                  5632  1 video
psmouse                46236  0
sdhci                  21508  0
battery                16776  0
snd                    70856  15 

snd_seq_dummy,snd_seq_oss,snd_hda_intel,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_pcm,snd_seq_device,snd_tim

er,snd_hwdep
asus_laptop            22492  0
serio_raw               9092  0
iTCO_wdt               15312  0
iTCO_vendor_support     5764  1 iTCO_wdt
mmc_core               59272  1 sdhci
ac                      8328  0
ricoh_mmc               5120  0
tpm_infineon           11836  0
tpm                    19488  1 tpm_infineon
led_class               7176  1 asus_laptop
button                 10912  0
intel_agp              30624  0
tpm_bios                9728  1 tpm
soundcore              10400  1 snd
evdev                  14976  5
pcspkr                  4992  0
shpchp                 38172  0
pci_hotplug            34608  1 shpchp
sr_mod                 20132  0
cdrom                  41512  1 sr_mod
pata_acpi               9856  0
usbhid                 35296  0
hid                    44992  1 usbhid
xfs                   562152  1
sg                     41880  0
sd_mod                 33280  3
ata_piix               24196  0
ohci1394               36532  0
ieee1394              106968  2 sbp2,ohci1394
ata_generic             9988  0
ahci                   33028  2
libata                176432  4 pata_acpi,ata_piix,ata_generic,ahci
scsi_mod              178488  5 sbp2,sr_mod,sg,sd_mod,libata
ehci_hcd               41996  0
uhci_hcd               29856  0
usbcore               169904  6 hci_usb,uvcvideo,usbhid,ehci_hcd,uhci_hcd
thermal                19744  0
processor              41448  4 acpi_cpufreq,thermal
fan                     6792  0
fbcon                  46336  0
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  1

```

```

# cat /proc/asound/devices
  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
  5: [ 0- 1]: hardware dependent
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 22: [ 0- 6]: digital audio playback
 24: [ 0- 0]: digital audio capture
 26: [ 0- 2]: digital audio capture
 30: [ 0- 6]: digital audio capture
 32: [ 1]   : control
 33:        : timer
 36: [ 1- 0]: hardware dependent
 51: [ 1- 3]: digital audio playback

```

```

# cat /proc/asound/card1/pcm3p/info
card: 1
device: 3
subdevice: 0
stream: PLAYBACK
id: ATI HDMI
name: ATI HDMI
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 1

```

```
custom /tmp/alsa-info.txt

!!ALSA Information Script v 0.4.48
!!Script ran on: Mon Aug  4 13:54:48 EEST 2008

Ubuntu 8.04.1 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 8.04.1"


!!ALSA Version
!!------------

Driver version:     1.0.16
Library version:
Utilities version:  1.0.15


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_hda_intel



!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-hda-intel: model=haier-w66


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
enable : Y,Y,Y,Y,Y,Y,Y,Y
enable_msi : 0
id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
index : -1,-1,-1,-1,-1,-1,-1,-1
model : haier-w66,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
position_fix : 0,0,0,0,0,0,0,0
power_save : 0
power_save_controller : Y
probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
single_cmd : N

!!Module: snd_hda_intel
enable : Y,Y,Y,Y,Y,Y,Y,Y
enable_msi : 0
id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
index : -1,-1,-1,-1,-1,-1,-1,-1
model : haier-w66,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
position_fix : 0,0,0,0,0,0,0,0
power_save : 0
power_save_controller : Y
probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
single_cmd : N




!!ALSA Device nodes
!!-----------------

crw-rw---- 1 root audio 116,  0 2008-08-04 09:52 /dev/snd/controlC0
crw-rw---- 1 root audio 116, 32 2008-08-04 09:52 /dev/snd/controlC1
crw-rw---- 1 root audio 116,  4 2008-08-04 09:52 /dev/snd/hwC0D0
crw-rw---- 1 root audio 116,  5 2008-08-04 09:52 /dev/snd/hwC0D1
crw-rw---- 1 root audio 116, 36 2008-08-04 09:52 /dev/snd/hwC1D0
crw-rw---- 1 root audio 116, 24 2008-08-04 09:52 /dev/snd/pcmC0D0c
crw-rw---- 1 root audio 116, 16 2008-08-04 13:35 /dev/snd/pcmC0D0p
crw-rw---- 1 root audio 116, 17 2008-08-04 09:52 /dev/snd/pcmC0D1p
crw-rw---- 1 root audio 116, 26 2008-08-04 09:52 /dev/snd/pcmC0D2c
crw-rw---- 1 root audio 116, 30 2008-08-04 09:52 /dev/snd/pcmC0D6c
crw-rw---- 1 root audio 116, 22 2008-08-04 09:52 /dev/snd/pcmC0D6p
crw-rw---- 1 root audio 116, 51 2008-08-04 12:57 /dev/snd/pcmC1D3p
crw-rw---- 1 root audio 116,  1 2008-08-04 09:52 /dev/snd/seq
crw-rw---- 1 root audio 116, 33 2008-08-04 09:52 /dev/snd/timer

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 26 [84%] [-7.50dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [-9.00dB] [on]
  Front Right: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [off]
  Front Right: Capture 0 [0%] [-16.50dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [on]
  Front Right: Capture 0 [0%] [-16.50dB] [on]
Simple mixer control 'Caller ID',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Off-hook',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

!!-------Mixer controls for card 1 [HDMI]

Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

```

```

# cat ~/.mplayer/config
# Write your default config options here!
ao=alsa:device=hw=1,3

```

```

# mplayer  /source/alsa/samples/Noise.wav
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /source/alsa/samples/Noise.wav.
Audio file file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 48000 Hz, 1 ch, s16le, 768.0 kbit/100.00% (ratio: 96000->96000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
[AO_ALSA] alsa-lib: pcm_hw.c:1099:(snd_pcm_hw_open) open /dev/snd/pcmC1D0p failed: No such file or directory
[AO_ALSA] Playback open error: No such file or directory
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video

```

Pls help, no sound through HDMI output , sound through HDMI outut have only with Windows Vista SP1 Ultimate.

---

### Post by dobrichkia on 2008-08-05
Mplayer no sound!
```

[AO_ALSA] alsa-lib: pcm_hw.c:1099:(snd_pcm_hw_open) open /dev/snd/pcmC1D0p failed: No such file or directory

```

But this test show - have noise sound :)
```

speaker-test -D plughw:1,3

```

What happend!
```

# ln -s /dev/snd/pcmC1D3p /dev/snd/pcmC1D0p

```

```

# mplayer  /source/alsa/samples/Noise.wav
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /source/alsa/samples/Noise.wav.
Audio file file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 48000 Hz, 1 ch, s16le, 768.0 kbit/100.00% (ratio: 96000->96000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   1.1 (01.0) of 1.0 (01.0)  1.0%

Exiting... (End of file)


```
Now sound have with mplayer too :) .

###################################################

```

# audio driver to use
# { auto  null  pulseaudio  alsa  oss  none  file }, default: 0

#change auto to alsa!
audio.driver:alsa

# device used for pulseaudio
# string, default:
#audio.pulseaudio_device:

# a/v sync method to use by OSS
# { auto  getodelay  getoptr  softsync  probebuffer }, default: 0
#audio.oss_sync_method:auto

# use A/52 dynamic range compression
# bool, default: 0
#audio.a52.dynamic_range:0

# downmix audio to 2 channel surround stereo
# bool, default: 0
#audio.a52.surround_downmix:0

# A/52 volume
# [0..200], default: 100
#audio.a52.level:100

# device used for mono output
# string, default: default

#change default to hw:1,3
audio.device.alsa_default_device:hw:1,3

# device used for stereo output
# string, default: plug:front:default

#change default to hw:1,3
audio.device.alsa_front_device:hw:1,3

```

Now sound have with xine too :) .

###################################################

edit file ~/.kde/share/config/kcmartsrc
```

[Arts]
AddOptions=
Arguments=\s-F 10 -S 4096 -a alsa -D hw:1,3 -s 60 -m artsmessage -c drkonqi -l 3 -f
AudioIO=alsa
AutoSuspend=true
Bits=0
DeviceName=hw:1,3
FullDuplex=false
Latency=250
NetworkTransparent=false
SamplingRate=0
StartRealtime=false
StartServer=true
SuspendTime=60

```

Now arts sound system work too with HDMI output :).

---

### Post by life_s_good on 2008-09-07
What did you change to make the sound play through the speakers?

---

### Post by terrax on 2008-09-13
> **dobrichkia said:**
> Hi, my laptop is Asus - M50Sa


Hey... Got that laptop too, and I got it all working. Just ask me.

The hdmi problem is easy solved. Just change the default sound device in gnome, under administrator -> sound to ati hdmi.

Then write:

```
> alsamixer -c1
```

Alsamixer will popup with you hdmi audio thingy. Just push 'm' to unmute the sound. Woila. Btw with newer ati gfx drivers, I have to unmute some times when I start with a new sound stream. That was not a problem with ati fglrx 8.3.

---

