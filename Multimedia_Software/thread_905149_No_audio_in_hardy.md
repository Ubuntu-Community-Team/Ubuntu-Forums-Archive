---
title: "No audio in hardy"
date: 2008-08-30
forum: Multimedia Software
---

### Post by naisho on 2008-08-30
I just shifted to Kubuntu8.04, earlier I had no sound problem with Ubuntu8.04 :o or Slackware or Suse!
I have enabled the mixers and volume is set to max. This is my aplay -l

Code:

naisho@Vizard:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Code:

naisho@Vizard:~$ lspci -v

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Aud
io Controller (rev 01)
        Subsystem: Intel Corporation Unknown device d606
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at 501c0000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


When for the first time I tried opening a mp3 with amarok, it asked me to download and install a few mp3 codec packages which I did, it showed successfully installed and started playing, only the progressbar was moving but no sound. Rebooted and still no luck. Plz help.

PS- I know this is Ubuntu forum but I´d really appreciate it if someone helps me out on this Kubuntu issue. Thnx.

---

### Post by naisho on 2008-08-30
EDIT:

Ok I did  sudo /etc/init.d/alsa-utils reset
the sound came, adjusted the Alsamixer. Rebooted. Again sound gone. Again did the reset, sound worked. Again after reboot its gone. Do i have to reset it everytime I login? :(

---

### Post by naisho on 2008-08-30
Bump

---

### Post by minky311 on 2008-08-30
Could you post what you get when you enter this in terminal
```
cat /proc/asound/modules
```

---

