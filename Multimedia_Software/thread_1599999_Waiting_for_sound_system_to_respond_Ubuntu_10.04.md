---
title: "Waiting for sound system to respond Ubuntu 10.04"
date: 2010-10-18
forum: Multimedia Software
---

### Post by HobbDogg on 2010-10-18
Alright I have tried to the best of my ability to get this popup from displaying. 
> Waiting for sound system to respond
I am using a PNY GeForce 210 graphics card with HDMI. I have the sound working over the HDMI thanks to these threads, and the XMBC wiki:

[HTML]http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240
http://www.nvnews.net/vbulletin/showthread.php?t=143610&page=4
http://www.nvnews.net/vbulletin/showthread.php?t=150113&page=4[/HTML]

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

This device is listed after I disabled the onboard audio through the bios, and found the correct mask for the probe_mask (listed below), otherwise there were about 8 devices listed.

My /etc/modprobe.d/sound.conf file contents
> alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel probe_mask=0xfff2

my /etc/asound.conf file contents
> pcm.!default hdmi:NVidia
pcm:iec958 hdmi:NVidia

I have also tried deleting the ~/.pulse file and restarting the computer because that did help out a lot of people, but this did not work either.

After running
```
killall pulseaudio
pulseaudio --start
E: main.c: Daemon startup failed.
```

I DO have sound, BUT I cannot control the sound through the OS sound panel. Any help would be greatly appreciated.

---

### Post by HobbDogg on 2010-10-20
bump, no ideas, i've tried some more searching, still nothing.

---

### Post by awi on 2010-10-25
I had a similar problem, and I've solved it by erasing my $HOME/.pulse directory, and now I have audio controls working again.

---

### Post by lelandnielsen on 2011-02-19
I have the same problem.  Deleting the .pulse folder doesn't work for me.  I have no access to the Sound preferences in System.  Attempts to open it give me the message "Waiting for sound system to respond".  I'm running Ubuntu 10.04, using an MAudio Delta 1010LT sound card, and an NVIDIA graphcis card.

---

### Post by juicyoner on 2011-04-01
bbbbbbbbbbbbbbbbbbbump.

ne1?

---

