---
title: "Mythbuntu sound problem"
date: 2008-02-13
forum: Multimedia &amp; Video
---

### Post by x-dragon on 2008-02-13
Here is the problem, when I use the frontend on the machine where the backend is located, I get no sound at all. When I try to play a MP3 with XMMS, I get about half a second of sound, then that part of the sound is repeated about 4 to 5 times and then it dies, no more sound. 
Below is the output of a script I found on the alsa troubleshoot page: (if it means anything to you guys)
But, when I use a frontend on a different machine, I DO get sound (I don't know if that's related, but I thought I'd add it here just in case)

xdragon@mythtv:~$ ./aadebug (link: [http://alsa.opensrc.org/index.php/Aadebug](http://alsa.opensrc.org/index.php/Aadebug) )
./aadebug: line 2: ALSA Audio Debug v0.1.0 - Wed Feb 13 08:54:41 CET 2008: command not found
[http://alsa.opensrc.org/aadebug](http://alsa.opensrc.org/aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux mythtv 2.6.22-14-generic #1 SMP Fri Feb 1 04:59:50 UTC 2008 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_intel8x0           34972  0
snd_ac97_codec        100644  1 snd_intel8x0
snd_pcm_oss            44672  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            33152  0
snd_seq_midi            9600  0
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC).
 0 [I82801BAICH2   ]: ICH - Intel 82801BA-ICH2
                      Intel 82801BA-ICH2 with AD1885 at irq 17
  2:        : timer
  3:        : sequencer
  4: [ 0- 1]: digital audio capture
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0]   : control
cat: /proc/asound/hwdep: No such file or directory
00-01: Intel ICH - MIC ADC : Intel 82801BA-ICH2 - MIC ADC : capture 1
00-00: Intel ICH : Intel 82801BA-ICH2 : playback 1 : capture 1
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
controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1c  seq  timer

CPU -------------------------------------------------------
model name      : Intel(R) Pentium(R) 4 CPU 1.70GHz
cpu MHz         : 1694.581

RAM -------------------------------------------------------
MemTotal:       515360 kB
SwapTotal:     1510068 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 12)
03:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
03:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

The alsa mixer => everything is set to 'open' as in 'not -muted' except:
Mic = Muted
Digital = Muted
Zero Fill Dac = Muted

Any help is appreciated...

---

### Post by x-dragon on 2008-02-14
No one ?

---

