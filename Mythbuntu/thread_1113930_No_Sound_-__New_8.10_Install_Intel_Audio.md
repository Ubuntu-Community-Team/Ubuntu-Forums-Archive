---
title: "No Sound -  New 8.10 Install Intel Audio"
date: 2009-04-02
forum: Mythbuntu
---

### Post by nasha on 2009-04-02
Hi Guys,
setting up a new backend to replace my dated server. Everything is up and running, except my sound, not only in mythtv but mythbuntu also.
I've never had any audio issues before, so i wouldnt know where to start with troubleshooting.

Settings Manager > Sound > Device: #0:HDA Intel
However when i try to select the checkboxes for the controls, after closing, theyre unchecked again

```
nasha@MythTV:~$ lspci -v

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: ASUSTeK Computer Inc. Device 8290
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f9ffc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```
Hopefully somebody can shed some light (or sound rather) on this situation :)

---

### Post by Sam Lars on 2009-04-03
What checkboxes are you referring to?

---

### Post by nickrout on 2009-04-03
why does a backend need sound?

---

### Post by nasha on 2009-04-04
In settings manager > sound. The checkboxes there for selectingg volume controls.

Its also my frontend...

---

### Post by nickrout on 2009-04-04
have you tried running alsamixer from the command line?

---

### Post by nasha on 2009-04-04
No i havn't, i will give it a shot this evening though. As i said, im completely unfamiliar with sound under linux. Appreciate the help

Just ran alsamixer, all volume levels are full (and un-muted), and it appears to recognise my audio device

---

### Post by nasha on 2009-04-05
I just tried the Mythbuntu 8.10 Live CD, and audio worked fine... So i reinstalled, ran alsamixer to ensure channels werent muted and the audio device was recognised, and all was good. But still no sound...

---

### Post by nasha on 2009-04-05
Turns out this issue was caused with the way the nvidia drivers handle tv's connected via DVI-HDMI cables, and disabling the audio input on the tv itself.

Thanks for your help nickrout, it was your post in the 9400gt thread that lead me to the solution :)

Solution to this problem can be found here:
[HTML]http://analogbit.com/node/23[/HTML]

---

