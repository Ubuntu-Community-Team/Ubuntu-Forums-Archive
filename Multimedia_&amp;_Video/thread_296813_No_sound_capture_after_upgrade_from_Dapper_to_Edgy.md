---
title: "No sound capture after upgrade from Dapper to Edgy"
date: 2006-11-10
forum: Multimedia &amp; Video
---

### Post by KeithUK on 2006-11-10
I have recently upgraded from Dapper to Edgy. Everything went fine except that sound capture has stopped working.

I have a Creative SBLive 5.1 sound card.

I have been using Audacity under Dapper to record and it worked fine.

Audio output is fine, excellent in fact, but I cannot capture audio now under Edgy.

I have tried different recording apps and none of those work either.

I have tried twiddling all the settings in the mixer and also tried using different mixer apps in case it was the mixer app, still no joy.

I know the card is ok because I dual boot with Windows XP and recording works fine under XP.

Here is the output from aadebug...

> ALSA Audio Debug v0.1.0 - Thu Nov  9 21:30:50 GMT 2006
[http://alsa.opensrc.org/index.php?page=aadebug](http://alsa.opensrc.org/index.php?page=aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux watson 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_emu10k1_synth       8960  0 
snd_emux_synth         39296  1 snd_emu10k1_synth
snd_seq_virmidi         8576  1 snd_emux_synth
snd_seq_midi_emul       8192  1 snd_emux_synth
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_seq_midi_event      8960  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                59120  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           128288  2 snd_emu10k1_synth
snd_rawmidi            27264  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_ac97_codec         97696  1 snd_emu10k1
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_seq_device          9868  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_timer              25348  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         11400  2 snd_emu10k1,snd_pcm
snd_util_mem            6016  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10756  2 snd_emux_synth,snd_emu10k1
snd                    58372  15 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.12rc1 (Thu Jun 22 13:55:50 2006 UTC).
 0 [Live           ]: EMU10K1 - SBLive 5.1 [SB0060]
                      SBLive 5.1 [SB0060] (rev.7, serial:0x80611102) at 0xb000, irq 11
  2:        : timer
  3: [ 0- 0]: hardware dependent
  4: [ 0- 0]: raw midi
  5: [ 0- 3]: digital audio playback
  6: [ 0- 2]: digital audio playback
  7: [ 0- 2]: digital audio capture
  8: [ 0- 1]: digital audio capture
  9: [ 0- 0]: digital audio playback
 10: [ 0- 0]: digital audio capture
 11: [ 0]   : control
 12:        : sequencer
 13: [ 0- 2]: hardware dependent
 14: [ 0- 1]: raw midi
 15: [ 0- 2]: raw midi
00-00: EMU10K1 (FX8010)
00-02: Emux WaveTable
00-03: emu10k1 : Multichannel Playback : playback 1
00-02: emu10k1 efx : Multichannel Capture/PT Playback : playback 8 : capture 1
00-01: emu10k1 mic : Mic Capture : capture 1
00-00: emu10k1 : ADC Capture/Standard PCM Playback : playback 32 : capture 1
Client info
  cur  clients : 5
  peak clients : 5
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
    Connecting To: 15:0
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
Client  15 : "OSS sequencer" [Kernel]
  Port   0 : "Receiver" (-we-)
    Connected From: 0:1
Client  16 : "SBLive 5.1 [SB0060]" [Kernel]
  Port   0 : "EMU10K1 MPU-401 (UART)" (RWeX)
Client  17 : "Emu10k1 WaveTable" [Kernel]
  Port   0 : "Emu10k1 Port 0" (-We-)
  Port   1 : "Emu10k1 Port 1" (-We-)
  Port   2 : "Emu10k1 Port 2" (-We-)
  Port   3 : "Emu10k1 Port 3" (-We-)

Dev Snd ---------------------------------------------------
controlC0  hwC0D2    midiC0D1  pcmC0D0c  pcmC0D1c  pcmC0D2p  seq
hwC0D0	   midiC0D0  midiC0D2  pcmC0D0p  pcmC0D2c  pcmC0D3p  timer

CPU -------------------------------------------------------
model name	: AMD Athlon(tm) Processor
cpu MHz		: 1343.272

RAM -------------------------------------------------------
MemTotal:       515868 kB
SwapTotal:     1052216 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: ALi Corporation M1647 Northbridge [MAGiK 1 / MobileMAGiK 1] (rev 04)
00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)


I know it was a bit naughty but I even tried installing alsa-utils 1.0.13 from Debian testing and running alsaconf in the hope that it would cure and config glitches.

But that didn't help either :(  

I suspect this is either an ALSA config issue or possibly a kernel option that's been missed.

Can anyone think of other things I could try before I raise this as a bug?

---

### Post by KeithUK on 2006-11-14
:D 

fixed it!!

after reading other posts I tried one of the other alsa mixer apps and noticed that the list of sound devices (front, read, tone, capture, etc. ) was different.

I also saw that people have cured a number of gnome legacy upgrade problems simply by deleting the config files gnome stores in their home directories.

So I deleted;

~/.gconf/apps/gnome-volume-control
~/.gnome2/accels/gnome-volume-control
~/.gnome2/gnome-volume-control

and got a slightly different list when I right clicked on the sound icon and chose Open Volume Control.

5 minutes fiddling with the settings and everything burst into life.

A similar exercise also fixed a problem I had with starting Rhythmbox.

Possibly a trick worth remembering if there are problems following an upgrade of Gnome or a Gnome app.

---

