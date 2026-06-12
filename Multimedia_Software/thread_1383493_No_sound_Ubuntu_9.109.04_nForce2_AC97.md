---
title: "No sound Ubuntu 9.10/9.04 nForce2 AC97"
date: 2010-01-17
forum: Multimedia Software
---

### Post by Fendro on 2010-01-17
Hello,
I have recently decided to abandon Windows OS for good and try Ubuntu. Firstly, I installed 9.10 and everything seemed to be fine - I configured network connection, downloaded and installed Flash player, Skype etc with ease. At this point I thought to myself "Why I even bothered with Widnows before?" and decided to curl up on the sofa listening to Armin's 'A state of trance 439'. Unfortunately it turned out that I don't have any sound at all. Since I am fresh new to Ubuntu I decided to Google that and resolve my problem myself without bothering anyone. Ten+ hours of my life were lost and I still couldn't get my sound working but many of the posts pointed that 9.10 have some sound issues. For that reason I reinstalled 9.10 and went for 9.04. Despite that I still can't hear anything (music, videos, youtube .. nothing). Here is some information and things I've tried:
Inspected /var/log/syslog :
```
Jan 17 07:12:10 miroPC kernel: [    8.984027] intel8x0_measure_ac97_clock: measured 55986 usecs
Jan 17 07:12:10 miroPC kernel: [    8.984032] intel8x0: clocking to 40820
```
Inspected  PCI devices found - (lspci -v):
```
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-nvidia
	Kernel modules: nvidia-agp

00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
	Subsystem: nVidia Corporation Device 0c17
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
	Subsystem: nVidia Corporation Device 0c17
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
	Subsystem: nVidia Corporation Device 0c17
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
	Subsystem: nVidia Corporation Device 0c17
	Flags: 66MHz, fast devsel

00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
	Subsystem: nVidia Corporation Device 0c17
	Flags: 66MHz, fast devsel

00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
	Subsystem: Elitegroup Computer Systems Device 1b31
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
	Subsystem: Elitegroup Computer Systems Device 1b31
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at c000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10)
	Subsystem: Elitegroup Computer Systems Device 1b31
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at ec003000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10)
	Subsystem: Elitegroup Computer Systems Device 1b31
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at ec004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 20)
	Subsystem: Elitegroup Computer Systems Device 1b31
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at ec005000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
	Subsystem: Elitegroup Computer Systems Device 1b31
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at ec000000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at c400 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

[B]00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
	Subsystem: Elitegroup Computer Systems Device 1b31
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	I/O ports at b000 [size=256]
	I/O ports at b400 [size=128]
	Memory at ec001000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0[/B]

00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: ea000000-ebffffff
	Prefetchable memory behind bridge: 50000000-500fffff
	Kernel modules: shpchp

00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: Device f019:1b31
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd

00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
	Flags: bus master, 66MHz, medium devsel, latency 32
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: e8000000-e9ffffff
	Prefetchable memory behind bridge: c0000000-dfffffff
	Kernel modules: shpchp

01:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at 9000 [size=256]
	Memory at eb000000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at 50000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp

01:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46) (prog-if 10)
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at eb001000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at 9400 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

02:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
	Subsystem: Info-Tek Corp. Device 0247
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at a000 [size=256]
	Memory at e9000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at e8000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeonfb

02:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
	Subsystem: Info-Tek Corp. Device 0246
	Flags: 66MHz, medium devsel
	Memory at d0000000 (32-bit, prefetchable) [disabled] [size=256M]
	Memory at e9010000 (32-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>
```
lsmod:
```
Module                  Size  Used by
binfmt_misc            16776  1 
radeon                342816  2 
drm                    96424  3 radeon
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25872  0 
output                 11008  1 video
input_polldev          11912  0 
lp                     17156  0 
[B]snd_intel8x0           38684  3 
snd_ac97_codec        112548  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec[/B]
snd_pcm_oss            45984  0 
snd_mixer_oss          22912  1 snd_pcm_oss
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
ppdev                  15620  0 
snd_seq_dummy          10884  0 
snd_seq_oss            36224  0 
snd_seq_midi           14240  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57584  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29192  2 snd_pcm,snd_seq
snd_seq_device         15372  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia_agp             14492  1 
snd                    66852  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         17032  2 snd_intel8x0,snd_pcm
pcspkr                 10496  0 
agpgart                42696  2 drm,nvidia_agp
shpchp                 40212  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
i2c_nforce2            14980  0 
usbhid                 42336  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
forcedeth              61712  0 
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```
sudo gedit /etc/modprobe.d/alsa-base.conf:
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
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
```

I've tried to add:
```
options snd-pcsp index=-2
options snd slots=snd_intel8x0
options snd_intel8x0 model=auto
alias snd-card-0 snd_intel8x0
options snd_intel8x0 enable_msi=1
```
to the end of alsa-base.conf and then my audio card is no detected at all. I've upgraded ALSA driver - cat /proc/asound/version:
```
Advanced Linux Sound Architecture Driver Version 1.0.20.
Compiled on Jan 17 2010 for kernel 2.6.28-17-generic (SMP).
```
aplay -l:
```
miroslav@miroPC:~$ Modprobe
bash: Modprobe: command not found
miroslav@miroPC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
EDIT (Added snd-intel8x0) - cat /etc/modules:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
snd-intel8x0
```
There are GNOME ALSA MIXER, PulseAudio and Kmix currently installed.
In BIOS AC 97 is Enabled.
I have runned alsamixer in terminal and have unmuted and increased volume on everything. Done the same in Volume Control, GNOME ALSA MIXER and PulseAudio Volume Control. 
This is how my System->Preferences->Sound looks like:
[http://img693.imageshack.us/img693/8828/screenshottb.png](http://img693.imageshack.us/img693/8828/screenshottb.png)
The Options in Sound Events, Music and Movies and Audio Conferencing are:
NVidia nForce2 with CMI9739 NVidia nForce2 IEC958 (ALSA)
NVidia nForce2 with CMI9739 NVidia nForce2 (ALSA)
NVidia nForce2 with CMI9739 NVidia nForce2 (OSS)
NVidia nForce2 with CMI9739 NVidia nForce2 (OSS)
NVidia nForce2 with CMI9739 NVidia nForce2 (OSS) (yes there are three of these :/ )
ALSA - Advanced Linux Sound Architecture
OSS- Opend Sound System
PulseAudio Sound Server
The Options in Default Mixer Tracks:
Capture: Monitor of NVidia nForce2 - NVidia nForce2 (PulseAudio Mixer)
Capture: NVidia nForce2 - NVidia nForce2 (PulseAudio Mixer)
C-Media Electronics CMI9739 (OSS Mixer)
NVidia nForce2 (Alsa mixer)
Playback: NVidia nForce2 - NVidia nForce2 (PulseAudio Mixer)
I think I have tried them all although I feel that I couldn't configure OSS the right way.
Also tried solutions mentioned in these threads:
[http://ubuntuforums.org/showthread.php?t=1136](http://ubuntuforums.org/showthread.php?t=1136)
[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)
[http://ubuntuforums.org/showthread.php?t=1129145](http://ubuntuforums.org/showthread.php?t=1129145)
If any further information is needed I will be more than happy to provide it - that is if I know how to get it since I have been using Ubuntu for two days so far (:  . I don't know if that have anything to do with this but when I installed Ubuntu at some point my monitor goes blank (but it's still on) and I had to change manually from analog to digital (or from digital to analog it doesn't matter I just need to switch between these two) from the monitor menu. I have to do the same thing on login screen everytime to make the monitor actually displaying the login screen.
I am looking forward to any suggestions (about the sound problem - I don't care about the monitor issue that much (: )
Miro Marinov

---

### Post by Fendro on 2010-01-18
Bump.

---

### Post by ChukG on 2010-02-10
I have the exact same problem and no solution. :-(

---

### Post by drauchomyn on 2010-02-21
I have the a nearly identical setup and similar problems. Almost everything Fendro posted is identical to my output. I've installed 9.10 and the best I can do is get poor quality pulsating distorted sound.   Playing around with alsamixer sort of helps, but the problem is still there.

I enabled sound by going to System->Preferences->Sound and choosing the Hardware tab. By default, Analog Stereo Output was the default sound profile.  I changed this to any of the Analog Surround outputs (4.0, 4.1, 5.1, etc.) and the sound began to work, but with crappy quality as mentioned above.

In addition, in alsamixer the following switches must be unmuted in order for sound to work: Master, PCM, Surround, Center, LFE.

running sudo aplay -l:

```

**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```I followed the instructions posted here: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

In the section "Is Alsa Using the Correct Model?" I figured out my chipset.  Here is the important bit:

```

!!Loaded sound module options
!!--------------------------

!!Module: snd_intel8x0
    ac97_clock : 0
    ac97_quirk : <NULL>
    buggy_irq : Y
    buggy_semaphore : N
    enable : N
    id : <NULL>
    index : -1
    joystick : 0
    spdif_aclink : 0
    xbox : N

!!Module: snd_mpu401
    enable : Y,N,N,N,N,N,N,N
    id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    index : -2,-2,-2,-2,-2,-2,-2,-2
    irq : 10,65535,65535,65535,65535,65535,65535,65535
    pnp : Y,Y,Y,Y,Y,Y,Y,Y
    port : 816,1,1,1,1,1,1,1
    uart_enter : Y,Y,Y,Y,Y,Y,Y,Y


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: Realtek ALC650F

```And here is what ALSA-configuration.txt from the git repository has to say about this:

```

Module snd-intel8x0
-------------------

Module for AC'97 motherboards from Intel and compatibles.
* Intel i810/810E, i815, i820, i830, i84x, MX440
ICH5, ICH6, ICH7, 6300ESB, ESB2
* SiS 7012 (SiS 735)
* NVidia NForce, NForce2, NForce3, MCP04, CK804
CK8, CK8S, MCP501
* AMD AMD768, AMD8111
* ALi m5455


ac97_clock    - AC'97 codec clock base (0 = auto-detect)
ac97_quirk    - AC'97 workaround for strange hardware
See "AC97 Quirk Option" section below.
buggy_irq     - Enable workaround for buggy interrupts on some
motherboards (default yes on nForce chips,
otherwise off)
buggy_semaphore - Enable workaround for hardwares with buggy
semaphores (e.g. on some ASUS laptops) 
(default off)
spdif_aclink  - Use S/PDIF over AC-link instead of direct connection
from the controller chip

(0 = off, 1 = on, -1 = default)

This module supports one chip and autoprobe.

Note: the latest driver supports auto-detection of chip clock.
if you still encounter too fast playback, specify the clock
explicitly via the module option "ac97_clock=41194".

Joystick/MIDI ports are not supported by this driver.  If your
motherboard has these devices, use the ns558 or snd-mpu401
modules, respectively.

The power-management is supported.

```Note the part about ac97_quirk, which is <NULL> in my snd_intel8x0 module. 

Also note that I have a Realtek ALC650F written under my AC97 codec information.

 In the ALSA config file, it says "ac97_quirk  - AC'97 workaround for strange hardware."

Here is what the "See "AC97 Quirk Option" says in thre git file repository:

```

AC97 Quirk Option

=================

The ac97_quirk option is used to enable/override the workaround for
specific devices on drivers for on-board AC'97 controllers like
snd-intel8x0.  Some hardware have swapped output pins between Master
and Headphone, or Surround (thanks to confusion of AC'97
specifications from version to version :-) 

The driver provides the auto-detection of known problematic devices,
but some might be unknown or wrongly detected.  In such a case, pass
the proper value with this option. 

The following strings are accepted:
     - default   Don't override the default setting
     - none      Disable the quirk
     - hp_only   Bind Master and Headphone controls as a single control
     - swap_hp   Swap headphone and master controls
     - swap_surround  Swap master and surround controls
     - ad_sharing  For AD1985, turn on OMS bit and use headphone
     - alc_jack  For ALC65x, turn on the jack sense mode
     - inv_eapd  Inverted EAPD implementation
     - mute_led  Bind EAPD bit for turning on/off mute LED

For backward compatibility, the corresponding integer value -1, 0,
... are  accepted, too.

For example, if "Master" volume control has no effect on your device
but only "Headphone" does, pass ac97_quirk=hp_only module option.

```For alc_jack it says: "For ALC65x, turn on the jack sense mode", and I have ALC650F.
Does this need to be turned on to help fix my problems??

Does anyone have any idea if any of these things I posted are related to my/our sound problems? If so, how would I/we go about fixing the problem?

Please help us out. This issue has also caused many hours of googling and no positive results.

---

### Post by Stackebrandt68 on 2010-02-22
First: Sorry for my poor english. My suggestion is to try it with Kubuntu. There is an application named KMix implemented and it works fine with my nforce2 Board (Epox 8rda3+). With the Ubuntu 9.10 distribution i got the same problems - poor sound in playing music and games. Maybe you can give it a try...

---

### Post by drauchomyn on 2010-02-22
But it should work for both operating systems.  I don't know how KDE would change things.

Any ideas?

---

### Post by Stackebrandt68 on 2010-02-22
Now I checked the sound modules and received my ALSA Information Script - it's all identical to your attachments. Only I can see a lot more N and <NULL> on my !!Module: snd_mpu401, but I can't imagine that's the important thing. Sorry - I think my informations are for no use.

---

### Post by drauchomyn on 2010-02-24
It turns out that I was on the right track and finally have a solution.   : )

Thanks to the Comprehensive Sound Problem forum ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)), the fix was very quick and easy. You can look at this post or look near the bottom of the first post in Comprehensive Sound Problem forum for "[SIZE=2]**webbca01** figured out how to get AC'97[/SIZE] work with the help of..."

This was done after a fresh install of 9.10 before anything else so I am confident that this is the root of the problem.

1) I had to change my device to "Analog Surround 4.0 Output" in Sound Preferences (in the "Hardware" tab). I think this may vary depending on the type of speakers you have plugged in to your computer, but the only ones that work start with "Analog Surround". All of the others don't work.

2) Ensure that the following channels are unmuted in alsamixer: Master, PCM, Surround, Center, LFE.

3) Follow the instructions as outlined by webbca01:

```

sudo nano /etc/modprobe.d/alsa-base

```Then add this line (do not worry if the file is empty):

```

options snd-intel8x0 ac97_quirk=3

```4) Reboot your computer.

That's it!  My sound works great now.

---

### Post by grouchyolddude on 2010-03-22
My audio quit several updates back in 9.04. I've been searching trying every "fix" I can find for a few weeks.
> **** List of PLAYBACK Hardware Devices ****
card 0: CK8 [NVidia CK8], device 0: Intel ICH [NVidia CK8]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8 [NVidia CK8], device 2: Intel ICH - IEC958 [NVidia CK8 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


my sound preference in systems is set to (oss) from the drop down menu. Either . OSS open sound system or nvidia ck8 with alc 658d NVidia CK8(oss) "test" seems to work there. But "nothing" alsa or "nvidia ck8 with alc 658d NVidia CK8(alsa) test work.

> 
apt-get purge pulseaudio
fixed the flash plugin sound in firefox, but now I have no audio in the movie player.
Reinstalled pulseaudio and now the sound and video in flash plugin(firefox) is choppy and distorted and the movie player, kaffiene no longer has audio ..
Sound preferences are set to oss in system.all volumes on the alsa mixer are up in the red. 
results of sudo lshw -C sound

> 
*-multimedia
description: Multimedia audio controller
product: MCP2S AC'97 Audio Controller
vendor: nVidia Corporation
physical id: 6
bus info: pci@0000:00:06.0
version: a1
width: 32 bits
clock: 66MHz
capabilities: pm bus_master cap_list
configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0 
ran sudo apt-get update and rebooted.. It appears I'm right back at square one.. no flash audio, but movie player, ect are back to working normal

then I tried this...
> Getting the ALSA drivers from a *fresh* kernel

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

A faster way, is to just remove the problematic packages and reinstall them cleanly.

(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils
[LIST][*]
VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm ubuntu-desktop
still no audio

---

### Post by grouchyolddude on 2010-03-22
> sudo apt-get remove pulseaudio
then 
> sudo apt-get install esound
reboot ..
fixed the issue entirely..

---

### Post by dwpbike on 2010-07-01
> **drauchomyn said:**
> It turns out that I was on the right track and finally have a solution.   : )

Thanks to the Comprehensive Sound Problem forum ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)), the fix was very quick and easy. You can look at this post or look near the bottom of the first post in Comprehensive Sound Problem forum for "[SIZE=2]**webbca01** figured out how to get AC'97[/SIZE] work with the help of..."

This was done after a fresh install of 9.10 before anything else so I am confident that this is the root of the problem.

1) I had to change my device to "Analog Surround 4.0 Output" in Sound Preferences (in the "Hardware" tab). I think this may vary depending on the type of speakers you have plugged in to your computer, but the only ones that work start with "Analog Surround". All of the others don't work.

2) Ensure that the following channels are unmuted in alsamixer: Master, PCM, Surround, Center, LFE.

3) Follow the instructions as outlined by webbca01:

```

sudo nano /etc/modprobe.d/alsa-base

```Then add this line (do not worry if the file is empty):

```

options snd-intel8x0 ac97_quirk=3

```4) Reboot your computer.

That's it!  My sound works great now.

this is the second time i've seen this "fix" mentioned.  hate to admit it, but it worked.  sorta.  can't go with "great", but i can listen to kingsley now.  isn't that what it's all about?

---

