---
title: "microphone doesn't work"
date: 2011-07-22
forum: Multimedia Software
---

### Post by kingbirdy on 2011-07-22
the mic on my laptop (lenovo g555, Ubuntu 11.04) doesn't work. No matter what application I'm using, it won't register. It worked just fine when I had windows installed. I've checked my sound preferences, and my input isn't muted, and no matter what volume I put the input at, it won't pick anything up.

---

### Post by Volens on 2011-07-22
Put this:
```
lspci -v
```
 
in a terminal and post the whole section regarding your audio adapter. If you can't find it, post all the output. This command lists hardware and their respective kernel modules (drivers).
 
This is to check if your soundcard is being detected and has a driver loaded.

---

### Post by kingbirdy on 2011-07-22
alright, I think this is the right thing:
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Lenovo Device 3938
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```

---

### Post by Volens on 2011-07-22
Check out one of my own old threads:
 
[http://ubuntuforums.org/showthread.php?t=1582088](http://ubuntuforums.org/showthread.php?t=1582088)
 
basically try adding:
 
```
options snd-hda-intel model=mobile
```
 
to the end of /etc/modprobe.d/alsa-base.conf
 
and reboot
 
If it doesn't work, take it out, reboot, and you'll have to wait for someone else to drop by because thats my only suggestion.
 
Good Luck

---

### Post by kingbirdy on 2011-07-22
still doesn't work. thanks anyway, though.

---

### Post by ajgreeny on 2011-07-22
Run ```
alsamixer
``` in terminal and check that the levels of outputs are not set too low.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
On the capture "page" move to the mic slider and check that the CAPTURE text at the bottom is in red, ie active.  If not and something else shows red use the spacebar to activate the mic to move it from the other captured input.
Esc will save and exit.

Using alsamixer can sometimes show things that do not appear elsewhere.  See screenshot.

---

### Post by kingbirdy on 2011-07-22
it's all the way up and active, and still not working

---

### Post by goldshirt9 on 2011-07-22
sound settings :-
*ensure the audio is set to PulseAudio duplex*

---

### Post by Volens on 2011-07-22
I forgot to check for that first ajgreeny, remember being told that quite a few times in the past.
 
Check out this:
 
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)
 
and also try using the option "model=lenovo" instead of "model=mobile"

---

### Post by kingbirdy on 2011-07-22
neither of those worked, thanks though

---

