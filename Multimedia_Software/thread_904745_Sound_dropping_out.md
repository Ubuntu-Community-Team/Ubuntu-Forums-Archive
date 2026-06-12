---
title: "Sound dropping out"
date: 2008-08-29
forum: Multimedia Software
---

### Post by Deebster on 2008-08-29
I'm running Mythbuntu (just reinstalled with 8.04.1, but this issue was around before) and have been having issues with sound dropping out for under a second quite frequently.

Is there some way to turn on extra debugging so I can see what's causing it?

Some stuff:
ALSA Audio Debug v0.1.0 - Fri Aug 29 20:38:45 BST 2008
[http://alsa.opensrc.org/aadebug](http://alsa.opensrc.org/aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux bernie 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_via82xx            29464  2 
snd_ac97_codec        101028  1 snd_via82xx
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  4 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9728  1 snd_via82xx
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  15 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Jun 18 2008 for kernel 2.6.24-19-generic (SMP).
 0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with VIA1617A at 0xe000, irq 12
  0: [ 0]   : control
  1:        : sequencer
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 24: [ 0- 0]: digital audio capture
 25: [ 0- 1]: digital audio capture
 33:        : timer
00-01: VIA 8237 : VIA 8237 : playback 1 : capture 1
00-00: VIA 8237 : VIA 8237 : playback 4 : capture 1
Client info
  cur  clients : 3
  peak clients : 3
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

Dev Snd ---------------------------------------------------
controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1c  pcmC0D1p  seq	timer

CPU -------------------------------------------------------
model name	: VIA Nehemiah
cpu MHz		: 798.000

RAM -------------------------------------------------------
MemTotal:       970340 kB
SwapTotal:     2000084 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

---

