---
title: "Strange sound behavior (automatic changing preferences))"
date: 2011-10-26
forum: Multimedia Software
---

### Post by Simsdebims on 2011-10-26
Hey everybody,

Since updating to 11.10 the sound of my system is quite strange: Sound volume changes permanently, about twice a second. Its kind a "flickering"... Those changes are shown through the controllers in KMix (and of course I can hear it). Also other preferences are reseted every time I try to change them: Muting is impossible, setting "analog output" or "analog headphone" is impossible - there is an permanent automatic switching between these two setting.
Im using KDE 4.7.2. Here are some more information about my system:

```

$ lsb_release -d
Description:    Ubuntu 11.10

$ uname -r
3.0.0-12-generic                                                                                                                                                                    

$ cat /proc/asound/cards 
 0 [Intel          ]: HDA-Intel - HDA Intel                                                                                                                                         
                      HDA Intel at 0xf7df8000 irq 41                                                                                                                                

$ aplay -l
**** Liste der Hardware-Geräte (PLAYBACK) ****                                                                                                                                      
Karte 0: Intel [HDA Intel], Gerät 0: ALC892 Analog [ALC892 Analog]                                                                                                                  
  Sub-Geräte: 1/1                                                                                                                                                                   
  Sub-Gerät #0: subdevice #0                                                                                                                                                        
Karte 0: Intel [HDA Intel], Gerät 1: ALC892 Digital [ALC892 Digital]                                                                                                                
  Sub-Geräte: 1/1                                                                                                                                                                   
  Sub-Gerät #0: subdevice #0                                                                                                                                                        

$ aplay /usr/share/sounds/alsa/Noise.wav                                                                                                                             
Wiedergabe: WAVE '/usr/share/sounds/alsa/Noise.wav' : Signed 16 bit Little Endian, Rate: 48000 Hz, mono                                                                             

$ lspci -nnk | grep -iA2 audio
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
        Subsystem: ASRock Incorporation Device [1849:0892]                                                                                                                          
        Kernel driver in use: HDA Intel                                                                                                                                             

$ ps -C esd                                                                                                                                                          
  PID TTY          TIME CMD                                                                                                                                                         

$ ps -C arts
  PID TTY          TIME CMD

$ ps -C pulseaudio
  PID TTY          TIME CMD
 2077 ?        00:00:12 pulseaudio

$ grep "^audio" /etc/group | grep "$USER" | wc -l
0

$ lsmod | grep "snd"
snd_hrtimer            12744  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  3 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm

$ head -n 3 /proc/asound/card0/codec#0
Codec: Realtek ALC892
Address: 0
AFG Function Id: 0x1 (unsol 1)

```Any ideas?

Thanks...

---

### Post by nailbar on 2011-11-28
I have the same problem. Integrated Intel card here too though not exactly the same.

```
$ cat /proc/asound/cards 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf9ff8000 irq 44

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

$ head -n 3 /proc/asound/card0/codec#0
Codec: Realtek ALC1200
Address: 0
AFG Function Id: 0x1 (unsol 1)
```It started some week ago after an update. I installed Kubuntu 11.10 from scratch and the problem wasn't there from the start.

---

### Post by nailbar on 2011-12-01
Aha! Found that Auto-Mute was enabled but not working properly. Problem solved at least for the time being.

I was able to disable Auto-Mute in alsamixer.

Can't say if this would be a work-around or a solution.

---

