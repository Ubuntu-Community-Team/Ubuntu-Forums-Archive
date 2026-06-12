---
title: "Sound doesn't work"
date: 2009-11-11
forum: Multimedia Software
---

### Post by Mandarine on 2009-11-11
Hi,

I recently installed Ubuntu 9.10 on my Desktop, hoping that my soundcard Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG will work. Unfortunately, it doesn't ...

The card shows up in the mixer, but I don't hear no sound ...

Here is some additional information:


```

lsb_release -d
Description:	Ubuntu 9.10
```

```
uname -r
2.6.31-14-generic
```

```
cat /proc/asound/cards
 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfdffc000 irq 16
 1 [CX8811         ]: CX88x - Conexant CX8811
                      Conexant CX8811 at 0xf8000000
 2 [Q9000          ]: USB-Audio - QuickCam Pro 9000
                      Logitech, Inc. QuickCam Pro 9000 at usb-0000:00:0a.1-3, high speed
```

```
aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: Generic [HD-Audio Generic], Gerät 0: CA0110 Analog [CA0110 Analog]
  Untergeordnete Geräte: 0/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: Generic [HD-Audio Generic], Gerät 1: CA0110 Digital [CA0110 Digital]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
```

```
aplay /usr/share/sounds/alsa/Noise.wav
Wiedergabe Wave '/usr/share/sounds/alsa/Noise.wav' : Signed 16 bit Little Endian, Samplingrate: 48000 Hz, Mono
```

no sound is audible ...

```
lspci | grep -i audio
02:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:07.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
02:07.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
02:07.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
03:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
04:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
```

```
ps -C esd
  PID TTY          TIME CMD
```

```
ps -C arts
  PID TTY          TIME CMD
```

```
ps -C pulseaudio
  PID TTY          TIME CMD
 2044 ?        00:00:02 pulseaudio
```

```
grep "^audio" /etc/group | grep "$USER" | wc -l
1
```

```
lsmod | grep "snd"
snd_usb_audio         102976  1 
snd_usb_lib            19648  1 snd_usb_audio
snd_hda_codec_ca0110     9472  1 
snd_hda_intel          31880  3 
snd_hda_codec          87584  2 snd_hda_codec_ca0110,snd_hda_intel
snd_hwdep               9352  2 snd_usb_audio,snd_hda_codec
snd_seq_dummy           3460  0 
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_seq_oss            33440  0 
snd_pcm                93160  6 snd_usb_audio,snd_hda_intel,snd_hda_codec,cx88_alsa,snd_pcm_oss
snd_seq_midi            8192  0 
snd_rawmidi            27360  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  23 snd_usb_audio,snd_hda_codec_ca0110,snd_hda_intel,snd_hda_codec,snd_hwdep,cx88_alsa,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
```

```
head -n 3 /proc/asound/card0/codec#0
head: „/proc/asound/card0/codec#0“ kann nicht zum Lesen geöffnet werden: No such file or directory
```

```
head -n 3 /proc/asound/card0/codec97#0/ac97#0-0
head: „/proc/asound/card0/codec97#0/ac97#0-0“ kann nicht zum Lesen geöffnet werden: No such file or directory
```

```
head -n 3 /proc/asound/card0/codec97#0/ac97#0-0+regs
head: „/proc/asound/card0/codec97#0/ac97#0-0+regs“ kann nicht zum Lesen geöffnet werden: No such file or directory
```

```
asoundconf list
asoundconf: command not found
```

```
cat ~/.asoundrc
cat: /home/sascha/.asoundrc: No such file or directory
```

```
cat ~/.asoundrc.asoundconf
cat: /home/sascha/.asoundrc.asoundconf: No such file or directory
```

can anybody help?

Sascha

---

### Post by VertexPusher on 2009-11-11
Open Synaptic and select the following packages for complete removal:

pulseaudio
gstreamer0.10-pulseaudio
vlc-plugin-pulse

Select the following packages for installation:

gstreamer0.10-alsa
gnome-alsamixer

Open a text editor and enter the following lines:
```
defaults.ctl.!card Generic
defaults.pcm.!card Generic
```
Save the file as ~/.asoundrc

This will make the Creative Labs card the default ALSA card for both playback and recording. If you prefer to make the webcam microphone the default recording device, set up the .asoundrc file like this:
```
pcm.!default {
    type asym
    playback.pcm {
        type plug
        slave.pcm dmix:Generic
    }
    capture.pcm {
        type plug
        slave.pcm dsnoop:Q9000
    }
}
```
This will bundle the Creative Labs card and the webcam mic as a virtual full-duplex soundcard that supports playback and recording in multiple applications simultaneously.

---

### Post by Mandarine on 2009-11-14
Nope, doesn't work ...

---

