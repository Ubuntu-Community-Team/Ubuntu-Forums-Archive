---
title: "No sound on Intrepid with Via VIA 82C686A/B rev40"
date: 2008-11-08
forum: Multimedia Software
---

### Post by Steve1961 on 2008-11-08
The title says it all.  After a clean install of Intrepid the VIA 82C686A/B rev40 onboard sound card isn't producing any sounds at all.  Here's some info:

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: rev40 [VIA 82C686A/B rev40], device 0: VIA 82C686A/B rev40 [VIA 82C686A/B rev40]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: modem [VIA 82XX modem], device 0: VIA 82XX modem [VIA 82XX modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 40)
	Subsystem: Packard Bell B.V. Device 200d
	Flags: medium devsel, IRQ 5
	I/O ports at e000 [size=256]
	I/O ports at e100 [size=4]
	I/O ports at e104 [size=4]
	Capabilities: <access denied>
	Kernel driver in use: VIA 82xx Audio
	Kernel modules: snd-via82xx

$ lsmod | grep snd
snd_via82xx            32536  1 
snd_via82xx_modem      19464  0 
gameport               19468  1 snd_via82xx
snd_ac97_codec        111652  2 snd_via82xx,snd_via82xx_modem
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_mpu401_uart        15360  1 snd_via82xx
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  14 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         16136  3 snd_via82xx,snd_via82xx_modem,snd_pcm
soundcore              15328  1 snd

I've made sure all the volume levels are at 100% in alsamixer and the sound card is enabled in the bios.  Any ideas anyone?  This worked fine when it was running Hardy.

---

