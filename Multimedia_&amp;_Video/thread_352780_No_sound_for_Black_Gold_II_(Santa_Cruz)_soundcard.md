---
title: "No sound for Black Gold II (Santa Cruz) soundcard"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by tarjxvf on 2007-02-03
I installed ubuntu 6.10 yesterday and got no sound. I have two soundcards in my computer:
1. Built-in soundcard on the mainboard, module name snd-intel8x0
2. A separate Black Gold II (Santa Cruz) sound card, module name snd-cs46xx
I want to use the second one, because it's much better.  

Whe the system first boot up, I used "lsmod" to see the modules, and found that both "snd-intel8x0 and snd-cs46xx" were on the list. So I blacklisted "snd-intel8x0" in /etc/modprobe.d/blacklist. 

Then I rebooted,  and saw that "snd-intel8x0" was gone, and only "snd-cs46xx" was on the list of "lsmod". However, there's still no sound.  All the programs look absolutely normal: totem has no problem playing mp3 files, alsamixer has no problem ajusting the bars), but there was simply no sound, deadly silent. It looked just as if the volume was muted. However, I checked many times in alsamixer that all these items were on: Master, PCM, PCM 1, ADC, DAC, External Amplifier etc. I am also quite sure that I did powered on the speakers, and did plug the wires into the right jack (because this setup works in windows xp). I also tried recomiling alsa-driver-1.0.13 from alsa-project, and tried disabling on-board soundcard in bios, but it's still the same.  

Interesingly, the on-board snd-intel8x0 does work very well: if I rmmod snd-cs46xx and then modprobe snd-intel8x0 and re-plug the wires of speakers into the jack of on-board sound card, then there's sound, very loudly. But no matter how hard I tried, the separate Santa Cruz sound card keeped silent. Is this a bug in the cs46xx module of alsa driver? Can any one help me? Thank you!

btw: Here are some outputs, hopefully it makes my situation more clear:
```

$ lspci | grep audio
01:08.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

```

```

$ lsmod | grep snd
snd_cs46xx             90728  1 
gameport               17160  2 snd_cs46xx
snd_rawmidi            27136  1 snd_cs46xx
snd_seq_device          9868  1 snd_rawmidi
snd_ac97_codec        102820  1 snd_cs46xx
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47232  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84996  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_timer              24964  1 snd_pcm
snd                    60676  10 snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11656  2 snd_cs46xx,snd_pcm

```


```

$ cat /proc/asound/cards 
 0 [CS46xx         ]: CS46xx - Sound Fusion CS46xx
                      Sound Fusion CS46xx at 0xf2100000/0xf2000000, irq 58

```

```

$ amixer 
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 14 [45%] [-25.50dB] [on]
  Front Right: Playback 14 [45%] [-25.50dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Master',1
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 0 [0%] [-94.50dB] [off]
  Front Right: Playback 0 [0%] [-94.50dB] [off]
Simple mixer control '3D Control - Center',1
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Depth',1
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control '3D Control - Switch',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control '3D Control Sigmatel - Depth',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 15 [48%] [-12.00dB] [on]
  Front Right: Playback 15 [48%] [-12.00dB] [on]
Simple mixer control 'PCM Out Path & Mute',0
  Capabilities: enum
  Items: 'pre 3D' 'post 3D'
  Item0: 'pre 3D'
Simple mixer control 'PCM Out Path & Mute',1
  Capabilities: enum
  Items: 'pre 3D' 'post 3D'
  Item0: 'pre 3D'
Simple mixer control 'PCM',1
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 15 [48%] [-12.00dB] [on]
  Front Right: Playback 15 [48%] [-12.00dB] [on]
Simple mixer control 'Surround',1
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 0 [0%] [-94.50dB] [off]
  Front Right: Playback 0 [0%] [-94.50dB] [off]
Simple mixer control 'Center',1
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 63
  Mono: Playback 21 [33%] [-63.00dB] [off]
Simple mixer control 'LFE',1
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 63
  Mono: Playback 0 [0%] [-94.50dB] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Line',1
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [3.00dB] [on] Capture [off]
  Front Right: Playback 25 [81%] [3.00dB] [on] Capture [off]
Simple mixer control 'CD',1
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Boost (+20dB)',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Mic',1
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Video',1
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 12 [39%] [-16.50dB] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',1
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Input',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Aux',1
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix',1
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',1
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'ADC',0
  Capabilities: volume cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 32767
  Front Left: 32767 [100%] Capture [off]
  Front Right: 32767 [100%] Capture [off]
Simple mixer control 'DAC',0
  Capabilities: volume cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 32767
  Front Left: 32767 [100%] Capture [off]
  Front Right: 32767 [100%] Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Sigmatel 4-Speaker Stereo',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Sigmatel Surround Phase Inversion Playback ',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

```

---

### Post by p!=f on 2007-02-03
This happened to me with an onboard RealTek and M-Audio. The sound was working when booted from LiveCD so I was sure there's something wrong with my setup. Honestly, I'm not sure what made it running, it just started to sound after a restart. I'm sure I ran this command, maybe it can do the trick but don't bet on it :)
```

sudo depmod

```
Btw, I noticed you don't have snd_seq_oss module loaded.

---

### Post by tarjxvf on 2007-02-03
Thank you for the tips. I've tried "sudo depmod" and "sudo modprobe snd_seq_oss". But it didn't work, unfortunately.

There is this weird message in kern.log and syslog:
```

kern.log:Feb  3 19:18:55 tarjxvf-desktop kernel: [17180374.492000] ALSA /home/aharon/tmp/alsa/alsa-driver-1.0.13/pci/cs46xx/../../alsa-kernel/pci/cs46xx/cs46xx_lib.c:429: cs46xx: failure waiting for FIFO command to complete

```
I'm not sure if it's related to the muting of the soundcard.

---

### Post by p!=f on 2007-02-04
So you tried to compile alsa (alsa-modules) on your own or you use Ubuntu packages? What's the output of
```

dpkg -l | grep alsa
dpkg -l | grep -v ^ii
apt-cache policy alsa-base linux-sound-base

```
Do you have a LiveCD by hand so you can try if it works from there?

---

### Post by tarjxvf on 2007-02-04
Yes, I tried in the ubuntu-6.10 live cd, and still no sound :-(

I googled a lot yesterday, and found that although BlackGoldII (Canon) sound cards use the same chip as Santa Cruz Turtle ones, they are not exactly the same. There is an extra electro-magnic device in BGII to be activated to be able to produce sound. Some guy from Togotech (the manufacturer) confirmed in its forum that this electro-magnic device need extra driver to activate, so directly using ALSA driver doesn't work. The bad news is that they have stopped writing the driver for linux a long time (more than 2 years) ago, and the most recent one only works for linux < 2.6.7 (?). If I were a driver programmer, and if I had a lot of time, I might look through their source code and write my own driver for linux-2.6.17. But I really don't have the time. So I simply give up and use the on-board intel8x0 driver!

---

### Post by pseudonym on 2007-02-04
If you have no luck with ALSA you could try the OSS drivers from opensound.com . They sometimes support cards (or support better) which ALSA doesn't at this time.

---

### Post by tarjxvf on 2007-02-05
I tried oss from opensound.com, but there's still no sound. I've given up. But thank you guys for your kind help!

---

