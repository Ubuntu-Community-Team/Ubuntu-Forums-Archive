---
title: "temporarely soundproblems under ubuntu 11.04 (x64)"
date: 2011-08-18
forum: Multimedia Software
---

### Post by henrik23 on 2011-08-18
Hi,

:confused:  most time I don't hear the music my computer plays. :confused:

```
fragstyler@fragstyler-desktop:~$ lsb_release -d
Description:    Ubuntu 11.04
fragstyler@fragstyler-desktop:~$ uname -r
2.6.38-10-generic
fragstyler@fragstyler-desktop:~$ cat /proc/asound/cards
 0 [CMI8738        ]: CMI8738-MC6 - C-Media CMI8738
                      C-Media CMI8738 (model 55) at 0xe800, irq 16
fragstyler@fragstyler-desktop:~$ aplay -l
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: CMI8738 [C-Media CMI8738], Gerät 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: CMI8738 [C-Media CMI8738], Gerät 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: CMI8738 [C-Media CMI8738], Gerät 2: CMI8738-MC6 [C-Media PCI IEC958]
  Sub-Geräte: 0/1
  Sub-Gerät #0: subdevice #0
fragstyler@fragstyler-desktop:~$ aplay /usr/share/sounds/alsa/Noise.wav
Wiedergabe: WAVE '/usr/share/sounds/alsa/Noise.wav' : Signed 16 bit Little Endian, Rate: 48000 Hz, mono
fragstyler@fragstyler-desktop:~$ lspci -nnk | grep -iA2 audio 
05:00.0 Multimedia audio controller [0401]: C-Media Electronics Inc CM8738 [13f6:0111] (rev 10)
    Subsystem: TERRATEC Electronic GmbH Aureon 5.1 [153b:1144]
    Kernel driver in use: C-Media PCI
fragstyler@fragstyler-desktop:~$ ps -C esd
  PID TTY          TIME CMD
fragstyler@fragstyler-desktop:~$ ps -C arts
  PID TTY          TIME CMD
fragstyler@fragstyler-desktop:~$ ps -C pulseaudio
  PID TTY          TIME CMD
 2175 ?        00:09:26 pulseaudio
fragstyler@fragstyler-desktop:~$ grep "^audio" /etc/group | grep "$USER" | wc -l
1
fragstyler@fragstyler-desktop:~$ lsmod | grep "snd"
snd_cmipci             44890  3 
gameport               19652  1 snd_cmipci
snd_pcm                96391  2 snd_cmipci
snd_page_alloc         18529  1 snd_pcm
snd_opl3_lib           19264  1 snd_cmipci
snd_hwdep              13604  1 snd_opl3_lib
snd_mpu401_uart        14169  1 snd_cmipci
snd_seq_midi           13324  0 
snd_rawmidi            30486  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device         14462  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  14 snd_cmipci,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
fragstyler@fragstyler-desktop:~$ head -n 3 /proc/asound/card0/codec#0
head: „/proc/asound/card0/codec#0“ can't be opened for reading: file or folder not found
fragstyler@fragstyler-desktop:~$ head -n 3 /proc/asound/card0/codec97#0/ac97#0-0
head: „/proc/asound/card0/codec97#0/ac97#0-0“ can't be opened for reading: file or folder not found
fragstyler@fragstyler-desktop:~$ head -n 3 /proc/asound/card0/codec97#0/ac97#0-0+regs
head: „/proc/asound/card0/codec97#0/ac97#0-0+regs“ can't be opened for reading: file or folder not found
fragstyler@fragstyler-desktop:~$ asoundconf list
Names of available sound cards:
CMI8738

```Hope somebody knows the answer.

Greets
Henrik

---

### Post by lidex on 2011-08-20
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by henrik23 on 2011-08-22
Hi,

here is the output: [http://www.alsa-project.org/db/?f=64fda3f3a18087e4010e11e329e8ad17a25b3572](http://www.alsa-project.org/db/?f=64fda3f3a18087e4010e11e329e8ad17a25b3572)

Greets
Henrik

---

