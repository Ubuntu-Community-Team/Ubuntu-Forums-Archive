---
title: "Can't get mp3s in ubuntu server to play"
date: 2010-01-11
forum: Multimedia Software
---

### Post by Buce on 2010-01-11
I'm trying to get mp3s to play in Ubuntu Server, Hardy Heron. I tried installing most of the packages from [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683"), avoiding the GUI ones, but when I try to play mp3s, I get static or a weird scratching noise. The ouput of aplay is something like

```
aplay path/to/file.mp3
Playing raw data 'path/to/file.mp3' : Unsigned 8 bit, Rate 8000 Hz, Mono
```

Any typos in these commands are because I'm transcribing them from my server to my laptop.

Sound plays fine when I use

```
aplay /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
```

I'd post the results of lspci, but since the above command works, I doubt its a hardware issue. Anybody know what I can do to fix this?

---

### Post by Buce on 2010-01-12
Here's the output of the script at [http://alsa.opensrc.org/index.php/Aadebug](http://alsa.opensrc.org/index.php/Aadebug)

```
ALSA Audio Debug v0.1.0 - Tue Jan 12 03:37:17 CST 2010
http://alsa.opensrc.org/aadebug
http://www.gnu.org/licenses/gpl.txt

Kernel ----------------------------------------------------
Linux r2d2 2.6.24-26-server #1 SMP Tue Dec 1 19:19:20 UTC 2009 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_intel8x0           35356  1 
snd_ac97_codec        100772  1 snd_intel8x0
snd_pcm_oss            42016  0 
snd_pcm                78724  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          17792  2 snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            35456  0 
snd_seq_midi            9248  0 
snd_rawmidi            25632  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56868  11 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         11528  2 snd_intel8x0,snd_pcm

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Dec  2 2009 for kernel 2.6.24-26-server (SMP).
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with ALC850 at irq 22
  0: [ 0]   : control
  1:        : sequencer
 16: [ 0- 0]: digital audio playback
 20: [ 0- 4]: digital audio playback
 24: [ 0- 0]: digital audio capture
 25: [ 0- 1]: digital audio capture
 26: [ 0- 2]: digital audio capture
 27: [ 0- 3]: digital audio capture
 33:        : timer
00-04: Intel ICH - IEC958 : Intel ICH5 - IEC958 : playback 1
00-03: Intel ICH - ADC2 : Intel ICH5 - ADC2 : capture 1
00-02: Intel ICH - MIC2 ADC : Intel ICH5 - MIC2 ADC : capture 1
00-01: Intel ICH - MIC ADC : Intel ICH5 - MIC ADC : capture 1
00-00: Intel ICH : Intel ICH5 : playback 1 : capture 1
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
controlC0  pcmC0D0p  pcmC0D2c  pcmC0D4p  timer
pcmC0D0c   pcmC0D1c  pcmC0D3c  seq

CPU -------------------------------------------------------
model name	: Intel(R) Pentium(R) 4 CPU 2.40GHz
cpu MHz		: 2398.926

RAM -------------------------------------------------------
MemTotal:      2075328 kB
SwapTotal:     4096532 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

```

I had to change this line in the script in order to get it to run without errors (comment is the original line, line below that is my modification):

```

else
    #cat /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}
    cat /proc/asound/{version,cards,devices,pcm,seq/clients}
fi

```

Does anyone see any obvious problems?

---

### Post by Buce on 2010-01-12
Taking a hint from [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

```
woody@r2d2:~$ ./alsa-info.sh
ALSA Information Script v 0.4.58
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See './alsa-info.sh --help' for command line options.

Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ... Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=1b64b5fcc625b3641c7da925462829ed98266f27](http://www.alsa-project.org/db/?f=1b64b5fcc625b3641c7da925462829ed98266f27)

Please inform the person helping you.

```

The driver version doesn't match the library/utilities version in the output of alsa-info. How do I correct this?

---

### Post by Buce on 2010-01-12
Just got the solution from Launchpad. Use mpg123, not aplay. *facepalm*

---

### Post by Bucky Ball on 2010-01-12
Well done! Please mark as solved from thread tools to help others. :)

---

