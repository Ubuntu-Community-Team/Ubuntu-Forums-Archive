---
title: "No sound: Ed/K/ubuntu (Breezy)+SB Live (CT4730)"
date: 2006-02-11
forum: Multimedia &amp; Video
---

### Post by brucetan on 2006-02-11
Dear all,

Have anyone got Ed/K/ubuntu Breezy working with SBLive (CT4730)?

If so, can you review my following setup and advice what gone wrong here? My sincere thanks.

PC Configuration:
===========
The PC configuration is as follows:
CPU: AMD Duron@650Mhz
Memory: 384MB
HD: IBM DLTA 30GB (IDE)
SoundCard: SB Live Value (Model CT4730, PCI)
CDRW/DVD R
Current OS: edubuntu Breezy Badger release 5.10 (but also had tried ubuntu and Kubuntu Breezy, no sound too)

I had been trying to get it to produce sound for the last 3 days but no luck -- :cry: 

The output of "cat /proc/asound/cards" is:
==========================
boon@edubuntu:~$ cat /proc/asound/cards
0 [AudioPCI ]: ENS1371 - Ensoniq AudioPCI Ensoniq AudioPCI ENS1371 at 0xa000, irq 10

The output of "lsmod | grep snd" is as follows:
===============================
boon@edubuntu:~$ lsmod | grep snd
snd_ens1371 22240 3
gameport 14472 1 snd_ens1371
snd_rawmidi 22816 1 snd_ens1371
snd_seq_device 8204 1 snd_rawmidi
snd_ac97_codec 72188 1 snd_ens1371
snd_pcm_oss 46368 0
snd_mixer_oss 16128 1 snd_pcm_oss
snd_pcm 78344 4 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer 21764 2 snd_pcm
snd 48644 12 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_co dec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore 9184 1 snd
snd_page_alloc 10120 1 snd_pcm

The output of "lspci | grep audio" is as follows:
===============================
boon@edubuntu:~$ lspci | grep audio
0000:00:0b.0 Multimedia audio controller: Creative Labs Ectiva EV1938

The output of "lsmod | grep oss" is as follows:
===============================
boon@edubuntu:~$ lsmod | grep oss
snd_pcm_oss 46368 0
snd_mixer_oss 16128 1 snd_pcm_oss
snd_pcm 78344 4 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd 48644 12 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_co dec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer

The output of "modinfo soundcore" is as follows:
===============================
boon@edubuntu:~$ modinfo soundcore
filename:       /lib/modules/2.6.12-10-386/kernel/sound/soundcore.ko
description:    Core sound module
author:         Alan Cox
license:        GPL
alias:          char-major-14-*
vermagic:       2.6.12-10-386 386 gcc-3.4
depends:
srcversion:     E11490DC3F523551C4C2A6D


The output of "modinfo snd-emu10k1" is as follows:
===============================
boon@edubuntu:~$ modinfo snd-emu10k1
filename:       /lib/modules/2.6.12-10-386/kernel/sound/pci/emu10k1/snd-emu10k1. ko
author:         Jaroslav Kysela <perex@suse.cz>
description:    EMU10K1
license:        GPL
vermagic:       2.6.12-10-386 386 gcc-3.4
depends:        snd-pcm,snd-ac97-codec,snd-util-mem,snd-page-alloc,snd-rawmidi,s nd,snd-timer,snd-hwdep,snd-seq-device
alias:          pci:v00001102d00000002sv*sd*bc*sc*i*
alias:          pci:v00001102d00000004sv*sd*bc*sc*i*
alias:          pci:v00001102d00000008sv*sd*bc*sc*i*
srcversion:     199C72359A21FF71F5FC884
parm:           enable_ir:Enable IR. (array of bool)
parm:           max_buffer_size:Maximum sample buffer size in MB. (array of int)
parm:           max_synth_voices:Maximum number of voices for WaveTable. (array of int)
parm:           seq_ports:Allocated sequencer ports for internal synthesizer. (a rray of int)
parm:           extout:Available external outputs for FX8010. Zero=default. (arr ay of int)
parm:           extin:Available external inputs for FX8010. Zero=default. (array  of int)
parm:           enable:Enable the EMU10K1 soundcard. (array of bool)
parm:           id:ID string for the EMU10K1 soundcard. (array of charp)
parm:           index:Index value for the EMU10K1 soundcard. (array of int)


The output of "modinfo snd-ens1371" is as follows:
===============================
boon@edubuntu:~$ modinfo snd-ens1371
filename:       /lib/modules/2.6.12-10-386/kernel/sound/pci/snd-ens1371.ko
author:         Jaroslav Kysela <perex@suse.cz>, Thomas Sailer <sailer@ife.ee.ethz.ch>
license:        GPL
description:    Ensoniq/Creative AudioPCI ES1371+
vermagic:       2.6.12-10-386 386 gcc-3.4
depends:        snd-pcm,snd-rawmidi,snd,gameport,snd-ac97-codec
alias:          pci:v00001274d00001371sv*sd*bc*sc*i*
alias:          pci:v00001274d00005880sv*sd*bc*sc*i*
alias:          pci:v00001102d00008938sv*sd*bc*sc*i*
srcversion:     D3D8CC5AD67BB5BCEE48E2D
parm:           joystick_port:Joystick port address. (array of int)
parm:           enable:Enable Ensoniq AudioPCI soundcard. (array of bool)
parm:           id:ID string for Ensoniq AudioPCI soundcard. (array of charp)
parm:           index:Index value for Ensoniq AudioPCI soundcard. (array of int)

---

### Post by brucetan on 2006-02-13
It is fixed now.  Please see thread: [http://ubuntuforums.org/showthread.php?t=126975&page=5]("http://ubuntuforums.org/showthread.php?t=126975&page=5")
Many thanks to Fareast.

---

