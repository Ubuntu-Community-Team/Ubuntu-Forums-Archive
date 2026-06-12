---
title: "SiS SI7012 with AD1888 at irq 18"
date: 2010-10-29
forum: Multimedia Software
---

### Post by theas on 2010-10-29
Hi,

My system: ECS GS7610
           CPU: amd64 Sempron(tm) 3400+
           RAM: 2GB DDR1
           Chipset: SiS761GX Northbridge and SiS965L Southbridge
           Bios: AMI date 11/09/07
           videocard: NnVidia Geforce 6200 LE
           videocapture: Hauppauge WinTV PVR-150 [cx26xxx]
           soundcard [internal]: Si7012 with AD1888, AC'97 codec
           three harddisks [870GB]

In fact this is a multiboot system [Grub1 as bootloader on first MBR]. Sound is working well on the windows platform [xp], using an external amplifier [via lineout]. On the system is also installed OpenSuse11.3 with Gnome-desktop, and sound is working well.
Earlier i had installed Ubuntuu 9.04 and sound was working well toooo, but since upgrading to 9.10 II've lost sound on the Ubuntu platform. I've checked the configuration and compared with other distros, but everything seems to be ok, sofar as i know of. However, the output of "dmesg" misses an entry pointing to the builtin [motherboard] soundcard [SI7012], only showing the entry pointing to the soundmodule of the Hauppauge TV-card. This is confirmed by the Gnome-desktop: Preferences > sound, the hardware tab is empty! On the other hand, in the hardware-applet, the Si7012 is fully recognized!! So this is a bit strange?
I've included here the output of some commands entered in the commandline-console. [BTW, I am puzzled by the lines "Capabilities: <access denied>", indicating what exactly? I am also worried about the fact that the swapfile (2GB) remains empty, only RAM is used, so that the system locks up when i've opened some more files, including firefox.]
I wonder if someone can give me some hints please, for i am stuck now, after several weeks of searching, probing, etc. the Ubuntu forum.
============================================================

mediaw@ubuntu9:~$ lsmod -v | less
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: Elitegroup Computer Systems Device 1880
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at e800 [size=256]
        I/O ports at e400 [size=128]
        Capabilities: <access denied>
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0

mediaw@ubuntu9:~$ lsmod | grep snd_intel8x0
snd_intel8x0           36872  0 
snd_ac97_codec        125720  1 snd_intel8x0
snd_pcm                93160  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    77096  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         10928  2 snd_intel8x0,snd_pcm
mediaw@ubuntu9:~$ 

mediaw@ubuntu9:~$ lsmod
Module                  Size  Used by
.......................................
......................................
tda9887                11780  1 
tda8290                15748  0 
tuner                  24520  2 
cx25840                29588  1 
snd_intel8x0           36872  0 
snd_ac97_codec        125720  1 snd_intel8x0
ac97_bus                2176  1 snd_ac97_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
iptable_filter          3872  0 
ppdev                   8232  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
...............................................
snd_seq_dummy           3460  0 
shpchp                 37756  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27296  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_intel8x0,snd_pcm
parport_pc             37352  1 
.............................................


/proc/asound/cards:
 0 [SI7012         ]: ICH - SiS SI7012
                      SiS SI7012 with AD1888 at irq 18

ID: Si70121
Alsa versie: 1.0.20

/proc/asound/modules:
 0 snd_intel8x0

/proc/asound/card0/intel8x0:
Intel8x0

Global control        : 0x00000002
Global status         : 0x00300100
AC'97 codecs ready    : primary
AC'97 codecs SDIN     : 0 0 0


mediaw@ubuntu9:~$ less .asoundrc.asoundconf
/home/mediaw/.asoundrc.asoundconf:
# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card AudioPCI
defaults.ctl.card AudioPCI
defaults.pcm.device 0
defaults.pcm.subdevice -1

/proc/asound/card0/codec97#0/ac97#0-0:
0-0/0: Analog Devices AD1888

PCI Subsys Vendor: 0x1019
PCI Subsys Device: 0x1880

Flags: 30
Capabilities     : -headphone out-
DAC resolution   : 20-bit
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
Double rate slots: 10/11
Extended ID      : codec=0 rev=0 AMAP LDAC SDAC CDAC DSA=0 SPDIF DRA VRA
Extended status  : SPCV LDAC SDAC CDAC SPDIF=3/4 VRA

=======================================================   

Thanks in advance!
Theas

---

