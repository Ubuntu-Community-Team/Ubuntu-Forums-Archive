---
title: "Intel HDA repeated crackling sound during playback"
date: 2010-11-07
forum: Multimedia Software
---

### Post by Vincent Vermeulen on 2010-11-07
During music playback I get every 10-15 seconds a crackling sound. This on a fresh install of 10.10, fully updated. Issue was not present on 10.04. Who has a similar issue or can help me out to diagnose?

I find people have issues with crackle on 10.10 at Ubuntu startup or shutdown. I have the issue during music playback (occurs at least on Rhythmbox and Firefox). Tried some options in alsa-base.conf (enable_msi=1, position_fix=1) but none so far have helped. I tried replacing speakers also, no change.

I think this is a pulseaudio issues. Can I downgrade to the 10.04 version of that :)

aplay -l gives:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by Vincent Vermeulen on 2010-11-08
For now removed PulseAudio--everything sounds fine now. Only thing missing was volume control, so I installed alsamixergui as also the gnome-volume control does not work anymore after PulseAudio removal.

Confirmed issue is caused by PulseAudio.

```
sudo apt-get purge pulseaudio
sudo apt-get install alsamixergui
```

---

### Post by bedihardeep on 2010-11-08
> **Vincent Vermeulen said:**
> For now removed PulseAudio--everything sounds fine now. Only thing missing was volume control, so I installed alsamixergui as also the gnome-volume control does not work anymore after PulseAudio removal.

Confirmed issue is caused by PulseAudio.

```
sudo apt-get purge pulseaudio
sudo apt-get install alsamixergui
```

i noticed same problem as well but 
i already installed alsamixer so if i uninstall pulse audio ,is that will work 

so u dont have any cracking sound any more 

please confirm

---

### Post by Vincent Vermeulen on 2010-11-08
bedihardeep, I can confirm that removing pulseaudio removes the crackling/stuttering sound in music playback on my setup. I've tested Rhythmbox and Firefox and VLC, all without crackling/stuttering now.

I added alsamixergui, because the volume control disappears once you remove pulseaudio. To change volume, you can use that (found in applications>sound & video).

---

### Post by bedihardeep on 2010-11-08
> **Vincent Vermeulen said:**
> bedihardeep, I can confirm that removing pulseaudio removes the crackling/stuttering sound in music playback on my setup. I've tested Rhythmbox and Firefox and VLC, all without crackling/stuttering now.

I added alsamixergui, because the volume control disappears once you remove pulseaudio. To change volume, you can use that (found in applications>sound & video).


ok 
thanks for sharing 
i will try

---

### Post by bedihardeep on 2010-11-09
> **bedihardeep said:**
> ok 
thanks for sharing 
i will try


i uninstall pulse audio it works great 

thanks buddy

---

### Post by sallymc on 2012-11-05
Unfortunately no luck with me!
Sallymc

---

