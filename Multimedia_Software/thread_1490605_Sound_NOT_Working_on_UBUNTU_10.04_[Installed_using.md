---
title: "Sound NOT Working on UBUNTU 10.04 [Installed using Boot CD]"
date: 2010-05-22
forum: Multimedia Software
---

### Post by frozonecom on 2010-05-22
I download Ubuntu 10.04 the other day, it is my 1st time using it, and it is so good. :D

but my problem is that there is no sound in it. I did not edit any settings in it or other config files, i just did a partial upgrade in it because when i Opened Update Manager, it says that I should upgrade. 

The first thing I noticed was that the speaker icon doesnt have any **sound waves** in it. 

[ATTACH]157891[/ATTACH]

As you can see in there, the volumes are all normal but the _***speaker icon (on the bottom right)***_ doesnt seem to respond from the actual settings.

Here are also some pictures that might help you to help me solve my problem. :D

[ATTACH]157892[/ATTACH]

[ATTACH]157893[/ATTACH]

[ATTACH]157894[/ATTACH]

***Second, I noticed that before I can login,*** before I can select my user account at the boot-up process, some text shows up. It shows up something like this:

```
Alsa Intel 8x0 error_codec ready: codec not ready [007x00]
```**NOTE**: That is not the actual text, those are just some words that i can remember, but the words **ALSA**, **INTEL 8x0**,  **CODEC**  are  absolutely there, I am sure.

[COLOR=DarkOrange]_***The error is seen in a black screen, and the text color is white.***_[/COLOR]

_**HERE ARE SOME OUTPUT OF THE CODES [IN TERMINAL] THAT ARE OFTEN ASKED TO SOLVE SOUND PROBLEMS:**_

cat /proc/asound/version  :
```
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May 21 2010 for kernel 2.6.32-22-generic (SMP).

```cat /proc/asound/cards  :
```
--- no soundcards ---

```lsmod  :
```
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_intel8x0           25960  0 
snd_ac97_codec        101347  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            41611  0 
snd_mixer_oss          13461  1 snd_pcm_oss
fbcon                  35102  71 
snd_pcm                78086  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
tileblit                2031  1 fbcon
font                    7557  1 fbcon
snd_seq_dummy           1498  0 
bitblit                 4707  1 fbcon
snd_seq_oss            30866  0 
softcursor              1189  1 bitblit
snd_seq_midi            5101  0 
snd_rawmidi            19879  1 snd_seq_midi
vga16fb                11385  0 
vgastate                8961  1 vga16fb
pcmcia                 33024  0 
snd_seq_midi_event      5939  2 snd_seq_oss,snd_seq_midi
joydev                  8708  0 
snd_seq                51494  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
yenta_socket           20408  1 
radeon                674135  3 
rsrc_nonstatic         10015  1 yenta_socket
snd_timer              19106  2 snd_pcm,snd_seq
ttm                    49943  1 radeon
drm_kms_helper         29297  1 radeon
snd_seq_device          5990  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tifm_7xx1               3690  0 
irda                  186556  0 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
drm                   162471  5 radeon,ttm,drm_kms_helper
psmouse                63245  0 
tifm_core               6045  1 tifm_7xx1
snd                    62362  13 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5028  1 radeon
intel_agp              24177  1 
lp                      7028  0 
video                  17375  0 
crc_ccitt               1339  1 irda
ipw2200               135216  0 
libipw                 39896  1 ipw2200
lib80211                5046  2 ipw2200,libipw
serio_raw               3978  0 
agpgart                31724  3 ttm,drm,intel_agp
soundcore               6620  1 snd
snd_page_alloc          7140  2 snd_intel8x0,snd_pcm
output                  1871  1 video
parport                32635  2 ppdev,lp
shpchp                 28820  0 
led_class               2864  0 
ohci1394               26950  0 
b44                    25542  0 
ieee1394               81181  1 ohci1394
ssb                    37336  1 b44
mii                     4381  1 b44

```lspci  :
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller

```lspci | grep audio  :
```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

```aplay -l  :
```
aplay: device_list:223: no soundcards found...
```lspci -v  :
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, fast devsel, latency 0
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, fast devsel, latency 0

00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)
    Flags: bus master, 66MHz, fast devsel, latency 96
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d0100000-d01fffff
    Prefetchable memory behind bridge: d8000000-dfffffff
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 0, IRQ 6
    I/O ports at 1800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 0, IRQ 6
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 0, IRQ 6
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 0, IRQ 10
    Memory at d0000000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=06, sec-latency=64
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: d0200000-d05fffff
    Prefetchable memory behind bridge: 10000000-15ffffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 0, IRQ 6
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1860 [size=16]
    Memory at 16000000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: medium devsel, IRQ 10
    I/O ports at 1880 [size=32]
    Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: medium devsel, IRQ 10
    I/O ports at 1c00 [size=256]
    I/O ports at 18c0 [size=64]
    Memory at d0000c00 (32-bit, non-prefetchable) [size=512]
    Memory at d0000800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel modules: snd-intel8x0

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: medium devsel, IRQ 10
    I/O ports at 2400 [size=256]
    I/O ports at 2000 [size=128]
    Capabilities: <access denied>
    Kernel modules: snd-intel8x0m

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 6
    Memory at d8000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 3000 [size=256]
    Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at d0120000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeonfb, radeon

02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, fast devsel, latency 64, IRQ 6
    Memory at d0204000 (32-bit, non-prefetchable) [size=8K]
    [virtual] Expansion ROM at 14000000 [disabled] [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b44
    Kernel modules: b44

02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
    Subsystem: Intel Corporation Device 2701
    Flags: bus master, medium devsel, latency 64, IRQ 10
    Memory at d0208000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ipw2200
    Kernel modules: ipw2200

02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 168, IRQ 10
    Memory at d0209000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
    Memory window 0: 10000000-13fff000 (prefetchable)
    Memory window 1: 18000000-1bfff000
    I/O window 0: 00004000-000040ff
    I/O window 1: 00004400-000044ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 64, IRQ 10
    Memory at d020a000 (32-bit, non-prefetchable) [size=2K]
    Memory at d0200000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 64, IRQ 10
    Memory at d0206000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1

```uname -a  :
```
Linux Ubuntu 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

```head -n 1 /proc/asound/card*/codec#*  :
```
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

```

this is the content of /etc/modprobe.d/alsa-base.conf  :
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

```sudo alsaconf  :
```
[sudo] password for gio: 
sudo: alsaconf: command not found

```amixer  :
```
amixer: Mixer attach default error: No such file or directory

```alsamixer  :
```
cannot open mixer: No such file or directory

```_***FOR ME, I THINK THE PROBLEM IS WITH THE CODEC, AS STATED ABOVE:***_

```
***Second, I noticed that before I can login,*** before I can  select my user account at the boot-up process, some text shows up. It  shows up something like this:

[CODE]Alsa Intel 8x0 error_codec ready: codec not ready [007x00]
```[/CODE]_I REALLY NEED THE SOUND TO WORK SO PLEASE HELP ME. :D_

---

### Post by waltercool on 2010-05-22
> **frozonecom said:**
> I download Ubuntu 10.04 the other day, it is my 1st time using it, and it is so good. :D

but my problem is that there is no sound in it. I did not edit any settings in it or other config files, i just did a partial upgrade in it because when i Opened Update Manager, it says that I should upgrade. 

The first thing I noticed was that the speaker icon doesnt have any **sound waves** in it. 

[ATTACH]157891[/ATTACH]

As you can see in there, the volumes are all normal but the _***speaker icon (on the bottom right)***_ doesnt seem to respond from the actual settings.

Here are also some pictures that might help you to help me solve my problem. :D

[ATTACH]157892[/ATTACH]

[ATTACH]157893[/ATTACH]

[ATTACH]157894[/ATTACH]

***Second, I noticed that before I can login,*** before I can select my user account at the boot-up process, some text shows up. It shows up something like this:

```
Alsa Intel 8x0 error_codec ready: codec not ready [007x00]
```**NOTE**: That is not the actual text, those are just some words that i can remember, but the words **ALSA**, **INTEL 8x0**,  **CODEC**  are  absolutely there, I am sure.

[COLOR=DarkOrange]_***The error is seen in a black screen, and the text color is white.***_[/COLOR]

_**HERE ARE SOME OUTPUT OF THE CODES [IN TERMINAL] THAT ARE OFTEN ASKED TO SOLVE SOUND PROBLEMS:**_

cat /proc/asound/version  :
```
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May 21 2010 for kernel 2.6.32-22-generic (SMP).

```cat /proc/asound/cards  :
```
--- no soundcards ---

```lsmod  :
```
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_intel8x0           25960  0 
snd_ac97_codec        101347  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            41611  0 
snd_mixer_oss          13461  1 snd_pcm_oss
fbcon                  35102  71 
snd_pcm                78086  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
tileblit                2031  1 fbcon
font                    7557  1 fbcon
snd_seq_dummy           1498  0 
bitblit                 4707  1 fbcon
snd_seq_oss            30866  0 
softcursor              1189  1 bitblit
snd_seq_midi            5101  0 
snd_rawmidi            19879  1 snd_seq_midi
vga16fb                11385  0 
vgastate                8961  1 vga16fb
pcmcia                 33024  0 
snd_seq_midi_event      5939  2 snd_seq_oss,snd_seq_midi
joydev                  8708  0 
snd_seq                51494  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
yenta_socket           20408  1 
radeon                674135  3 
rsrc_nonstatic         10015  1 yenta_socket
snd_timer              19106  2 snd_pcm,snd_seq
ttm                    49943  1 radeon
drm_kms_helper         29297  1 radeon
snd_seq_device          5990  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tifm_7xx1               3690  0 
irda                  186556  0 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
drm                   162471  5 radeon,ttm,drm_kms_helper
psmouse                63245  0 
tifm_core               6045  1 tifm_7xx1
snd                    62362  13 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5028  1 radeon
intel_agp              24177  1 
lp                      7028  0 
video                  17375  0 
crc_ccitt               1339  1 irda
ipw2200               135216  0 
libipw                 39896  1 ipw2200
lib80211                5046  2 ipw2200,libipw
serio_raw               3978  0 
agpgart                31724  3 ttm,drm,intel_agp
soundcore               6620  1 snd
snd_page_alloc          7140  2 snd_intel8x0,snd_pcm
output                  1871  1 video
parport                32635  2 ppdev,lp
shpchp                 28820  0 
led_class               2864  0 
ohci1394               26950  0 
b44                    25542  0 
ieee1394               81181  1 ohci1394
ssb                    37336  1 b44
mii                     4381  1 b44

```lspci  :
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller

```lspci | grep audio  :
```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

```aplay -l  :
```
aplay: device_list:223: no soundcards found...
```lspci -v  :
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, fast devsel, latency 0
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, fast devsel, latency 0

00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)
    Flags: bus master, 66MHz, fast devsel, latency 96
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d0100000-d01fffff
    Prefetchable memory behind bridge: d8000000-dfffffff
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 0, IRQ 6
    I/O ports at 1800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 0, IRQ 6
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 0, IRQ 6
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 0, IRQ 10
    Memory at d0000000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=06, sec-latency=64
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: d0200000-d05fffff
    Prefetchable memory behind bridge: 10000000-15ffffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 0, IRQ 6
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1860 [size=16]
    Memory at 16000000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: medium devsel, IRQ 10
    I/O ports at 1880 [size=32]
    Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: medium devsel, IRQ 10
    I/O ports at 1c00 [size=256]
    I/O ports at 18c0 [size=64]
    Memory at d0000c00 (32-bit, non-prefetchable) [size=512]
    Memory at d0000800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel modules: snd-intel8x0

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: medium devsel, IRQ 10
    I/O ports at 2400 [size=256]
    I/O ports at 2000 [size=128]
    Capabilities: <access denied>
    Kernel modules: snd-intel8x0m

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 6
    Memory at d8000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 3000 [size=256]
    Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at d0120000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeonfb, radeon

02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, fast devsel, latency 64, IRQ 6
    Memory at d0204000 (32-bit, non-prefetchable) [size=8K]
    [virtual] Expansion ROM at 14000000 [disabled] [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b44
    Kernel modules: b44

02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
    Subsystem: Intel Corporation Device 2701
    Flags: bus master, medium devsel, latency 64, IRQ 10
    Memory at d0208000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ipw2200
    Kernel modules: ipw2200

02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 168, IRQ 10
    Memory at d0209000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
    Memory window 0: 10000000-13fff000 (prefetchable)
    Memory window 1: 18000000-1bfff000
    I/O window 0: 00004000-000040ff
    I/O window 1: 00004400-000044ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 64, IRQ 10
    Memory at d020a000 (32-bit, non-prefetchable) [size=2K]
    Memory at d0200000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 64, IRQ 10
    Memory at d0206000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1

```uname -a  :
```
Linux Ubuntu 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

```head -n 1 /proc/asound/card*/codec#*  :
```
[head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory
/CODE]

this is the content of /etc/modprobe.d/alsa-base.conf  :
[CODE]# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

```sudo alsaconf  :
```
[sudo] password for gio: 
sudo: alsaconf: command not found

```amixer  :
```
amixer: Mixer attach default error: No such file or directory

```alsamixer  :
```
cannot open mixer: No such file or directory

```_***FOR ME, I THINK THE PROBLEM IS WITH THE CODEC, AS STATED ABOVE:***_

```
***Second, I noticed that before I can login,*** before I can  select my user account at the boot-up process, some text shows up. It  shows up something like this:

[CODE]Alsa Intel 8x0 error_codec ready: codec not ready [007x00]
```[/CODE]_I REALLY NEED THE SOUND TO WORK SO PLEASE HELP ME. :D_

Please, can you upload your /var/log/dmesg ?

---

### Post by frozonecom on 2010-05-23
/var/log/dmesg

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-22-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 (Ubuntu 2.6.32-22.33-generic 2.6.32.11+drm33.2)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fee0000 (usable)
[    0.000000]  BIOS-e820: 000000000fee0000 - 000000000feec000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000feec000 - 000000000ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000000ff00000 - 0000000010000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xfee0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FF0000000 write-back
[    0.000000]   1 base 00FF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000000fee0000 (usable)
[    0.000000]  modified: 000000000fee0000 - 000000000feec000 (ACPI data)
[    0.000000]  modified: 000000000feec000 - 000000000ff00000 (ACPI NVS)
[    0.000000]  modified: 000000000ff00000 - 0000000010000000 (reserved)
[    0.000000]  modified: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  modified: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000fffffc00 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000000fee0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 000fc00000 page 2M
[    0.000000]  000fc00000 - 000fee0000 page 4k
[    0.000000] kernel direct mapping tables up to fee0000 @ 7000-c000
[    0.000000] RAMDISK: 0b7d1000 - 0bf67ec8
[    0.000000] ACPI: RSDP 000f62c0 00014 (v00 ACER  )
[    0.000000] ACPI: RSDT 0fee6205 00030 (v01 ACER   Kestrel  20021012  LTP 00000000)
[    0.000000] ACPI: FACP 0feebf2c 00074 (v01 ACER   Kestrel  20021012 PTL  00000050)
[    0.000000] ACPI: DSDT 0fee6235 05CF7 (v01 ACER   Kestrel  20021012 MSFT 0100000E)
[    0.000000] ACPI: FACS 0fefcfc0 00040
[    0.000000] ACPI: HPET 0feebfa0 00038 (v01 ACER   Kestrel  20021012 PTL  00000000)
[    0.000000] ACPI: BOOT 0feebfd8 00028 (v01 ACER   Kestrel  20021012  LTP 00000001)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 254MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0fee0000
[    0.000000]   low ram: 0 - 0fee0000
[    0.000000]   node 0 low ram: 00000000 - 0fee0000
[    0.000000]   node 0 bootmap 00008000 - 00009fdc
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000fee0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [000b7d1000 - 000bf67ec8]          RAMDISK ==> [000b7d1000 - 000bf67ec8]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [00008da000 - 00008dd174]              BRK ==> [00008da000 - 00008dd174]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000a000]          BOOTMAP ==> [0000008000 - 000000a000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000fee0
[    0.000000]   HighMem  0x0000fee0 -> 0x0000fee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0000fee0
[    0.000000] On node 0 totalpages: 65147
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 478 pages used for memmap
[    0.000000]   Normal zone: 60674 pages, LIFO batch:15
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0x0 is invalid
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 10000000:eec10000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1400000 s36024 r0 d21320 u4194304
[    0.000000] pcpu-alloc: s36024 r0 d21320 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64637
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=0eb5e1e5-2aaf-4e9c-b6ea-b4e05c5e9afd ro quiet splash
[    0.000000] PID hash table entries: 1024 (order: 0, 4096 bytes)
[    0.000000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 1304960 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 240784k/260992k available (4673k kernel code, 19456k reserved, 2121k data, 656k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xd06e0000 - 0xff7fe000   ( 753 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xcfee0000   ( 254 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590653 - 0xc07a2e48   (2121 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590653   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1498.925 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 2997.85 BogoMIPS (lpj=5995700)
[    0.004030] Security Framework initialized
[    0.004063] AppArmor: AppArmor initialized
[    0.004072] Mount-cache hash table entries: 512
[    0.004231] Initializing cgroup subsys ns
[    0.008006] Initializing cgroup subsys cpuacct
[    0.008012] Initializing cgroup subsys memory
[    0.008024] Initializing cgroup subsys devices
[    0.008028] Initializing cgroup subsys freezer
[    0.008031] Initializing cgroup subsys net_cls
[    0.008061] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008065] CPU: L2 cache: 2048K
[    0.008071] mce: CPU supports 5 MCE banks
[    0.008089] Performance Events: 
[    0.008092] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.008095] no hardware sampling interrupt available.
[    0.008098] p6 PMU driver.
[    0.008124] ... version:                0
[    0.008127] ... bit width:              32
[    0.008129] ... generic registers:      2
[    0.008132] ... value mask:             00000000ffffffff
[    0.008135] ... max period:             000000007fffffff
[    0.008138] ... fixed-purpose events:   0
[    0.008140] ... event mask:             0000000000000003
[    0.008146] Checking 'hlt' instruction... OK.
[    0.024997] SMP alternatives: switching to UP code
[    0.033766] Freeing SMP alternatives: 19k freed
[    0.033777] ACPI: Core revision 20090903
[    0.044162] ACPI: setting ELCR to 0200 (from 0440)
[    0.048009] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.048014] ftrace: allocating 21771 entries in 43 pages
[    0.052079] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.052084] weird, boot CPU (#0) not listed by the BIOS.
[    0.052088] SMP motherboard not detected.
[    0.052091] Local APIC not detected. Using dummy APIC emulation.
[    0.052094] SMP disabled
[    0.052239] Brought up 1 CPUs
[    0.052242] Total of 1 processors activated (2997.85 BogoMIPS).
[    0.053529] CPU0 attaching NULL sched-domain.
[    0.053709] devtmpfs: initialized
[    0.054159] regulator: core version 0.5
[    0.054181] Time:  4:19:01  Date: 05/23/10
[    0.054237] NET: Registered protocol family 16
[    0.054385] EISA bus registered
[    0.054396] ACPI: bus type pci registered
[    0.056488] PCI: PCI BIOS revision 2.10 entry at 0xfd782, last bus=2
[    0.056491] PCI: Using configuration type 1 for base access
[    0.057686] bio: create slab <bio-0> at 0
[    0.058527] ACPI: EC: Look up EC in DSDT
[    0.064600] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.192058] ACPI: Interpreter enabled
[    0.192066] ACPI: (supports S0 S3 S4 S5)
[    0.192089] ACPI: Using PIC for interrupt routing
[    0.197476] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    0.197545] ACPI: Power Resource [PFN0] (off)
[    0.197587] ACPI: Power Resource [PFN1] (off)
[    0.198248] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.198983] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.199034] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xe0000000-0xefffffff]
[    0.199206] pci 0000:00:1d.0: reg 20 io port: [0x1800-0x181f]
[    0.199256] pci 0000:00:1d.1: reg 20 io port: [0x1820-0x183f]
[    0.199308] pci 0000:00:1d.2: reg 20 io port: [0x1840-0x185f]
[    0.199366] pci 0000:00:1d.7: reg 10 32bit mmio: [0xd0000000-0xd00003ff]
[    0.199421] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.199427] pci 0000:00:1d.7: PME# disabled
[    0.199510] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.199515] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.199538] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.199546] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.199553] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.199561] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.199568] pci 0000:00:1f.1: reg 20 io port: [0x1860-0x186f]
[    0.199576] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.199625] pci 0000:00:1f.3: reg 20 io port: [0x1880-0x189f]
[    0.199666] pci 0000:00:1f.5: reg 10 io port: [0x1c00-0x1cff]
[    0.199674] pci 0000:00:1f.5: reg 14 io port: [0x18c0-0x18ff]
[    0.199681] pci 0000:00:1f.5: reg 18 32bit mmio: [0xd0000c00-0xd0000dff]
[    0.199689] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xd0000800-0xd00008ff]
[    0.199717] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.199722] pci 0000:00:1f.5: PME# disabled
[    0.199750] pci 0000:00:1f.6: reg 10 io port: [0x2400-0x24ff]
[    0.199757] pci 0000:00:1f.6: reg 14 io port: [0x2000-0x207f]
[    0.199792] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.199797] pci 0000:00:1f.6: PME# disabled
[    0.199834] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xd8000000-0xdfffffff]
[    0.199841] pci 0000:01:00.0: reg 14 io port: [0x3000-0x30ff]
[    0.199848] pci 0000:01:00.0: reg 18 32bit mmio: [0xd0100000-0xd010ffff]
[    0.199864] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.199883] pci 0000:01:00.0: supports D1 D2
[    0.199916] pci 0000:00:01.0: bridge io port: [0x3000-0x3fff]
[    0.199921] pci 0000:00:01.0: bridge 32bit mmio: [0xd0100000-0xd01fffff]
[    0.199926] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd8000000-0xdfffffff]
[    0.199959] pci 0000:02:02.0: reg 10 32bit mmio: [0xd0204000-0xd0205fff]
[    0.199985] pci 0000:02:02.0: reg 30 32bit mmio pref: [0x000000-0x003fff]
[    0.200011] pci 0000:02:02.0: supports D1 D2
[    0.200014] pci 0000:02:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.200019] pci 0000:02:02.0: PME# disabled
[    0.200051] pci 0000:02:04.0: reg 10 32bit mmio: [0xd0208000-0xd0208fff]
[    0.200094] pci 0000:02:04.0: PME# supported from D0 D3hot D3cold
[    0.200098] pci 0000:02:04.0: PME# disabled
[    0.200131] pci 0000:02:06.0: reg 10 32bit mmio: [0xd0209000-0xd0209fff]
[    0.200149] pci 0000:02:06.0: supports D1 D2
[    0.200152] pci 0000:02:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.200157] pci 0000:02:06.0: PME# disabled
[    0.200189] pci 0000:02:06.2: reg 10 32bit mmio: [0xd020a000-0xd020a7ff]
[    0.200197] pci 0000:02:06.2: reg 14 32bit mmio: [0xd0200000-0xd0203fff]
[    0.200236] pci 0000:02:06.2: supports D1 D2
[    0.200239] pci 0000:02:06.2: PME# supported from D0 D1 D2 D3hot
[    0.200244] pci 0000:02:06.2: PME# disabled
[    0.200274] pci 0000:02:06.3: reg 10 32bit mmio: [0xd0206000-0xd0207fff]
[    0.200315] pci 0000:02:06.3: supports D1 D2
[    0.200318] pci 0000:02:06.3: PME# supported from D0 D1 D2 D3hot
[    0.200323] pci 0000:02:06.3: PME# disabled
[    0.200359] pci 0000:00:1e.0: transparent bridge
[    0.200364] pci 0000:00:1e.0: bridge io port: [0x4000-0x4fff]
[    0.200370] pci 0000:00:1e.0: bridge 32bit mmio: [0xd0200000-0xd05fffff]
[    0.200398] pci_bus 0000:00: on NUMA node 0
[    0.200403] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.200577] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.200604] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.203666] ACPI: PCI Interrupt Link [LNKA] (IRQs *6)
[    0.203787] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[    0.203905] ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
[    0.204034] ACPI: PCI Interrupt Link [LNKD] (IRQs *6)
[    0.204152] ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
[    0.204269] ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled.
[    0.204388] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *0, disabled.
[    0.204507] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[    0.204627] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.204633] vgaarb: loaded
[    0.204774] SCSI subsystem initialized
[    0.204823] libata version 3.00 loaded.
[    0.204907] usbcore: registered new interface driver usbfs
[    0.204930] usbcore: registered new interface driver hub
[    0.204964] usbcore: registered new device driver usb
[    0.205115] ACPI: WMI: Mapper loaded
[    0.205117] PCI: Using ACPI for IRQ routing
[    0.205279] NetLabel: Initializing
[    0.205282] NetLabel:  domain hash size = 128
[    0.205284] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.205303] NetLabel:  unlabeled traffic allowed by default
[    0.205338] Switching to clocksource tsc
[    0.207812] AppArmor: AppArmor Filesystem Enabled
[    0.207825] pnp: PnP ACPI init
[    0.207840] ACPI: bus type pnp registered
[    0.210001] pnp: PnP ACPI: found 9 devices
[    0.210004] ACPI: ACPI bus type pnp unregistered
[    0.210008] PnPBIOS: Disabled by ACPI PNP
[    0.210022] system 00:04: ioport range 0x164e-0x164f has been reserved
[    0.210028] system 00:04: ioport range 0x600-0x60f has been reserved
[    0.210032] system 00:04: ioport range 0x700-0x70f has been reserved
[    0.210036] system 00:04: ioport range 0x800-0x80f has been reserved
[    0.210040] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.210044] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    0.210048] system 00:04: ioport range 0x1c0-0x1cf has been reserved
[    0.210053] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    0.210057] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.210061] system 00:04: ioport range 0x610-0x61f has been reserved
[    0.210066] system 00:04: iomem range 0xfec10000-0xfec1ffff has been reserved
[    0.210071] system 00:04: iomem range 0xff800000-0xffbfffff has been reserved
[    0.210075] system 00:04: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.210080] system 00:04: iomem range 0x0-0x9ffff could not be reserved
[    0.210084] system 00:04: iomem range 0xe0000-0xfffff could not be reserved
[    0.210089] system 00:04: iomem range 0xdf800-0xdffff could not be reserved
[    0.244799] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.244804] pci 0000:00:01.0:   IO window: 0x3000-0x3fff
[    0.244809] pci 0000:00:01.0:   MEM window: 0xd0100000-0xd01fffff
[    0.244814] pci 0000:00:01.0:   PREFETCH window: 0xd8000000-0xdfffffff
[    0.244823] pci 0000:02:06.0: CardBus bridge, secondary bus 0000:03
[    0.244827] pci 0000:02:06.0:   IO window: 0x004000-0x0040ff
[    0.244832] pci 0000:02:06.0:   IO window: 0x004400-0x0044ff
[    0.244837] pci 0000:02:06.0:   PREFETCH window: 0x10000000-0x13ffffff
[    0.244843] pci 0000:02:06.0:   MEM window: 0x18000000-0x1bffffff
[    0.244848] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.244852] pci 0000:00:1e.0:   IO window: 0x4000-0x4fff
[    0.244859] pci 0000:00:1e.0:   MEM window: 0xd0200000-0xd05fffff
[    0.244864] pci 0000:00:1e.0:   PREFETCH window: 0x10000000-0x15ffffff
[    0.244882] pci 0000:00:1e.0: setting latency timer to 64
[    0.244892] pci 0000:02:06.0: enabling device (0104 -> 0107)
[    0.245076] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[    0.245079] PCI: setting IRQ 10 as level-triggered
[    0.245085] pci 0000:02:06.0: PCI INT A -> Link[LNKE] -> GSI 10 (level, low) -> IRQ 10
[    0.245093] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.245097] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.245101] pci_bus 0000:01: resource 0 io:  [0x3000-0x3fff]
[    0.245104] pci_bus 0000:01: resource 1 mem: [0xd0100000-0xd01fffff]
[    0.245108] pci_bus 0000:01: resource 2 pref mem [0xd8000000-0xdfffffff]
[    0.245112] pci_bus 0000:02: resource 0 io:  [0x4000-0x4fff]
[    0.245116] pci_bus 0000:02: resource 1 mem: [0xd0200000-0xd05fffff]
[    0.245119] pci_bus 0000:02: resource 2 pref mem [0x10000000-0x15ffffff]
[    0.245123] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.245127] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.245130] pci_bus 0000:03: resource 0 io:  [0x4000-0x40ff]
[    0.245134] pci_bus 0000:03: resource 1 io:  [0x4400-0x44ff]
[    0.245138] pci_bus 0000:03: resource 2 pref mem [0x10000000-0x13ffffff]
[    0.245141] pci_bus 0000:03: resource 3 mem: [0x18000000-0x1bffffff]
[    0.245177] NET: Registered protocol family 2
[    0.245282] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.245608] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.245667] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.245726] TCP: Hash tables configured (established 8192 bind 8192)
[    0.245730] TCP reno registered
[    0.245806] NET: Registered protocol family 1
[    0.245885] pci 0000:01:00.0: Boot video device
[    0.245945] Simple Boot Flag at 0x37 set to 0x1
[    0.246019] cpufreq-nforce2: No nForce2 chipset.
[    0.246044] Scanning for low memory corruption every 60 seconds
[    0.246178] audit: initializing netlink socket (disabled)
[    0.246194] type=2000 audit(1274588341.242:1): initialized
[    0.260035] Trying to unpack rootfs image as initramfs...
[    0.274903] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.282691] VFS: Disk quotas dquot_6.5.2
[    0.282777] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.283575] fuse init (API version 7.13)
[    0.283692] msgmni has been set to 470
[    0.283955] alg: No test for stdrng (krng)
[    0.284031] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.284035] io scheduler noop registered
[    0.284038] io scheduler anticipatory registered
[    0.284040] io scheduler deadline registered
[    0.284092] io scheduler cfq registered (default)
[    0.284249] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.284280] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.284410] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.298858] ACPI: Lid Switch [LID]
[    0.298949] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.298954] ACPI: Sleep Button [SLPB]
[    0.299016] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.299020] ACPI: Power Button [PWRF]
[    0.299207] fan PNP0C0B:00: registered as cooling_device0
[    0.299219] ACPI: Fan [FAN0] (off)
[    0.299347] fan PNP0C0B:01: registered as cooling_device1
[    0.299354] ACPI: Fan [FAN1] (off)
[    0.299529] Marking TSC unstable due to TSC halts in idle
[    0.299573] processor LNXCPU:00: registered as cooling_device2
[    0.306742] Switching to clocksource acpi_pm
[    0.336504] thermal LNXTHERM:01: registered as thermal_zone0
[    0.336521] ACPI: Thermal Zone [THRM] (42 C)
[    0.336607] ACPI: SBS HC: EC = 0xcf890420, offset = 0x18, query_bit = 0x20
[    0.464450] ACPI: Smart Battery System [SBS0]: AC Adapter [AC0] (on-line)
[    0.557518] Freeing initrd memory: 7771k freed
[    0.884151] ACPI: Smart Battery System [SBS0]: Battery Slot [BAT0] (battery absent)
[    1.168081] ACPI: Smart Battery System [SBS0]: Battery Slot [BAT1] (battery absent)
[    1.170032] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.170178] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[    1.170808] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    1.170814] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    1.170823] serial 0000:00:1f.6: PCI INT B disabled
[    1.172172] brd: module loaded
[    1.172804] loop: module loaded
[    1.172918] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.173061] ata_piix 0000:00:1f.1: version 2.13
[    1.173086] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
[    1.173093] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    1.173303] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 6
[    1.173306] PCI: setting IRQ 6 as level-triggered
[    1.173312] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 6 (level, low) -> IRQ 6
[    1.173366] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.173480] scsi0 : ata_piix
[    1.173598] isapnp: Scanning for PnP cards...
[    1.179114] scsi1 : ata_piix
[    1.180386] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
[    1.180390] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
[    1.180872] Fixed MDIO Bus: probed
[    1.180920] PPP generic driver version 2.4.2
[    1.180981] tun: Universal TUN/TAP device driver, 1.6
[    1.180984] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.181090] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.181300] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    1.181306] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[    1.181326] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.181331] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.181378] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.181416] ehci_hcd 0000:00:1d.7: debug port 1
[    1.185303] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.185574] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xd0000000
[    1.276562] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.276685] usb usb1: configuration #1 chosen from 1 choice
[    1.276724] hub 1-0:1.0: USB hub found
[    1.276735] hub 1-0:1.0: 6 ports detected
[    1.276813] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.276832] uhci_hcd: USB Universal Host Controller Interface driver
[    1.277056] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 6
[    1.277061] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 6 (level, low) -> IRQ 6
[    1.277068] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.277072] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.277114] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.277137] uhci_hcd 0000:00:1d.0: irq 6, io base 0x00001800
[    1.277255] usb usb2: configuration #1 chosen from 1 choice
[    1.277289] hub 2-0:1.0: USB hub found
[    1.277299] hub 2-0:1.0: 2 ports detected
[    1.277529] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
[    1.277534] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 6 (level, low) -> IRQ 6
[    1.277541] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.277545] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.277585] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.277606] uhci_hcd 0000:00:1d.1: irq 6, io base 0x00001820
[    1.277719] usb usb3: configuration #1 chosen from 1 choice
[    1.277753] hub 3-0:1.0: USB hub found
[    1.277761] hub 3-0:1.0: 2 ports detected
[    1.277810] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 6 (level, low) -> IRQ 6
[    1.277817] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.277821] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.277864] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.277885] uhci_hcd 0000:00:1d.2: irq 6, io base 0x00001840
[    1.278004] usb usb4: configuration #1 chosen from 1 choice
[    1.278038] hub 4-0:1.0: USB hub found
[    1.278047] hub 4-0:1.0: 2 ports detected
[    1.278169] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOU2] at 0x60,0x64 irq 1,12
[    1.282381] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.283351] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.283359] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.283392] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.283420] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.283448] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.283585] mice: PS/2 mouse device common for all mice
[    1.283788] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.283806] rtc0: alarms up to one month, y3k, 242 bytes nvram
[    1.283948] device-mapper: uevent: version 1.0.3
[    1.284108] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.284177] device-mapper: multipath: version 1.1.0 loaded
[    1.284181] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.284327] EISA: Probing bus 0 at eisa.0
[    1.284334] Cannot allocate resource for EISA slot 1
[    1.284338] Cannot allocate resource for EISA slot 2
[    1.284341] Cannot allocate resource for EISA slot 3
[    1.284344] Cannot allocate resource for EISA slot 4
[    1.284362] EISA: Detected 0 cards.
[    1.284469] cpuidle: using governor ladder
[    1.284546] cpuidle: using governor menu
[    1.285092] TCP cubic registered
[    1.285303] NET: Registered protocol family 10
[    1.285871] lo: Disabled Privacy Extensions
[    1.286264] NET: Registered protocol family 17
[    1.286711] Using IPI No-Shortcut mode
[    1.286792] PM: Resume from disk failed.
[    1.286806] registered taskstats version 1
[    1.287031]   Magic number: 10:414:313
[    1.287109] rtc_cmos 00:01: setting system clock to 2010-05-23 04:19:03 UTC (1274588343)
[    1.287113] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.287115] EDD information not available.
[    1.436770] hub 2-0:1.0: over-current change on port 1
[    1.437308] ata2.00: ATAPI: Slimtype DVDRW SOSW-852S, PRS9, max UDMA/33
[    1.437494] ata1.00: ATA-6: HTS541060G9AT00, MB3VA60A, max UDMA/100
[    1.437498] ata1.00: 117210240 sectors, multi 16: LBA48 
[    1.487439] ata2.00: configured for UDMA/33
[    1.587125] isapnp: No Plug & Play device found
[    1.587169] ata1.00: configured for UDMA/100
[    1.587178] hub 2-0:1.0: over-current change on port 2
[    1.587259] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.589668] scsi 0:0:0:0: Direct-Access     ATA      HTS541060G9AT00  MB3V PQ: 0 ANSI: 5
[    1.589805] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.589983] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.590035] sd 0:0:0:0: [sda] Write Protect is off
[    1.590039] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.590066] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.590331]  sda:
[    1.590462] scsi 1:0:0:0: CD-ROM            Slimtype DVDRW SOSW-852S  PRS9 PQ: 0 ANSI: 5
[    1.593472] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.593476] Uniform CD-ROM driver Revision: 3.20
[    1.593568] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.593614] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.616504]  sda1 sda2 < sda5 >
[    1.645747] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.645762] Freeing unused kernel memory: 656k freed
[    1.646173] Write protecting the kernel text: 4676k
[    1.646213] Write protecting the kernel read-only data: 1840k
[    1.666341] udev: starting version 151
[    1.918883] ohci1394 0000:02:06.2: PCI INT A -> Link[LNKE] -> GSI 10 (level, low) -> IRQ 10
[    1.980062] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[d020a000-d020a7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.980485] b44 0000:02:02.0: PCI INT A -> Link[LNKD] -> GSI 6 (level, low) -> IRQ 6
[    2.040132] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[    2.040305] b44.c:v2.0
[    2.060774] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:c0:9f:48:15:72
[    2.192051] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.252166] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f00001e8486]
[   10.205593] Adding 728056k swap on /dev/sda5.  Priority:-1 extents:1 across:728056k 
[   10.436478] udev: starting version 151
[   11.300656] type=1505 audit(1274588353.512:2):  operation="profile_load" pid=444 name="/sbin/dhclient3"
[   11.301356] type=1505 audit(1274588353.512:3):  operation="profile_load" pid=444 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.301734] type=1505 audit(1274588353.512:4):  operation="profile_load" pid=444 name="/usr/lib/connman/scripts/dhclient-script"
[   11.480478] acer-wmi: Acer Laptop ACPI-WMI Extras
[   11.480496] acer-wmi: No or unsupported WMI interface, unable to load
[   11.543035] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.569557] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input5
[   11.569696] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   11.613769] intel_rng: FWH not detected
[   11.706533] lib80211: common routines for IEEE802.11 drivers
[   11.706538] lib80211_crypt: registered algorithm 'NULL'
[   11.732528] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   11.732532] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   11.882348] irda_init()
[   11.882365] NET: Registered protocol family 23
[   11.910057] Linux agpgart interface v0.103
[   11.940618] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   11.940674] nsc-ircc, chip->init
[   11.940682] nsc-ircc, Found chip at base=0x164e
[   11.940704] nsc-ircc, driver loaded (Dag Brattli)
[   11.941186] nsc_ircc_open(), can't get iobase of 0x2f8
[   11.941211] nsc-ircc, Found chip at base=0x164e
[   11.941233] nsc-ircc, driver loaded (Dag Brattli)
[   11.941236] nsc_ircc_open(), can't get iobase of 0x2f8
[   11.941957] nsc-ircc 00:08: disabled
[   11.954208] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[   11.978897] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   12.036884] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   12.036889] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   12.036962] ipw2200 0000:02:04.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   12.037025] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   12.037069] ipw2200 0000:02:04.0: firmware: requesting ipw2200-bss.fw
[   12.158161] [drm] Initialized drm 1.1.0 20060810
[   12.178067] lp: driver loaded but no devices found
[   12.368024] ipw2200: Radio Frequency Kill Switch is On:
[   12.368028] Kill switch must be turned off for wireless networking to work.
[   12.370817] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   12.425376] tifm_7xx1 0000:02:06.3: PCI INT A -> Link[LNKE] -> GSI 10 (level, low) -> IRQ 10
[   12.544961] yenta_cardbus 0000:02:06.0: CardBus bridge found [1025:0064]
[   12.544977] yenta_cardbus 0000:02:06.0: Enabling burst memory read transactions
[   12.544982] yenta_cardbus 0000:02:06.0: Using CSCINT to route CSC interrupts to PCI
[   12.544985] yenta_cardbus 0000:02:06.0: Routing CardBus interrupts to PCI
[   12.544990] yenta_cardbus 0000:02:06.0: TI: mfunc 0x01a21b22, devctl 0x64
[   12.776550] yenta_cardbus 0000:02:06.0: ISA IRQ mask 0x08b8, PCI irq 10
[   12.776555] yenta_cardbus 0000:02:06.0: Socket status: 30000006
[   12.776560] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   12.776570] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[   12.776575] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x4fff: clean.
[   12.776844] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd05fffff
[   12.776848] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0x10000000 - 0x15ffffff
[   12.806658] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[   12.849347] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
[   13.192632] [drm] radeon defaulting to kernel modesetting.
[   13.192637] [drm] radeon kernel modesetting enabled.
[   13.192705] radeon 0000:01:00.0: power state changed by ACPI to D0
[   13.192718] radeon 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 6 (level, low) -> IRQ 6
[   13.213224] [drm] radeon: Initializing kernel modesetting.
[   13.217735] [drm] register mmio base: 0xD0100000
[   13.217739] [drm] register mmio size: 65536
[   13.218902] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   13.218919] [drm] Generation 2 PCI interface, using max accessible memory
[   13.218928] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   13.218946] agpgart-intel 0000:00:00.0: putting AGP V2 device into 1x mode
[   13.218979] radeon 0000:01:00.0: putting AGP V2 device into 1x mode
[   13.219003] [drm] radeon: VRAM 64M
[   13.219005] [drm] radeon: VRAM from 0x00000000 to 0x03FFFFFF
[   13.219007] [drm] radeon: GTT 256M
[   13.219010] [drm] radeon: GTT from 0xE0000000 to 0xEFFFFFFF
[   13.219032] [drm] radeon: irq initialized.
[   13.221771] [drm] Detected VRAM RAM=64M, BAR=128M
[   13.221775] [drm] RAM width 128bits DDR
[   13.224327] [TTM] Zone  kernel: Available graphics memory: 124788 kiB.
[   13.224345] [drm] radeon: 64M of VRAM memory ready
[   13.224348] [drm] radeon: 256M of GTT memory ready.
[   13.224573] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   13.224586] [drm] radeon: cp idle (0x10000C03)
[   13.224658] [drm] Loading R300 Microcode
[   13.224879] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   13.378149] [drm] radeon: ring at 0x00000000E0000000
[   13.378172] [drm] ring test succeeded in 1 usecs
[   13.382423] [drm] radeon: ib pool ready.
[   13.382506] [drm] ib test succeeded in 0 usecs
[   13.383250] [drm] Panel ID String: QDS                     
[   13.383253] [drm] Panel Size 1280x800
[   13.383447] [drm] Default TV standard: NTSC
[   13.383449] [drm] 27.000000000 MHz TV ref clk
[   13.383453] [drm] Default TV standard: NTSC
[   13.383455] [drm] 27.000000000 MHz TV ref clk
[   13.384226] [drm] Radeon Display Connectors
[   13.384229] [drm] Connector 0:
[   13.384231] [drm]   VGA
[   13.384234] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   13.384236] [drm]   Encoders:
[   13.384238] [drm]     CRT1: INTERNAL_DAC1
[   13.384240] [drm] Connector 1:
[   13.384242] [drm]   LVDS
[   13.384244] [drm]   Encoders:
[   13.384245] [drm]     LCD1: INTERNAL_LVDS
[   13.384247] [drm] Connector 2:
[   13.384249] [drm]   S-video
[   13.384251] [drm]   Encoders:
[   13.384253] [drm]     TV1: INTERNAL_DAC2
[   13.432080] [drm] fb mappable at 0xD8040000
[   13.432083] [drm] vram apper at 0xD8000000
[   13.432085] [drm] size 4096000
[   13.432087] [drm] fb depth is 24
[   13.432088] [drm]    pitch is 5120
[   13.432347] fb0: radeondrmfb frame buffer device
[   13.432349] registered panic notifier
[   13.432355] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   13.469519] vga16fb: initializing
[   13.469524] vga16fb: mapped to 0xc00a0000
[   13.469528] vga16fb: not registering due to another framebuffer present
[   13.917763] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   13.919129] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   13.920195] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   13.920702] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   13.921371] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   14.093667] Console: switching to colour frame buffer device 160x50
[   15.440696] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   15.440724] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   16.452031] ALSA intel8x0.c:2435: codec_ready: codec is not ready [0x700000]
[   16.452243] Intel ICH 0000:00:1f.5: PCI INT B disabled
[   16.452262] Intel ICH: probe of 0000:00:1f.5 failed with error -5
[   17.387089] type=1505 audit(1274588359.596:5):  operation="profile_load" pid=680 name="/usr/share/gdm/guest-session/Xsession"
[   17.390607] type=1505 audit(1274588359.600:6):  operation="profile_replace" pid=682 name="/sbin/dhclient3"
[   17.391313] type=1505 audit(1274588359.600:7):  operation="profile_replace" pid=682 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.396274] type=1505 audit(1274588359.608:8):  operation="profile_replace" pid=682 name="/usr/lib/connman/scripts/dhclient-script"
[   17.452796] type=1505 audit(1274588359.664:9):  operation="profile_load" pid=684 name="/usr/bin/evince"
[   17.464084] type=1505 audit(1274588359.676:10):  operation="profile_load" pid=684 name="/usr/bin/evince-previewer"
[   17.470276] type=1505 audit(1274588359.680:11):  operation="profile_load" pid=684 name="/usr/bin/evince-thumbnailer"
[   17.516852] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.526969] type=1505 audit(1274588359.736:12):  operation="profile_load" pid=749 name="/usr/lib/cups/backend/cups-pdf"
[   17.528503] type=1505 audit(1274588359.740:13):  operation="profile_load" pid=749 name="/usr/sbin/cupsd"
[   17.579673] type=1505 audit(1274588359.788:14):  operation="profile_load" pid=752 name="/usr/sbin/tcpdump"
[   24.970537] ttyS1: LSR safety check engaged!
[   40.837228] ppdev: user-space parallel port driver
```

I am so sorry it took long, I am from Asia. ^^ I posted the problem in the morning, then I slept, I just woke up. :D please help me. :)

---

### Post by frozonecom on 2010-05-23
anyone there??

---

### Post by waltercool on 2010-05-23
Well, your problems seems here:

  15.440696] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   15.440724] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   16.452031] ALSA intel8x0.c:2435: codec_ready: codec is not ready [0x700000]
[   16.452243] Intel ICH 0000:00:1f.5: PCI INT B disabled
[   16.452262] Intel ICH: probe of 0000:00:1f.5 failed with error -5

Let me search something useful of that

EDIT:

Try that: [http://ubuntuforums.org/showpost.php?p=9214046&postcount=12](http://ubuntuforums.org/showpost.php?p=9214046&postcount=12)

---

### Post by frozonecom on 2010-05-23
I'll try that. Thanks for the rep. I will private message you and reply here if it works or not. thanks. :)

---

### Post by frozonecom on 2010-05-23
I tried the things posted in the link you gave me. However, the commands had errors.

sudo get clean && sudo apt-get autoremove  
```
gio@Ubuntu:~$ sudo get clean && sudo apt-get autoremove 
[sudo] password for gio: 
sudo: get: command not found
gio@Ubuntu:~$ 

```

_so I tried it separately._

sudo get clean
```
gio@Ubuntu:~$ sudo get clean
sudo: get: command not found
gio@Ubuntu:~$ 
```

sudo apt-get autoremove
```
gio@Ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gio@Ubuntu:~$ 
```

[U][I]After doing all of the comands :

[/I][/U]> sudo apt-get remove --purge alsa-base

sudo apt-get remove --purge pulseaudio

sudo get clean && sudo apt-get autoremove  

 sudo apt-get install alsa-base 

sudo apt-get install pulseaudio

_*I rebooted and see if anything changed. *_

The only thing I see that changed was that the _*speaker icon*_ is no longer in the panel, but it still works when I go to System>Preferences>Sound.

Also when I reboot, the error:
```
[   16.452031] ALSA intel8x0.c:2435: codec_ready: codec is not ready  [0x700000]
```
is still there.

is there any solutions you got? I will do anything to get my sound to work.

---

### Post by frozonecom on 2010-05-23
bump

---

### Post by frozonecom on 2010-05-23
bump. .. . .

---

### Post by lidex on 2010-05-23
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

Try
```
aplay -l
```
again. Same result? Do this:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```
Reboot.

---

### Post by waltercool on 2010-05-23
Woops... sorry...

Should be

sudo apt-get remove --purge alsa-base

sudo apt-get remove --purge pulseaudio

sudo apt-get clean && sudo apt-get autoremove

sudo apt-get install alsa-base

sudo apt-get install pulseaudio 

You can try the lidex post too if isnt working... (sorry... i have -04:00 GMT

---

### Post by frozonecom on 2010-05-24
> **lidex said:**
> Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```Logout/in.

Try
```
aplay -l
```again. Same result? Do this:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
``````
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```Reboot.

so i tried what you said lidex and i had some errors on the first part:

rm -r ~/.pulse ~/.asound*
```
rm: cannot remove `/home/gio/.pulse': No such file or directory
rm: cannot remove `/home/gio/.asound*': No such file or directory

```
sudo rm /etc/asound.conf
```
rm: cannot remove `/etc/asound.conf': No such file or directory
```

so i proceed to the second codes you gave me. I did all the steps and still no sound. Dummy output shows up in the speaker icon.

---

### Post by lidex on 2010-05-24
Did you reboot? What is the output of 
```
aplay -l
```

Try this:
```
sudo apt-get install --reinstall pulseaudio pavucontrol paprefs padevchooser libpulse0 pulseaudio-esound-compat pulseaudio-module-x11 pulseaudio-utils gstreamer0.10-pulseaudio 
```

Reboot.

---

### Post by frozonecom on 2010-05-24
yes i did reboot.

aplay -l
```
aplay: device_list:223: no soundcards found...
```

I tried the second one. I am rebooting now.

---

### Post by frozonecom on 2010-05-24
after i reboot, 

i checked the output of 
aplay -l
```
aplay: device_list:223: no soundcards found...
```

maybe this problem has something to do with modules or something??

and the speaker icon shows Dummy Output again.

---

### Post by frozonecom on 2010-05-24
if it should help, here is my updated /var/log/dmesg

```
[    0.374887] pci 0000:00:1d.1: reg 20 io port: [0x1820-0x183f]
[    0.374938] pci 0000:00:1d.2: reg 20 io port: [0x1840-0x185f]
[    0.374996] pci 0000:00:1d.7: reg 10 32bit mmio: [0xd0000000-0xd00003ff]
[    0.375051] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.375057] pci 0000:00:1d.7: PME# disabled
[    0.375139] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.375144] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.375167] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.375175] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.375183] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.375190] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.375198] pci 0000:00:1f.1: reg 20 io port: [0x1860-0x186f]
[    0.375206] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.375255] pci 0000:00:1f.3: reg 20 io port: [0x1880-0x189f]
[    0.375296] pci 0000:00:1f.5: reg 10 io port: [0x1c00-0x1cff]
[    0.375304] pci 0000:00:1f.5: reg 14 io port: [0x18c0-0x18ff]
[    0.375311] pci 0000:00:1f.5: reg 18 32bit mmio: [0xd0000c00-0xd0000dff]
[    0.375319] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xd0000800-0xd00008ff]
[    0.375347] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.375352] pci 0000:00:1f.5: PME# disabled
[    0.375381] pci 0000:00:1f.6: reg 10 io port: [0x2400-0x24ff]
[    0.375388] pci 0000:00:1f.6: reg 14 io port: [0x2000-0x207f]
[    0.375423] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.375428] pci 0000:00:1f.6: PME# disabled
[    0.375464] pci 0000:01:00.0: reg 10 32bit mmio: [0xd8000000-0xdfffffff]
[    0.375471] pci 0000:01:00.0: reg 14 io port: [0x3000-0x30ff]
[    0.375478] pci 0000:01:00.0: reg 18 32bit mmio: [0xd0100000-0xd010ffff]
[    0.375494] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.375512] pci 0000:01:00.0: supports D1 D2
[    0.375546] pci 0000:00:01.0: bridge io port: [0x3000-0x3fff]
[    0.375550] pci 0000:00:01.0: bridge 32bit mmio: [0xd0100000-0xd01fffff]
[    0.375555] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd8000000-0xdfffffff]
[    0.375589] pci 0000:02:02.0: reg 10 32bit mmio: [0xd0204000-0xd0205fff]
[    0.375615] pci 0000:02:02.0: reg 30 32bit mmio: [0x000000-0x003fff]
[    0.375631] pci 0000:02:02.0: supports D1 D2
[    0.375634] pci 0000:02:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.375639] pci 0000:02:02.0: PME# disabled
[    0.375671] pci 0000:02:04.0: reg 10 32bit mmio: [0xd0208000-0xd0208fff]
[    0.375713] pci 0000:02:04.0: PME# supported from D0 D3hot D3cold
[    0.375718] pci 0000:02:04.0: PME# disabled
[    0.375750] pci 0000:02:06.0: reg 10 32bit mmio: [0xd0209000-0xd0209fff]
[    0.375768] pci 0000:02:06.0: supports D1 D2
[    0.375771] pci 0000:02:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.375776] pci 0000:02:06.0: PME# disabled
[    0.375808] pci 0000:02:06.2: reg 10 32bit mmio: [0xd020a000-0xd020a7ff]
[    0.375816] pci 0000:02:06.2: reg 14 32bit mmio: [0xd0200000-0xd0203fff]
[    0.375855] pci 0000:02:06.2: supports D1 D2
[    0.375858] pci 0000:02:06.2: PME# supported from D0 D1 D2 D3hot
[    0.375863] pci 0000:02:06.2: PME# disabled
[    0.375893] pci 0000:02:06.3: reg 10 32bit mmio: [0xd0206000-0xd0207fff]
[    0.375934] pci 0000:02:06.3: supports D1 D2
[    0.375937] pci 0000:02:06.3: PME# supported from D0 D1 D2 D3hot
[    0.375942] pci 0000:02:06.3: PME# disabled
[    0.375978] pci 0000:00:1e.0: transparent bridge
[    0.375983] pci 0000:00:1e.0: bridge io port: [0x4000-0x4fff]
[    0.375988] pci 0000:00:1e.0: bridge 32bit mmio: [0xd0200000-0xd05fffff]
[    0.376026] pci_bus 0000:00: on NUMA node 0
[    0.376032] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.376207] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.376233] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.378813] ACPI: PCI Interrupt Link [LNKA] (IRQs *6)
[    0.378932] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[    0.379048] ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
[    0.379163] ACPI: PCI Interrupt Link [LNKD] (IRQs *6)
[    0.379278] ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
[    0.379393] ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled.
[    0.379510] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *0, disabled.
[    0.379627] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[    0.379848] SCSI subsystem initialized
[    0.379902] libata version 3.00 loaded.
[    0.379988] usbcore: registered new interface driver usbfs
[    0.380015] usbcore: registered new interface driver hub
[    0.380046] usbcore: registered new device driver usb
[    0.380211] ACPI: WMI: Mapper loaded
[    0.380214] PCI: Using ACPI for IRQ routing
[    0.380387] Bluetooth: Core ver 2.15
[    0.380419] NET: Registered protocol family 31
[    0.380421] Bluetooth: HCI device and connection manager initialized
[    0.380425] Bluetooth: HCI socket layer initialized
[    0.380428] NetLabel: Initializing
[    0.380430] NetLabel:  domain hash size = 128
[    0.380432] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.380449] NetLabel:  unlabeled traffic allowed by default
[    0.382663] pnp: PnP ACPI init
[    0.382683] ACPI: bus type pnp registered
[    0.386224] pnp: PnP ACPI: found 9 devices
[    0.386227] ACPI: ACPI bus type pnp unregistered
[    0.386232] PnPBIOS: Disabled by ACPI PNP
[    0.386247] system 00:04: ioport range 0x164e-0x164f has been reserved
[    0.386254] system 00:04: ioport range 0x600-0x60f has been reserved
[    0.386258] system 00:04: ioport range 0x700-0x70f has been reserved
[    0.386262] system 00:04: ioport range 0x800-0x80f has been reserved
[    0.386266] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.386270] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    0.386274] system 00:04: ioport range 0x1c0-0x1cf has been reserved
[    0.386279] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    0.386284] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.386288] system 00:04: ioport range 0x610-0x61f has been reserved
[    0.386293] system 00:04: iomem range 0xfec10000-0xfec1ffff has been reserved
[    0.386298] system 00:04: iomem range 0xff800000-0xffbfffff has been reserved
[    0.386302] system 00:04: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.386307] system 00:04: iomem range 0x0-0x9ffff could not be reserved
[    0.386311] system 00:04: iomem range 0xe0000-0xfffff could not be reserved
[    0.386316] system 00:04: iomem range 0xdf800-0xdffff could not be reserved
[    0.421012] AppArmor: AppArmor Filesystem Enabled
[    0.421046] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.421050] pci 0000:00:01.0:   IO window: 0x3000-0x3fff
[    0.421055] pci 0000:00:01.0:   MEM window: 0xd0100000-0xd01fffff
[    0.421061] pci 0000:00:01.0:   PREFETCH window: 0xd8000000-0xdfffffff
[    0.421069] pci 0000:02:06.0: CardBus bridge, secondary bus 0000:03
[    0.421072] pci 0000:02:06.0:   IO window: 0x004000-0x0040ff
[    0.421078] pci 0000:02:06.0:   IO window: 0x004400-0x0044ff
[    0.421083] pci 0000:02:06.0:   PREFETCH window: 0x10000000-0x13ffffff
[    0.421089] pci 0000:02:06.0:   MEM window: 0x18000000-0x1bffffff
[    0.421095] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.421099] pci 0000:00:1e.0:   IO window: 0x4000-0x4fff
[    0.421105] pci 0000:00:1e.0:   MEM window: 0xd0200000-0xd05fffff
[    0.421111] pci 0000:00:1e.0:   PREFETCH window: 0x10000000-0x15ffffff
[    0.421126] pci 0000:00:1e.0: setting latency timer to 64
[    0.421134] pci 0000:02:06.0: enabling device (0104 -> 0107)
[    0.421324] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[    0.421327] PCI: setting IRQ 10 as level-triggered
[    0.421333] pci 0000:02:06.0: PCI INT A -> Link[LNKE] -> GSI 10 (level, low) -> IRQ 10
[    0.421341] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.421345] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.421349] pci_bus 0000:01: resource 0 io:  [0x3000-0x3fff]
[    0.421353] pci_bus 0000:01: resource 1 mem: [0xd0100000-0xd01fffff]
[    0.421357] pci_bus 0000:01: resource 2 pref mem [0xd8000000-0xdfffffff]
[    0.421361] pci_bus 0000:02: resource 0 io:  [0x4000-0x4fff]
[    0.421365] pci_bus 0000:02: resource 1 mem: [0xd0200000-0xd05fffff]
[    0.421368] pci_bus 0000:02: resource 2 pref mem [0x10000000-0x15ffffff]
[    0.421372] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.421376] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.421379] pci_bus 0000:03: resource 0 io:  [0x4000-0x40ff]
[    0.421383] pci_bus 0000:03: resource 1 io:  [0x4400-0x44ff]
[    0.421387] pci_bus 0000:03: resource 2 pref mem [0x10000000-0x13ffffff]
[    0.421391] pci_bus 0000:03: resource 3 mem: [0x18000000-0x1bffffff]
[    0.421434] NET: Registered protocol family 2
[    0.421548] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.421872] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.421938] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.422003] TCP: Hash tables configured (established 8192 bind 8192)
[    0.422006] TCP reno registered
[    0.422089] NET: Registered protocol family 1
[    0.422160] Trying to unpack rootfs image as initramfs...
[    0.699026] Freeing initrd memory: 7466k freed
[    0.706263] Simple Boot Flag at 0x37 set to 0x1
[    0.706382] cpufreq-nforce2: No nForce2 chipset.
[    0.706415] Scanning for low memory corruption every 60 seconds
[    0.706583] audit: initializing netlink socket (disabled)
[    0.706618] type=2000 audit(1274685885.703:1): initialized
[    0.718304] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.720253] VFS: Disk quotas dquot_6.5.2
[    0.720327] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.721055] fuse init (API version 7.12)
[    0.721167] msgmni has been set to 486
[    0.721419] alg: No test for stdrng (krng)
[    0.721434] io scheduler noop registered
[    0.721436] io scheduler anticipatory registered
[    0.721439] io scheduler deadline registered
[    0.721494] io scheduler cfq registered (default)
[    0.721580] pci 0000:01:00.0: Boot video device
[    0.721708] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.721739] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.721899] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.721905] ACPI: Power Button [PWRF]
[    0.721983] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.760052] ACPI: Lid Switch [LID]
[    0.760114] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.760118] ACPI: Sleep Button [SLPB]
[    0.760280] fan PNP0C0B:00: registered as cooling_device0
[    0.760288] ACPI: Fan [FAN0] (off)
[    0.760413] fan PNP0C0B:01: registered as cooling_device1
[    0.760421] ACPI: Fan [FAN1] (off)
[    0.760579] Marking TSC unstable due to TSC halts in idle
[    0.760600] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.760622] processor LNXCPU:00: registered as cooling_device2
[    0.760626] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.764012] Switched to high resolution mode on CPU 0
[    0.840211] thermal LNXTHERM:01: registered as thermal_zone0
[    0.840222] ACPI: Thermal Zone [THRM] (57 C)
[    0.840256] ACPI: SBS HC: EC = 0xcf831480, offset = 0x18, query_bit = 0x20
[    1.032070] ACPI: Smart Battery System [SBS0]: AC Adapter [AC0] (on-line)
[    1.656072] ACPI: Smart Battery System [SBS0]: Battery Slot [BAT0] (battery absent)
[    2.088074] ACPI: Smart Battery System [SBS0]: Battery Slot [BAT1] (battery absent)
[    2.088094] isapnp: Scanning for PnP cards...
[    2.442041] isapnp: No Plug & Play device found
[    2.443394] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.443519] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[    2.444082] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    2.444088] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    2.444097] serial 0000:00:1f.6: PCI INT B disabled
[    2.445262] brd: module loaded
[    2.445840] loop: module loaded
[    2.445926] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    2.446056] ata_piix 0000:00:1f.1: version 2.13
[    2.446070] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
[    2.446076] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    2.446262] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 6
[    2.446266] PCI: setting IRQ 6 as level-triggered
[    2.446271] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 6 (level, low) -> IRQ 6
[    2.446315] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.446398] scsi0 : ata_piix
[    2.446488] scsi1 : ata_piix
[    2.447683] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
[    2.447687] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
[    2.448759] Fixed MDIO Bus: probed
[    2.448804] PPP generic driver version 2.4.2
[    2.448908] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.449105] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    2.449110] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[    2.449125] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.449130] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.449175] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.453090] ehci_hcd 0000:00:1d.7: debug port 1
[    2.453097] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.453364] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xd0000000
[    2.468034] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.468138] usb usb1: configuration #1 chosen from 1 choice
[    2.468175] hub 1-0:1.0: USB hub found
[    2.468188] hub 1-0:1.0: 6 ports detected
[    2.468259] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.468280] uhci_hcd: USB Universal Host Controller Interface driver
[    2.468488] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 6
[    2.468493] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 6 (level, low) -> IRQ 6
[    2.468500] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.468504] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.468544] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.468568] uhci_hcd 0000:00:1d.0: irq 6, io base 0x00001800
[    2.468661] usb usb2: configuration #1 chosen from 1 choice
[    2.468697] hub 2-0:1.0: USB hub found
[    2.468706] hub 2-0:1.0: 2 ports detected
[    2.468925] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
[    2.468930] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 6 (level, low) -> IRQ 6
[    2.468937] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.468941] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.468976] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.468998] uhci_hcd 0000:00:1d.1: irq 6, io base 0x00001820
[    2.469093] usb usb3: configuration #1 chosen from 1 choice
[    2.469126] hub 3-0:1.0: USB hub found
[    2.469134] hub 3-0:1.0: 2 ports detected
[    2.469179] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 6 (level, low) -> IRQ 6
[    2.469188] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.469192] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.469228] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.469250] uhci_hcd 0000:00:1d.2: irq 6, io base 0x00001840
[    2.469352] usb usb4: configuration #1 chosen from 1 choice
[    2.469384] hub 4-0:1.0: USB hub found
[    2.469392] hub 4-0:1.0: 2 ports detected
[    2.469494] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOU2] at 0x60,0x64 irq 1,12
[    2.471036] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.471995] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.472024] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.472062] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.472066] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.472070] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.472135] mice: PS/2 mouse device common for all mice
[    2.472290] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    2.472307] rtc0: alarms up to one month, y3k, 242 bytes nvram
[    2.472431] device-mapper: uevent: version 1.0.3
[    2.472535] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    2.475513] device-mapper: multipath: version 1.1.0 loaded
[    2.475517] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.475661] EISA: Probing bus 0 at eisa.0
[    2.475669] Cannot allocate resource for EISA slot 1
[    2.475672] Cannot allocate resource for EISA slot 2
[    2.475675] Cannot allocate resource for EISA slot 3
[    2.475678] Cannot allocate resource for EISA slot 4
[    2.475696] EISA: Detected 0 cards.
[    2.475793] cpuidle: using governor ladder
[    2.475868] cpuidle: using governor menu
[    2.476473] TCP cubic registered
[    2.476674] NET: Registered protocol family 10
[    2.477188] lo: Disabled Privacy Extensions
[    2.477563] NET: Registered protocol family 17
[    2.477583] Bluetooth: L2CAP ver 2.13
[    2.477585] Bluetooth: L2CAP socket layer initialized
[    2.477589] Bluetooth: SCO (Voice Link) ver 0.6
[    2.477591] Bluetooth: SCO socket layer initialized
[    2.477627] Bluetooth: RFCOMM TTY layer initialized
[    2.477631] Bluetooth: RFCOMM socket layer initialized
[    2.477634] Bluetooth: RFCOMM ver 1.11
[    2.478044] Using IPI No-Shortcut mode
[    2.478109] PM: Resume from disk failed.
[    2.478122] registered taskstats version 1
[    2.478235]   Magic number: 10:910:420
[    2.478239]   hash matches /build/buildd/linux-2.6.31/drivers/base/power/main.c:339
[    2.478302] rtc_cmos 00:01: setting system clock to 2010-05-24 07:24:47 UTC (1274685887)
[    2.478306] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.478308] EDD information not available.
[    2.572032] hub 2-0:1.0: over-current change on port 1
[    2.616485] ata2.00: ATAPI: Slimtype DVDRW SOSW-852S, PRS9, max UDMA/33
[    2.617022] ata1.00: ATA-6: HTS541060G9AT00, MB3VA60A, max UDMA/100
[    2.617026] ata1.00: 117210240 sectors, multi 16: LBA48 
[    2.632318] ata2.00: configured for UDMA/33
[    2.632734] ata1.00: configured for UDMA/100
[    2.632867] scsi 0:0:0:0: Direct-Access     ATA      HTS541060G9AT00  MB3V PQ: 0 ANSI: 5
[    2.632994] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.633036] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    2.633087] sd 0:0:0:0: [sda] Write Protect is off
[    2.633090] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.633117] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.633248]  sda:
[    2.634070] scsi 1:0:0:0: CD-ROM            Slimtype DVDRW SOSW-852S  PRS9 PQ: 0 ANSI: 5
[    2.636910] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.636914] Uniform CD-ROM driver Revision: 3.20
[    2.636996] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.637045] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.650549] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.660009]  sda1 sda2 <
[    2.676029] hub 2-0:1.0: over-current change on port 2
[    2.688040]  sda5 >
[    2.688292] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.688308] Freeing unused kernel memory: 544k freed
[    2.688649] Write protecting the kernel text: 4584k
[    2.688690] Write protecting the kernel read-only data: 1840k
[    2.851426] Linux agpgart interface v0.103
[    2.939433] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[    2.965436] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:02/device:03/input/input5
[    2.965479] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    3.050373] ohci1394 0000:02:06.2: PCI INT A -> Link[LNKE] -> GSI 10 (level, low) -> IRQ 10
[    3.058887] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    3.093535] [drm] Initialized drm 1.1.0 20060810
[    3.120444] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[d020a000-d020a7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.120746] b44 0000:02:02.0: PCI INT A -> Link[LNKD] -> GSI 6 (level, low) -> IRQ 6
[    3.120996] [drm] radeon default to kernel modesetting DISABLED.
[    3.121114] pci 0000:01:00.0: power state changed by ACPI to D0
[    3.121122] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 6 (level, low) -> IRQ 6
[    3.122118] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
[    3.180244] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[    3.180271] b44.c:v2.0
[    3.200707] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:c0:9f:48:15:72
[    3.926123] PM: Starting manual resume from disk
[    3.926128] PM: Resume from partition 8:5
[    3.926130] PM: Checking hibernation image.
[    3.926351] PM: Resume from disk failed.
[    3.929747] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.929752] EXT4-fs (sda1): write access will be enabled during recovery
[    3.960635] EXT4-fs (sda1): barriers enabled
[    4.392164] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f00001e8486]
[    4.511642] kjournald2 starting: pid 355, dev sda1:8, commit interval 5 seconds
[    4.511682] EXT4-fs (sda1): delayed allocation enabled
[    4.511686] EXT4-fs: file extents enabled
[    4.520134] EXT4-fs: mballoc enabled
[    4.520148] EXT4-fs (sda1): recovery complete
[    4.520779] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    5.724251] type=1505 audit(1274685890.745:2): operation="profile_load" pid=379 name=/usr/share/gdm/guest-session/Xsession
[    5.727106] type=1505 audit(1274685890.745:3): operation="profile_load" pid=380 name=/sbin/dhclient3
[    5.727839] type=1505 audit(1274685890.745:4): operation="profile_load" pid=380 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.728387] type=1505 audit(1274685890.749:5): operation="profile_load" pid=380 name=/usr/lib/connman/scripts/dhclient-script
[    5.806709] type=1505 audit(1274685890.826:6): operation="profile_load" pid=381 name=/usr/bin/evince
[    5.820696] type=1505 audit(1274685890.841:7): operation="profile_load" pid=381 name=/usr/bin/evince-previewer
[    5.828712] type=1505 audit(1274685890.849:8): operation="profile_load" pid=381 name=/usr/bin/evince-thumbnailer
[    5.865924] type=1505 audit(1274685890.885:9): operation="profile_load" pid=383 name=/usr/lib/cups/backend/cups-pdf
[    5.866787] type=1505 audit(1274685890.885:10): operation="profile_load" pid=383 name=/usr/sbin/cupsd
[    5.880610] type=1505 audit(1274685890.901:11): operation="profile_load" pid=384 name=/usr/sbin/tcpdump
[   11.435039] Adding 730916k swap on /dev/sda5.  Priority:-1 extents:1 across:730916k 
[   11.745104] EXT4-fs (sda1): internal journal on sda1:8
[   11.849623] udev: starting version 147
[   12.663250] lp: driver loaded but no devices found
[   12.890797] irda_init()
[   12.890810] NET: Registered protocol family 23
[   12.894050] acer-wmi: Acer Laptop ACPI-WMI Extras
[   12.894065] acer-wmi: No or unsupported WMI interface, unable to load
[   12.899036] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.090680] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   13.090704] nsc-ircc, chip->init
[   13.090712] nsc-ircc, Found chip at base=0x164e
[   13.090734] nsc-ircc, driver loaded (Dag Brattli)
[   13.090740] nsc_ircc_open(), can't get iobase of 0x2f8
[   13.090764] nsc-ircc, Found chip at base=0x164e
[   13.090786] nsc-ircc, driver loaded (Dag Brattli)
[   13.090789] nsc_ircc_open(), can't get iobase of 0x2f8
[   13.091023] nsc-ircc 00:08: disabled
[   13.102145] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.246576] lib80211: common routines for IEEE802.11 drivers
[   13.246580] lib80211_crypt: registered algorithm 'NULL'
[   13.266382] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   13.266385] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   13.290925] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   13.290928] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   13.291005] ipw2200 0000:02:04.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   13.291067] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   13.291108] ipw2200 0000:02:04.0: firmware: requesting ipw2200-bss.fw
[   13.335660] intel_rng: FWH not detected
[   13.760653] ipw2200: Radio Frequency Kill Switch is On:
[   13.760657] Kill switch must be turned off for wireless networking to work.
[   13.775205] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   13.778215] tifm_7xx1 0000:02:06.3: PCI INT A -> Link[LNKE] -> GSI 10 (level, low) -> IRQ 10
[   13.784103] yenta_cardbus 0000:02:06.0: CardBus bridge found [1025:0064]
[   13.784118] yenta_cardbus 0000:02:06.0: Enabling burst memory read transactions
[   13.784123] yenta_cardbus 0000:02:06.0: Using CSCINT to route CSC interrupts to PCI
[   13.784126] yenta_cardbus 0000:02:06.0: Routing CardBus interrupts to PCI
[   13.784131] yenta_cardbus 0000:02:06.0: TI: mfunc 0x01a21b22, devctl 0x64
[   13.917920] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[   13.966523] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
[   14.016567] yenta_cardbus 0000:02:06.0: ISA IRQ mask 0x08b8, PCI irq 10
[   14.016572] yenta_cardbus 0000:02:06.0: Socket status: 30000006
[   14.016578] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   14.016588] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[   14.016592] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x4fff: clean.
[   14.016863] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd05fffff
[   14.016866] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0x10000000 - 0x15ffffff
[   14.335099] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   14.335132] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   14.872089] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   14.873456] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   14.874059] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   14.874564] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   14.875227] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   15.344028] ALSA intel8x0.c:2435: codec_ready: codec is not ready [0x700000]
[   15.344061] Intel ICH 0000:00:1f.5: PCI INT B disabled
[   15.344082] Intel ICH: probe of 0000:00:1f.5 failed with error -5
[   15.420028] Clocksource tsc unstable (delta = -112897766 ns)
[   15.976907] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.980435] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   17.079186] type=1505 audit(1274685902.097:12): operation="profile_replace" pid=891 name=/usr/share/gdm/guest-session/Xsession
[   17.081713] type=1505 audit(1274685902.101:13): operation="profile_replace" pid=892 name=/sbin/dhclient3
[   17.082452] type=1505 audit(1274685902.101:14): operation="profile_replace" pid=892 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   17.082856] type=1505 audit(1274685902.101:15): operation="profile_replace" pid=892 name=/usr/lib/connman/scripts/dhclient-script
[   17.089172] type=1505 audit(1274685902.109:16): operation="profile_replace" pid=893 name=/usr/bin/evince
[   17.096735] ttyS1: LSR safety check engaged!
[   17.120811] type=1505 audit(1274685902.141:17): operation="profile_replace" pid=893 name=/usr/bin/evince-previewer
[   17.129614] type=1505 audit(1274685902.149:18): operation="profile_replace" pid=893 name=/usr/bin/evince-thumbnailer
[   17.146228] type=1505 audit(1274685902.165:19): operation="profile_replace" pid=901 name=/usr/lib/cups/backend/cups-pdf
[   17.147095] type=1505 audit(1274685902.165:20): operation="profile_replace" pid=901 name=/usr/sbin/cupsd
[   17.150688] type=1505 audit(1274685902.169:21): operation="profile_replace" pid=902 name=/usr/sbin/tcpdump
[   18.260206] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   18.260223] agpgart-intel 0000:00:00.0: putting AGP V2 device into 1x mode
[   18.260256] pci 0000:01:00.0: putting AGP V2 device into 1x mode
[   18.503011] [drm] Setting GART location based on new memory map
[   18.503019] [drm] Loading R300 Microcode
[   18.503062] [drm] Num pipes: 1
[   18.503069] [drm] writeback test succeeded in 1 usecs

```

---

### Post by lidex on 2010-05-24
Try this command:
```
modprobe snd_intel8x0 
```

or use sudo if needed

---

### Post by Titus A Duxass on 2010-05-24
Try using sudo apt-get clean and not sudo get clean

---

### Post by frozonecom on 2010-05-24
I tried both of your commands.

i tried modprobe snd_intel8x0 and sudo modprobe snd_intel8x0 and there was no output.
is that bad or good??

and yes, i tried sudo apt-get clean. no output either. gonna reboot and see if anything change.

---

### Post by frozonecom on 2010-05-24
still the same. 

aplay -l says no sound cards found. speaker icon still dummy output. any ideas left?:(

---

### Post by frozonecom on 2010-05-24
bump. ..

---

### Post by waltercool on 2010-05-24
Try with that:

modprobe -r snd-intel8x0
modprobe snd-index8x0 ac97_quirk=1 xbox=1

Source: [http://alsa.opensrc.org/index.php/Intel8x0](http://alsa.opensrc.org/index.php/Intel8x0)

---

### Post by frozonecom on 2010-05-24
thank you for your help. :) i am gonna try what you wrote. :)

hope it works.

---

### Post by frozonecom on 2010-05-24
oh no. the results are not good.

```
sudo modprobe -r snd-intel8x0
```
worked out great, i added sudo because without sudo, it says that operation is not **permitted, **so i tried adding sudo, and it worked. And it didnt say anything.

```
sudo modprobe snd-index8x0 ac97_quirk=1 xbox=1
```
didnt work. 
here is the ouput:
```
FATAL: Module snd_index8x0 not found.
```

maybe i should install that module and see if the sound may work?? but i dont know how to do that, any ideas?

---

### Post by Yellow Pasque on 2010-05-24
```
sudo modprobe snd-index8x0 ac97_quirk=1 xbox=1
```
^There was a typo. It should have been:
```
sudo modprobe snd-in**tel**8x0 ac97_quirk=1 xbox=1
```

---

### Post by waltercool on 2010-05-24
Idk... i just copy/pasted from alsa wiki :P

Works?

---

### Post by frozonecom on 2010-05-25
i tried the post of tamujin and the sound wont work.

still dummy output.

sorry for the late reply, i was searching for solutions my self.

so, any more ideas? i think the sound driver is not present, where can i get it?

---

### Post by frozonecom on 2010-05-25
This page might help for me, but I dont know what to do. Please tell me what to do.

First I went to this link. [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) , then I went to "is my sound card supported?" (here is the link if you cant find it in the page: [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main))

then,

I clicked **INTEL** because it says in *sudo lspci | grep audio* :
```
00:1f.5 Multimedia audio controller: ***Intel*** Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
```so i think, I am in the right path.

then I clicked **DETAILS** on the row of **ICH southbridge AC97 audio **because :

```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (**ICH4/ICH4-L/ICH4-M**) A**C'97 Audio Controller** (rev 03)
```and after that I dont know what to do, but i did this code :

[FONT=Verdana]```
modinfo soundcore
```and the output is[/FONT] 
```
filename:       /lib/modules/2.6.31-14-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     3A50BBE947364A4D9DB6A97
depends:        
vermagic:       2.6.31-14-generic SMP mod_unload modversions 586 
```and it says that :

> If this command returns that you have this module, then you don't need to recompile your kernel. but i dont know if the output is good or bad, I dont know what to do, sorry. im rather stupid. :D

so please help me, :((

---

### Post by frozonecom on 2010-05-25
also in this thread: 

[http://ubuntuforums.org/showthread.php?t=1492002](http://ubuntuforums.org/showthread.php?t=1492002)

the author is saying that he is having problems with intel8x0 too.

and someone suggested that he needs to delete the config files in
```
~/.pulse*
```

so maybe thats also my problem? if so, how do i delete it? would it be harmful to my system?

---

### Post by frozonecom on 2010-05-25
so tell me wat ya think?? XD

---

### Post by CHNdonny on 2010-05-25
> **frozonecom said:**
> This page might help for me, but I dont know what to do. Please tell me what to do.

First I went to this link. [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) , then I went to "is my sound card supported?" (here is the link if you cant find it in the page: [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main))

then,

I clicked **INTEL** because it says in *sudo lspci | grep audio* :
```
00:1f.5 Multimedia audio controller: ***Intel*** Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
```so i think, I am in the right path.

then I clicked **DETAILS** on the row of **ICH southbridge AC97 audio **because :

```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (**ICH4/ICH4-L/ICH4-M**) A**C'97 Audio Controller** (rev 03)
```and after that I dont know what to do, but i did this code :

[FONT=Verdana]```
modinfo soundcore
```and the output is[/FONT] 
```
filename:       /lib/modules/2.6.31-14-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     3A50BBE947364A4D9DB6A97
depends:        
vermagic:       2.6.31-14-generic SMP mod_unload modversions 586 
```and it says that :

but i dont know if the output is good or bad, I dont know what to do, sorry. im rather stupid. :D

so please help me, :((

I read your article,incompatibility probably occurred,It's obvious that soundcore.ko is working on 2.6.31-14-generic and when you ran cat /proc/asound/version,it shows the alsa module was compiled on  2.6.32-22-generic
this is my tip,but I don't know how to resolve it

---

### Post by frozonecom on 2010-05-25
oh ok. :)) but i had sound in ubuntu 9.10. I dont know why i didnt have sound now. and i installed using cd. Uhm, can you pls tell me where the sound card slot is in my laptop,

it is Acer 1681 WLMi . Maybe the sound card is improperly placed?

---

### Post by Yellow Pasque on 2010-05-25
The sound chip is integrated and lspci shows it, so you're okay there. The issue is with the driver loading

> Advanced Linux Sound Architecture Driver Version 1.0.23.


It looks like you used the ALSA upgrade script at some point to get ALSA 1.0.23. If you installed a kernel upgrade, you need to run the build (-c) and install (-i) options of it again: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by frozonecom on 2010-05-25
okay, i am gonna try it tomorrow, i am gonna sleep now. I am on GMT +8:00

hope it works.

---

### Post by frozonecom on 2010-05-25
i did what you said, and cat /proc/asound/version says:

```
gio@gio-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May 25 2010 for kernel 2.6.31-21-generic (SMP).
gio@gio-laptop:~$ 
```

---

### Post by frozonecom on 2010-05-25
so what should i do next? any ideas?

---

### Post by lidex on 2010-05-26
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by frozonecom on 2010-05-26
```
gio@gio-laptop:~$ sudo bash utils_alsa-info.sh
[sudo] password for gio: 
ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'utils_alsa-info.sh --help' for command line options.

/usr/sbin/alsactl: save_state:1504: No soundcards found...
cat: /tmp/alsa-info.AQFHlmX7TX/alsactl.tmp: No such file or directory
Automatically upload ALSA information to www.alsa-project.org? [y/N] : n


Your ALSA information is in /tmp/alsa-info.txt.qAdHbVIXoB

gio@gio-laptop:~$ 
```

should i upload ALSA Information, i selected no because i dont know what to do. And that is the ouput of the code you gave. i dont know what any of those words mean.:KS

---

### Post by lidex on 2010-05-26
It's not necessary. Copy and paste the file from your temp directory into a post using code tags.

---

### Post by frozonecom on 2010-05-26
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Wed May 26 04:26:11 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 9.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.10"


!!DMI Information
!!---------------

Manufacturer:      Acer
Product Name:      Aspire 1680   


!!Kernel Information
!!------------------

Kernel release:    2.6.31-21-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1f.5 0401: 8086:24c5 (rev 03)
    Subsystem: 1025:0064


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: power_save=10 power_save_controller=N


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  1 May 26 00:15 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 May 26 00:15 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:235: no soundcards found...

ARECORD

arecord: device_list:235: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
michael_mic
arc4
ecb
lib80211_crypt_tkip
aes_i586
aes_generic
lib80211_crypt_ccmp
binfmt_misc
ppdev
snd_intel8x0
snd_ac97_codec
ac97_bus
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
pcmcia
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
iptable_filter
joydev
yenta_socket
snd_seq
rsrc_nonstatic
snd_timer
pcmcia_core
ip_tables
tifm_7xx1
snd_seq_device
snd
tifm_core
x_tables
soundcore
ipw2200
libipw
lib80211
psmouse
snd_page_alloc
shpchp
irda
lp
serio_raw
crc_ccitt
parport
led_class
video
output
ohci1394
ieee1394
b44
ssb
mii
radeon
ttm
drm
i2c_algo_bit
intel_agp
agpgart


!!ALSA/HDA dmesg
!!------------------

[   15.436169] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   16.252029] ALSA intel8x0.c:2435: codec_ready: codec is not ready [0x700000]
[   16.252062] Intel ICH 0000:00:1f.5: PCI INT B disabled

```

sorry i post the wrong thing. ahah. :)) by the way, thats the file you requested.

---

### Post by lidex on 2010-05-26
What is the output of these commands:
```
locate alsactl
```
```
ls /etc/modprobe.d
```

---

### Post by frozonecom on 2010-05-26
locate alsactl

```
/sbin/alsactl
/usr/sbin/alsactl
/usr/share/man/man1/alsactl.1
/usr/share/man/man1/alsactl.1.gz
/usr/share/man/man7/alsactl_init.7
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/.deps
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/Makefile
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/Makefile.am
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/Makefile.in
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/alsactl
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/alsactl.1
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/alsactl.c
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/alsactl.h
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/alsactl.o
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/alsactl_init.7
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/alsactl_init.xml
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/init
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/init_parse.c
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/init_parse.o
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/init_sysdeps.c
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/init_sysfs.c
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/init_utils_run.c
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/init_utils_string.c
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/list.h
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/state.c
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/state.o
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/utils.c
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/utils.o
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/.deps/alsactl.Po
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/.deps/init_parse.Po
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/.deps/state.Po
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/.deps/utils.Po
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/init/00main
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/init/Makefile
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/init/Makefile.am
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/init/Makefile.in
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/init/default
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/init/hda
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/init/help
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/init/info
/usr/src/Alsa-1.0.23/alsa-utils-1.0.23/alsactl/init/test
```ls /etc/modprobe.d
```

alsa-base.conf          blacklist-firewire.conf     blacklist-oss.conf
blacklist-ath_pci.conf  blacklist-framebuffer.conf  blacklist-watchdog.conf
blacklist.conf          blacklist-modem.conf        libpisock9.conf
```


oh and the text "blacklist-oss.conf" is written in cyan and in bold as it appears in the terminal, it is like this :
[B]
[COLOR=Cyan]blacklist-oss.conf[/COLOR][/B]

---

### Post by lidex on 2010-05-26
Something screwy here dude. You say you're using 10.04, the script says 9.10 and the kernel verifies it. What does this say:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

---

### Post by frozonecom on 2010-05-26
```
gio@gio-laptop:~$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
[sudo] password for gio: 
Cannot stat /dev/dsp*: No such file or directory
Cannot stat /dev/dsp*: No such file or directory
gio@gio-laptop:~$ 
```

---

### Post by lidex on 2010-05-26
Wow. Try this:
```
sudo apt-get install --reinstall ubuntu-desktop
```
and let it complete. Then:
```
sudo update-grub
```
**Reboot**

---

### Post by frozonecom on 2010-05-26
i have done what you told me and still no sound

---

### Post by frozonecom on 2010-05-26
bump...

---

### Post by lidex on 2010-05-26
Now this:
```
aplay -l
```

---

### Post by frozonecom on 2010-05-26
> **lidex said:**
> Now this:
```
aplay -l
```
```
gio@gio-laptop:~$ aplay -l
aplay: device_list:235: no soundcards found...
```

i'm a gonner. :(

---

### Post by frozonecom on 2010-05-26
badump///////////

---

### Post by Yellow Pasque on 2010-05-26
It looks like an upgrade gone bad. What is output of:
```
sudo apt-get dist-upgrade
```

> i'm a gonner.
Huh?

---

### Post by frozonecom on 2010-05-26
```
gio@gio-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

and also, when i run sudo alsaconf, i get this :

```
gio@gio-laptop:~$ sudo alsaconf
Building card database..

























Running update-modules...
/usr/sbin/alsaconf: line 929: update-modules: command not found
Setting default volumes...
amixer: Mixer attach default error: No such file or directory
Saving the mixer setup used for this in /etc/asound.state.
/usr/sbin/alsactl: save_state:1502: No soundcards found...



















===============================================================================

 Now ALSA is ready to use.
 For adjustment of volumes, use your favorite mixer.

 Have a lot of fun!


gio@gio-laptop:~$ 
```

---

### Post by lidex on 2010-05-29
Go to this page:
[http://www.linlap.com/wiki/audio+tester]("http://www.linlap.com/wiki/audio+tester") and download the two files necessary to run the test. You'll find the instructions there. Report your results.

---

### Post by frozonecom on 2010-05-30
there is no sound i can hear after i executed the audio test.

---

### Post by sophist on 2010-05-30
I've the same problem and I've fix it by the following 

1. you have to upgrade your Alsa to 1.0.23

go to this website and follow the instructions 
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/")

skip the second command


after that 

do the following command to be able to run your media files.

sudo apt-get install ubuntu-restricted-extras

and then 

this one

sudo apt-get upgrade  ubuntu-restricted-extras

---

### Post by esrom02 on 2012-02-24
**I know this thread is more than a year old, but I'm having the same problem and I can't fix it by following the instruction above me.. please help me..**

---

### Post by Eiji Takanaka on 2012-02-24
Have you tried turning your speakers on?

---

### Post by esrom02 on 2012-02-24
**yeah :( I'm using 10.04.. and whenever there is some action on desktop i.e moving the cursor, it produces "zzzzzzzzzzzzz" sound..**

---

