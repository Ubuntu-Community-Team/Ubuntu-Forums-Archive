---
title: "Microphone on Skype with Maverick 64 bit doesn't work"
date: 2010-11-09
forum: Multimedia Software
---

### Post by Axx83 on 2010-11-09
Hi guys, I have a problem making skype work with my notebook.

Ubuntu is version 10.10 amd64, the computer is an Acer Travelmate 8172t, the card is a Conexant CX20585 and to make it work I installed alsa package from this repository [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu)

I installed skype from partner repository, everything works, including webcam, but of course getting sound from microphone.

With gnome recorder the mic works ok.

What should I do ?

---

### Post by DinghySailor on 2010-11-10
I have the same issue, with Skype 2.1.0.81 on 10.10 (Maverick) using 32 bit Ubuntu on a notebook. It worked fine on Lucid. Mumble suffers similarly - the received sound is fine - just the microphone.

Sound Recorder works fine, so its not the microphone. I use a headset.

Many thanks,

---

### Post by Bucky Ball on 2010-11-10
Right click on the speaker icon and go to the sound properties themselves (from memory, don't have my Maverick laptop in front of me). From there, click on input devices and make a test call with Skype. You should have an audio stream happen in input devices. Right click on that and 'Move Stream'. 

This is from memory. In 10.10 possible you just need to right click on desired input device and make that default and that's enough.

I'll check back later when I have my Maverick happening. Can I presume these are USB headsets?

ps: DinghySailor, just wondering if you mean netbook? If you have a notebook, has it dual-core and if so why no 64bit?

---

### Post by Axx83 on 2010-11-10
I solved it, you open ```
alsamixer -Dhw
``` press tab and when under the MIC column you keep pressing the c key until the right side mic is completely muted, that makes everything works.

---

### Post by ramidalf on 2011-04-23
> **Axx83 said:**
> I solved it, you open ```
alsamixer -Dhw
``` press tab and when under the MIC column you keep pressing the c key until the right side mic is completely muted, that makes everything works.
Its working but i used PulseAudio Device Chooser from Ubuntu software center. Then i ran this program and chose Volume Meter and muted right side mic completely.

---

