---
title: "No Audio"
date: 2007-02-22
forum: Multimedia &amp; Video
---

### Post by WinstonEwert on 2007-02-22
I installed a fresh installation of dapper onto my computer. However, I have no sound and I know almost nothing about unix. (I can manipulate files through the command line)

As far as I can see, it sees my AC'97 audio card and in all ways appears to be outputing to it. But, nothing comes out. (I have checked the speakers, they are not muted)

I found a script which pulls a bunch of audio settings I'm not entirely sure how it all works, but here is the output if it helps diagnose hte problem.

Thanks in advance.

winston@brandie:/$ aplay /usr/share/sounds/login.wav
Playing WAVE '/usr/share/sounds/login.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
winston@brandie:/$ cd /
winston@brandie:/$ ./aadebug
ALSA Audio Debug v0.1.0 - Thu Feb 22 13:09:28 PST 2007
[http://alsa.opensrc.org/aadebug](http://alsa.opensrc.org/aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux brandie 2.6.15-28-686 #1 SMP PREEMPT Thu Feb 1 16:14:07 UTC 2007 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_intel8x0           35772  1
snd_ac97_codec        100224  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0
snd_mixer_oss          20544  2 snd_pcm_oss
snd_pcm                96708  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd                    60004  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         11304  2 snd_intel8x0,snd_pcm

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).
0 [I440MX         ]: ICH - Intel 440MX
                     Intel 440MX with STAC9721,23 at 0x1000, irq 9
 25: [0- 1]: digital audio capture
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
 33:       : timer
cat: /proc/asound/hwdep: No such file or directory
00-00: Intel ICH : Intel 440MX : playback 1 : capture 1
00-01: Intel ICH - MIC ADC : Intel 440MX - MIC ADC : capture 1
cat: /proc/asound/seq/clients: No such file or directory

Dev Snd ---------------------------------------------------
controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1c  timer

CPU -------------------------------------------------------
model name      : Pentium III (Coppermine)
cpu MHz         : 398.325

RAM -------------------------------------------------------
MemTotal:       190788 kB
SwapTotal:      273064 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: Intel Corporation 82440MX Host Bridge (rev 01)
0000:00:00.1 Multimedia audio controller: Intel Corporation 82440MX AC'97 Audio Controller

winston@brandie:/$

---

### Post by zvacet on 2007-02-22
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by WinstonEwert on 2007-02-22
I don't think the WAV was a restricted format...

At any rate installing all of that failed to make a difference.

---

