---
title: "Audigy/Jack/Ardour issues"
date: 2006-11-02
forum: Multimedia &amp; Video
---

### Post by twiddle87 on 2006-11-02
Hi all,
I recently installed an Audigy LS Soundcard with the intention of doing some 5.1 mixing using Ardour. I dont seem to be able to get anything other than stereo out of my speakers (that is, stereo upmixed to all the speakers). I looked at qjackctl and I appear to only have 2 alsa_pcm devices. Presumably they correspond to stereo left and right. Is there any way i can reconfigure Alsa/Jack to pick up the other 4 outputs and create the pcm devices so i can route Ardour's output to them? Or any other ideas how i can get the correct output in each speaker?

Heres my AADebug output:

ALSA Audio Debug v0.1.0 - Sat Nov  4 07:30:04 EST 2006
[http://alsa.opensrc.org/index.php?page=aadebug](http://alsa.opensrc.org/index.php?page=aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux c083821 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_rtctimer            3340  0 
snd_seq_dummy           3844  0 
snd_seq_oss            33536  0 
snd_seq_midi            9376  0 
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_ca0106             34212  0 
snd_via82xx            28824  2 
snd_ac97_codec         93216  2 snd_ca0106,snd_via82xx
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0 
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  5 snd_ca0106,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  3 snd_rtctimer,snd_seq,snd_pcm
snd_page_alloc         10632  3 snd_ca0106,snd_via82xx,snd_pcm
snd_mpu401_uart         7808  1 snd_via82xx
snd_rawmidi            25504  3 snd_seq_midi,snd_ca0106,snd_mpu401_uart
snd_seq_device          8716  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    55268  15 snd_seq_oss,snd_seq,snd_ca0106,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).
0 [rev50          ]: VIA686A - VIA 82C686A/B rev50
                     VIA 82C686A/B rev50 with STAC9721,23 at 0xcc00, irq 11
1 [CA0106         ]: CA0106 - CA0106
                     Audigy SE [SB0570] at 0xe800 irq 12
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
  1:       : sequencer
 33:       : timer
 40: [1- 0]: raw midi
 51: [1- 3]: digital audio playback
 59: [1- 3]: digital audio capture
 50: [1- 2]: digital audio playback
 58: [1- 2]: digital audio capture
 49: [1- 1]: digital audio playback
 57: [1- 1]: digital audio capture
 48: [1- 0]: digital audio playback
 56: [1- 0]: digital audio capture
 32: [1- 0]: ctl
00-00: VIA 82C686A/B rev50 : VIA 82C686A/B rev50 : playback 1 : capture 1
01-00: ca0106 : CA0106 : playback 1 : capture 1
01-01: ca0106 : CA0106 : playback 1 : capture 1
01-02: ca0106 : CA0106 : playback 1 : capture 1
01-03: ca0106 : CA0106 : playback 1 : capture 1
Client info
  cur  clients : 4
  peak clients : 4
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
    Connecting To: 63:0
Client  62 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
Client  63 : "OSS sequencer" [Kernel]
  Port   0 : "Receiver" (-we-)
    Connected From: 0:1
  Output pool :
    Pool size          : 1024
    Cells in use       : 0
    Peak cells in use  : 0
    Alloc success      : 0
    Alloc failures     : 0
Client  72 : "CA0106 MPU-401 (UART)" [Kernel]
  Port   0 : "CA0106 MPU-401 (UART)" (RWeX)

Dev Snd ---------------------------------------------------
controlC0  midiC1D0  pcmC0D0p  pcmC1D0p  pcmC1D1p  pcmC1D2p  pcmC1D3p  timer
controlC1  pcmC0D0c  pcmC1D0c  pcmC1D1c  pcmC1D2c  pcmC1D3c  seq

CPU -------------------------------------------------------
model name	: AMD Duron(tm) Processor
cpu MHz		: 747.578

RAM -------------------------------------------------------
MemTotal:       515936 kB
SwapTotal:     1502036 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
0000:00:0b.0 Multimedia audio controller: Creative Labs SB Audigy LS

thanks.

Edit: i can't even get the upmixed output any more, not through totem, not through aplay... Eeek.

---

