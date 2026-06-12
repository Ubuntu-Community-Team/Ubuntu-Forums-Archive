---
title: "No Sound in Ubuntu 8.0.4"
date: 2008-05-27
forum: Multimedia Software
---

### Post by yamuna on 2008-05-27
Hi,
I am very new to Ubuntu. I have few issues with sound in my system. I am not able to hear any sounds in System->Preferences->Sounds and trying to play any mps3s just hangs the application. I have attached the sound configuration of my system generated using aadebug. Any help with this problem is greatly appreciated.

Thanks,
Yamuna

---

### Post by lisati on 2008-05-27
I couldn't see your attachment of your specs. What is sometimes helpful for the forum includes what sort of computer you're using and what kind of sound card you have.

---

### Post by yamuna on 2008-05-27
I have included below the output of the aadebug.log

ALSA Audio Debug v0.1.0 - Tue May 27 13:06:17 IST 2008
[http://alsa.opensrc.org/aadebug](http://alsa.opensrc.org/aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux yamuna-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_hda_intel         344728  5
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Apr 21 2008 for kernel 2.6.24-16-generic (SMP).
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd0200000 irq 21
  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 24: [ 0- 0]: digital audio capture
 33:        : timer
00-00: HDA Codec 0
00-01: AD198x Digital : AD198x Digital : playback 1
00-00: AD198x Analog : AD198x Analog : playback 1 : capture 1
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
controlC0  hwC0D0  pcmC0D0c  pcmC0D0p  pcmC0D1p  seq  timer

CPU -------------------------------------------------------
model name      : Intel(R) Pentium(R) D CPU 3.00GHz
cpu MHz         : 1200.000
model name      : Intel(R) Pentium(R) D CPU 3.00GHz
cpu MHz         : 1200.000

RAM -------------------------------------------------------
MemTotal:      1025748 kB
SwapTotal:      497972 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: Intel Corporation 82946GZ/PL/GL Memory Controller Hub (rev 02)

Thanks,
Yamuna

---

### Post by yamuna on 2008-05-27
The problem with playing sounds has now been resolved after I have changed the settings in Sounds under System->Administration and installing ubuntu restricted extras. But the sounds played over the net are now distorted and I( cant listen to anything properly. Could this be because I changed the alsamixer settings? Could someone please tell me what I am to do?

Thanks,
Yamuna

---

