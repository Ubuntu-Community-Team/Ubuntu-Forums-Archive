---
title: "[SOLVED] Help with Microphone Needed plz"
date: 2008-12-08
forum: Multimedia Software
---

### Post by djbushido on 2008-12-08
I'm trying to get my microphone enabled so I can use skype. I tried all available options in skype, but it still isn't working. I have no idea how to debug this, so any help would be appreciated. Once again, sorry for being ambiguous, but i have no idea where to start.

---

### Post by Menschenfresser on 2008-12-09
I had a similar problem (no mic after upgrading to intrepid, worked before). What solved it for me in both the desktop and the laptop was to select in the skype "Sound Device" sound out and ringing to "pulse" and sound in to "HDA Intel (hw:...)". Besides that, in Ubuntu's volume control, recording tab, the microphone was practically muted. After moving it up it worked fine.

---

### Post by djbushido on 2008-12-09
What do you mean by pulse? Pulse audio server? because even with my pulse daemon running, that doesn't show up in skype.

---

### Post by Menschenfresser on 2008-12-09
Yes pulseaudio. If it isn't even showing up there, it looks it's a more serious issue with PulseAudio and I have no idea, I've had my share of problems with it...

---

### Post by djbushido on 2008-12-09
I'm going to try and reinstall pulse, and see if that helps. Do you know if there is anyway to detect the hardware input? I.e., the port where the microphone comes in at?

---

### Post by markbuntu on 2008-12-09
You should not need to reinstall pulseaudio. What you most likely need is to get it setup properly:


[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by djbushido on 2008-12-10
Alright, get ready for teh ultimate fail...
Plugged in headphone slot,not microphone...
I am so stupid...
Anyway, thank you for helping me get pulseaudio running... that's going to help later i guarantee it...
Thanks a lot guys...

---

