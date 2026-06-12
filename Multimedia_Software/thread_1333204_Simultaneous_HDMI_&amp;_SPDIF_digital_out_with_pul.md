---
title: "Simultaneous HDMI &amp; SPDIF digital out with pulseaudio"
date: 2009-11-21
forum: Multimedia Software
---

### Post by bogoliubov on 2009-11-21
Hello. I have a (Zotac) ION 330 MB with HDMI and SPDIF digital outputs. I want to use both outputs simultaneously , but don't know how to set this up!?

I use Ubuntu 9.10 (upgraded from 9.04)

I have tried to run paprefs and enable outputs on all soundcards, but this makes no change. I guess this is since I only have one soundcard, but with several outputs...?

So, any ideas are greatly appreciated!

---

### Post by bogoliubov on 2010-01-09
Please, is there anyone who can help with this? I've tried to read the docs for both Alsa and PulseAudio, but no sucess yet. I really need this to work!

---

### Post by bogoliubov on 2010-06-29
No changes with Lucid Lynx?

---

### Post by bogoliubov on 2010-12-06
I don't want to bump this thread, but I still can't find a solution to this. I really suspect it is possible to set this up, but can't find any documentation about it...

I'd greatly appreciate any suggestions!

---

### Post by sydbat on 2010-12-06
I don't know if it is possible. Pulse allows you to play different sounds at once on the same card, but getting 2 sound cards to run at the same time might cause more conflict headaches than it is worth.

However, I have 2 sound cards...well one is the HDMI from my video card. Anyway, if I want to have sound through HDMI, I HAVE to change the setting on the on-board sound to input only. Otherwise, all sound wants to go out through the on-board sound card. I have never found any way around this.

So, as I mentioned above, I do not think it is possible.

I do have a couple of questions though...do you dual boot with Windows or OSX? If so, can you send sound individually through both cards at the same time? I suspect you can't, but I have been wrong before!:P

---

### Post by bogoliubov on 2010-12-10
I think it is the same card. All is onboard. Anyway, no dualboot with Windows. I have used Linux/OSX exclusively since 2004...

---

