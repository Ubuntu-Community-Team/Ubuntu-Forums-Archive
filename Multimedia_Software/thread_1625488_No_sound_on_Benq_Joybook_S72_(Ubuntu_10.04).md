---
title: "No sound on Benq Joybook S72 (Ubuntu 10.04)"
date: 2010-11-19
forum: Multimedia Software
---

### Post by timi030 on 2010-11-19
Hello,
i have installed Ubuntu 10.04 on a Benq Joybook S72. After adding radeon-kms.conf everything works fine** except the sound**. I read a lot of websites but found no solution for my problem. 
The audiosettings and the alsamixer a adjusted right but the is no sound neither from the spaeakers nor from a plugged in headphone. 
I have attached some details: 
```
lsb_release -d
Description:    Ubuntu 10.04.1 LTS

uname -r
2.6.32-25-generic

cat /proc/asound/cards
 0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with AD1980 at irq 10
aplay -l
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: ICH6 [Intel ICH6], Gerät 0: Intel ICH [Intel ICH6]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: ICH6 [Intel ICH6], Gerät 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0

aplay /usr/share/sounds/alsa/Noise.wav
Wiedergabe: WAVE '/usr/share/sounds/alsa/Noise.wav' : Signed 16 bit Little Endian, Rate: 48000 Hz, mono

aplay /usr/share/sounds/alsa/Front_Center.wav 
Wiedergabe: WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate: 48000 Hz, mono


lspci -nnk | grep -iA2 audio
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 04)
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

lsmod | grep "snd" 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54180  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm

cat /proc/asound/cards 
 0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with AD1980 at irq 10

head -n 3 /proc/asound/card0/codec#0 
head: „/proc/asound/card0/codec#0“ kann nicht zum Lesen geöffnet werden: No such file or directory

head -n 3 /proc/asound/card0/codec97#0/ac97#0-0 
0-0/0: Analog Devices AD1980

PCI Subsys Vendor: 0x17ff

head -n 3 /proc/asound/card0/codec97#0/ac97#0-0+regs 
0:00 = 0090
0:02 = 1f1f
0:04 = 0000

aplay -l 
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: ICH6 [Intel ICH6], Gerät 0: Intel ICH [Intel ICH6]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: ICH6 [Intel ICH6], Gerät 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0

aplay /usr/share/sounds/startup.wav 
/usr/share/sounds/startup.wav: No such file or directory

asoundconf list 
asoundconf: Befehl nicht gefunden

ps -C esd
  PID TTY          TIME CMD

ps -C arts
  PID TTY          TIME CMD

ps -C pulseaudio
  PID TTY          TIME CMD
 1239 ?        00:00:00 pulseaudio

```Could someone please help me. Thanks

---

### Post by timi030 on 2010-11-22
Has *nobody any ideas* ? i would appreciate a response. Thank you.

---

### Post by timi030 on 2011-02-23
A user from the german ubuntuusers forum posted the solution.
I just had to switch on the "Exchange Front/Surround" in the alsamixer and change the sound preferences to surround and now its working.

---

