---
title: "No sound EPOX EP-9NPAJ Motherboard"
date: 2008-10-14
forum: Multimedia Software
---

### Post by c.pergiel on 2008-10-14
No sound EPOX EP-9NPAJ Motherboard

I've been going round and round with this for awhile now. I've found lots of advice for laptops, and additional sound cards, but none that seem to apply to my situation.

I am using the integrated sound card on the motherboard. This thing has six ports for standard mini-stereo plugs on the motherboard back panel:
- blue
- lime green <- speakers plugged in here.
- pink
- gray
- black
- orange

Ubuntu 8.04 latest updates as of today, Monday October 13, 2008

I did found one post that suggested adding this line 

	# Test option suggestion from Ubuntu forum.
	options snd-hda-intel model=hp

to this file: /etc/modprobe.d/alsa-base
It did not help.


============================================================================================

I found numerous requests for additional information about the problem system. This is a list of commands I executed. The results follow.

cat /etc/modprobe.d/alsa-base
cat /proc/asound/version
cat /proc/asound/cards
cat /proc/asound/devices
cat /proc/asound/card0/codec97#0/ac97#0-0
cat /proc/asound/card0/codec97#0/ac97#0-0+regs
lsmod | grep "snd"
lspci
aplay -l
sudo lshw -C multimedia

============================================================================================

ccp@ccp-ubuntu:~$ cat /etc/modprobe.d/alsa-base
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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }

# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

============================================================================================

ccp@ccp-ubuntu:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Jun 18 2008 for kernel 2.6.24-19-generic (SMP).

============================================================================================

ccp@ccp-ubuntu:~$ cat /proc/asound/cards
 0 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at irq 17

============================================================================================

ccp@ccp-ubuntu:~$ cat /proc/asound/devices
  0: [ 0]   : control
  1:        : sequencer
 16: [ 0- 0]: digital audio playback
 18: [ 0- 2]: digital audio playback
 24: [ 0- 0]: digital audio capture
 25: [ 0- 1]: digital audio capture
 33:        : timer

============================================================================================

ccp@ccp-ubuntu:~$ cat /proc/asound/card0/codec97#0/ac97#0-0
0-0/0: Realtek ALC850 rev 0

PCI Subsys Vendor: 0x1695
PCI Subsys Device: 0x1011

Revision         : 0x00
Compat. Class    : 0x00
Subsys. Vendor ID: 0xffff
Subsys. ID       : 0xffff

Capabilities     :
DAC resolution   : 16-bit
ADC resolution   : 16-bit
3D enhancement   : No 3D Stereo Enhancement

Current setup
Mic gain         : +0dB [+0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Double rate slots: 7/8
Extended ID      : codec=0 rev=2 LDAC SDAC CDAC DSA=0 SPDIF DRA
Extended status  : SPCV LDAC SDAC CDAC SPDIF=3/4
SPDIF Control    : Consumer PCM Category=0x2 Generation=1 Rate=48kHz

============================================================================================

ccp@ccp-ubuntu:~$ cat /proc/asound/card0/codec97#0/ac97#0-0+regs
0:00 = 0000
0:02 = 0909
0:04 = 0000
0:06 = 0006
0:08 = 0000
0:0a = 801e
0:0c = 801f
0:0e = 801f
0:10 = 9f1f
0:12 = 0606
0:14 = 0000
0:16 = 9f1f
0:18 = 0606
0:1a = 0000
0:1c = 0000
0:1e = 0000
0:20 = 0400
0:22 = 0000
0:24 = 0000
0:26 = 800f
0:28 = 09c6
0:2a = 05c0
0:2c = bb80
0:2e = bb80
0:30 = bb80
0:32 = bb80
0:34 = 0000
0:36 = 9f80
0:38 = 9f9f
0:3a = 2824
0:3c = 0000
0:3e = 0000
0:40 = 0000
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0000
0:4e = 0000
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = 0000
0:58 = 0000
0:5a = 0000
0:5c = 0000
0:5e = 0000
0:60 = 0000
0:62 = 0000
0:64 = 0808
0:66 = 0808
0:68 = 0a0a
0:6a = 8000
0:6c = 0000
0:6e = 0017
0:70 = c5a0
0:72 = 00c0
0:74 = 8388
0:76 = 8a90
0:78 = 148e
0:7a = 20d2
0:7c = 414c
0:7e = 4790

============================================================================================

ccp@ccp-ubuntu:~$ lsmod | grep "snd"
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm

============================================================================================

ccp@ccp-ubuntu:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

============================================================================================

ccp@ccp-ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

============================================================================================

ccp@ccp-ubuntu:~$ sudo lshw -C multimedia
  *-multimedia            
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0

============================================================================================
END of Terminal Command Results.
============================================================================================

---

### Post by markbuntu on 2008-10-14
Well that is pretty confusing.

According to this, you should be using snd_hda_intel because the ALC850 is an Intel HDA chip:

```

ccp@ccp-ubuntu:~$ cat /proc/asound/cards
0 [CK804 ]: NFORCE - NVidia CK804
NVidia CK804 with ALC850 at irq 17

```

But according to everything else you should be using one of the AC '97 drivers snd-intel8x0m which should be the correct driver for your sound chip.

The green connector is supposed to be the line out. If you are using powered speakers that should work. Do you have some headphones you can try in the headphone jack?

---

