---
title: "HP G61-448CA and Mic"
date: 2011-05-24
forum: Multimedia Software
---

### Post by sssjkn on 2011-05-24
Ugh, I hope I'm not beating a dead horse by now. Also I'm new here, hi all!

I have the abovementioned laptop, and it has a built-in mic. The soundcard is HDI ATI SB, the chip is IDT 92HD75B2X5. I'm on Maverick. I upgraded my ALSA to 1.0.24. I don't remember whether or not my mic worked on Karmic. I know it works perfectly fine on my dual-boot Windoze.

After I start the computer, the mic only works once, and that recording has a lot of noise. After one use, the little microphone gauge in the Sound Preferences becomes black and disabled (it's working before) and my mic stops working.

In alsa-base, I've tried (snd-hda-intel):
- model = hp-laptop, auto, g61 <= they all work equally poorly
- position-fix = 1 <= currently using, no difference either

That's all, I think.

EDIT: Ubuntu Audio Dev Team PPA fixed it eventually.
[HTML]sudo add-apt-repository ppa:ubuntu-audio-dev/ppa 
sudo apt-get update[/HTML]

---

