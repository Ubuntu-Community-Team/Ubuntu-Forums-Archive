---
title: "envy24control, M44, 10.04 and no sound"
date: 2010-05-02
forum: Multimedia Software
---

### Post by cathalcummins on 2010-05-02
Hi there, I've been having problems with my Delta 44 on 10.04. I'm getting no sound but the levels are showing up in envy24control panel - i.e if a sound is being played the meters are going up and down as normal. I disabled the onboard sound via the BIOS months back so M44 is default card 0 at the moment. The problem was after a fresh install of 10.04 - I was using KK and sound was fine (after removing pulseaudio from the system).

I was thinking, should I remove the pulseaudio folder from etc entirely?

Or has anybody any suggestions as to why the levels would show up in envy but not come through the breakout box?

Thanks in advance!!!

---

### Post by cchhrriiss121212 on 2010-05-02
I would remove it entirely. I've the same card, and pulse offers zero functionality for me as well as not working on any install I have tried.

---

### Post by lidex on 2010-05-02
And try this: Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-ice1712 model=delta44 
```
Save. Close. Reboot. 

> Alternate channel mappings needed for ICE1712

Cards such as Audiophile 2496, Delta 1010LT and others using the ICE1712 chip, there is a bug with the channel mapping.

Diagnosis

Open a terminal, then enter this command:

cat /proc/asound/cards | grep ICE1712

If you get a line specifying the name of your soundcard, you're probably affected.

Fix / workaround

See [bug #178442]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442"). 

---

### Post by cathalcummins on 2010-05-03
I removed the pulse folder and I attached the suggested line to the alsa-base.conf file. Still no go. I've attached some possibly helpful results from standard commands - apologies for the overload of information but I'm unsure which parts aren't useful.


__________________________________________________________________________________________________________

[I]>> gksudo gedit /etc/modprobe.d/alsa-base.conf

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
options snd-ice1712 model=delta44[/I]


__________________________________________________________________________________________________________

[I]>> cat /proc/asound/cards
 0 [M44            ]: ICE1712 - M Audio Delta 44
                      M Audio Delta 44 at 0xec00, irq 19[/I]
__________________________________________________________________________________________________________


[I]>> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: M44 [M Audio Delta 44], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 0/1
  Subdevice #0: subdevice #0[/I]

## **I remember that I used to have 1 subdevice before - perhaps this was the onboard sound before I disabled it?**
__________________________________________________________________________________________________________


[I]>> sudo lsmod

Module                  Size  Used by
binfmt_misc             7960  1 
snd_ice1712            66309  3 
snd_ice17xx_ak4xxx      3123  1 snd_ice1712
snd_ak4xxx_adda         8572  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              7946  1 snd_ice1712
snd_ac97_codec        125394  1 snd_ice1712
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  4 snd_ice1712,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          8500  1 snd_pcm
ac97_bus                1450  1 snd_ac97_codec
snd_i2c                 5518  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         6857  1 snd_ice1712
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
nvidia              10799466  38 
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  3 snd_pcm,snd_seq
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  1 
i2c_nforce2             6099  0 
snd                    70978  18 snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_i2c,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vgastate                9857  1 vga16fb
k8temp                  3912  0 
soundcore               8052  1 snd
amd64_edac_mod         20456  0 
edac_core              45423  3 amd64_edac_mod
ppdev                   6375  0 
edac_mce_amd            9214  1 amd64_edac_mod
parport_pc             29958  1 
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
asus_atk0110           10033  0 
usbhid                 40988  0 
hid                    83376  1 usbhid
floppy                 63156  0 
sata_nv                23778  1 
pata_amd               11962  2 
forcedeth              55592  0 [/I]

__________________________________________________________________________________________________________


[I]>> cat /proc/asound/modules
 0 snd_ice1712[/I]


__________________________________________________________________________________________________________


[I]>> sudo lshw -C sound

  *-multimedia            
       description: Multimedia audio controller
       product: ICE1712 [Envy24] PCI Multi-Channel I/O Controller
       vendor: VIA Technologies Inc.
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ICE1712 latency=64
       resources: irq:19 ioport:ec00(size=32) ioport:e880(size=16) ioport:e800(size=16) ioport:e480(size=64)[/I]

__________________________________________________________________________________________________________


[I]>> uname -a
Linux terminal38 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux[/I]


__________________________________________________________________________________________________________




[I]>> envy24control
using	 --- input_channels: 4
	 --- output_channels: 4
	 --- pcm_output_channels: 8
	 --- spdif in/out channels: 2[/I]

__________________________________________________________________________________________________________

---

### Post by WIREHEAD on 2010-05-16
I really hope we can find a solution to this soon !

Also M-audio Delta 44 worked fine before upgrade .

Also works with PCLinuxOS2010 .

I have tried way too many times to fix this :

 removed pulseaudio and installed esound - partial functionality system sounds worked - audacity also had sound .

Reinstalled pulseaudio - removed esound . ETC......

In the process I have probably totally lost any hope of salvaging this install .

BTW , booting from 10.04 CD also gives the same symptoms as the upgrade...

I may try reverting to the previous kernal if this does not resolve soon.

Good luck !

---

### Post by lidex on 2010-05-16
Did you try the work-around in the bug report thread?

---

