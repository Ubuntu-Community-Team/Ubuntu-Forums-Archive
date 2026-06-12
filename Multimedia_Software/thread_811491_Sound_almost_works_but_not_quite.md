---
title: "Sound almost works but not quite"
date: 2008-05-29
forum: Multimedia Software
---

### Post by hedbag on 2008-05-29
Hi

I can't get my sound working!

I'm using an internal PCI Creative Labs Live! value soundblaster 5.1 card on 64 bit Ubuntu 8.04 with an Intel Workstation Motherboard S5000XVN.

In "System -> Preferences -> Sound -> Devices", testing playback or capture with any of the emu10k1x, alsa or oss options freezes the application and plays no sound.

I was following instructions on [http://ubuntuforums.org/showthread.php?t=205449&highlight=Creative+Labs+Live](http://ubuntuforums.org/showthread.php?t=205449&highlight=Creative+Labs+Live) , 
but everything in terms of drivers being installed etc seems fine. I'm stuck at a point after those instructions.

I think there is either some problem with how this card interfaces with my motherboard or how pulseaudio interfaces with alsamixer.
...or perhaps it's something face rakingly simple!! :)


Diagnostic information:
-------------------------------------------------------------------------------

"uname -a"
Linux Tiamat 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 x86_64 GNU/Linux


Onboard snd_hda_intel sound was disabled in the BIOS.


Got ALSA drivers from a fresh kernel followed by reboot:
"sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils"
"sudo apt-get install linux-sound-base alsa-base alsa-utils"
"sudo apt-get install gdm ubuntu-desktop"


"sudo asoundconf list"
Names of available sound cards:
Live


"lspci|grep Live" 
05:01.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X


"sudo lspci -v -s 05:01.0"
05:01.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
	Subsystem: Creative Labs Unknown device 1001
	Flags: bus master, fast Back2Back, medium devsel, latency 32, IRQ 25
	I/O ports at 2000 [size=32]
	Capabilities: [dc] Power Management version 2


"lsmod|grep emu" 
snd_emu10k1x           23236  10 
snd_ac97_codec        123224  1 snd_emu10k1x
snd_pcm                92168  8 snd_emu10k1x,snd_ac97_codec,snd_pcm_oss
snd_rawmidi            29856  2 snd_emu10k1x,snd_seq_midi
snd                    70856  23 snd_emu10k1x,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         13200  2 snd_emu10k1x,snd_pcm


"lsmod|grep snd"
snd_emu10k1x           23236  10 
snd_ac97_codec        123224  1 snd_emu10k1x
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  8 snd_emu10k1x,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  2 snd_emu10k1x,snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  5 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    70856  23 snd_emu10k1x,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10400  1 snd
ac97_bus                3840  1 snd_ac97_codec
snd_page_alloc         13200  2 snd_emu10k1x,snd_pcm


"modinfo snd-emu10k1x" 
filename:       /lib/modules/2.6.24-17-generic/ubuntu/sound/alsa-driver/pci/emu10k1/snd-emu10k1x.ko
license:        GPL
description:    EMU10K1X
author:         Francisco Moraes <fmoraes@nc.rr.com>
srcversion:     AF05CE11BC7806DFC2E96BF
alias:          pci:v00001102d00000006sv*sd*bc*sc*i*
depends:        snd,snd-pcm,snd-page-alloc,snd-rawmidi,snd-ac97-codec
vermagic:       2.6.24-17-generic SMP mod_unload 
parm:           index:Index value for the EMU10K1X soundcard. (array of int)
parm:           id:ID string for the EMU10K1X soundcard. (array of charp)
parm:           enable:Enable the EMU10K1X soundcard. (array of bool)


"aplay --list-devices"
**** List of PLAYBACK Hardware Devices ****
card 0: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


"cat /proc/asound/modules"
 0 snd_emu10k1x


"cat /proc/asound/cards"
 0 [Live           ]: EMU10K1X - Dell Sound Blaster Live!
                      Dell Sound Blaster Live! at 0x2000 irq 25


"cat /proc/asound/version"
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on May  6 2008 for kernel 2.6.24-17-generic (SMP).


"grep 'audio' /etc/group"
audio:x:29:pulse,hedbag


"cat /etc/modules"
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
snd-emu10k1x


"alsamixer -c0"
Loads up fine and allows alteration of front, center and rear channels.


"aplay a.wav"
Playing WAVE 'a.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo

...but actual no sound.


...and when I got desperate:
Tried a different PCI slot for the soundcard.
Played with mute and volume settings in alsamixer.
Toggled "Analog/Digital Output Jack" in "switches" tab of "Volume Control".
Tested analog cable plugged into different output jacks.

-------------------------------------------------------------------------------

Thanks for any help or general snippets of info you can give.

---

