---
title: "Logitech Z-5 USB not even listed in the Sound menu"
date: 2011-04-10
forum: Multimedia Software
---

### Post by varelov on 2011-04-10
After cheering the Ubuntu Developers team on the great work they did with hardware recognition, I was suddenly stunned by the silence from my USB speakers this afternoon. Although previously correctly recognized and fully functional, after installing several non- audio updates, the sound from my USB speakers ceased. Moreover, this pair of Logitech Z-5 USB speakers aren't even listed on the Sound menu (System > Preferences > Sound) although lsusb lists them correctly.
I have an embedded sound adapter to which no speakers are connected. My PC runs on Ubuntu 10.04.
What should I do to get the sound through my USB speakers?

---

### Post by varelov on 2011-04-10
asound list command returns "asound: command not found". Meanwhile I installed PulseAudio to be able to choose devices but still no show for my USB speakers.
It was previously working. Now it doesn't. How to bring back sound to these USB speakers?

---

### Post by croaking on 2012-02-15
I'm running into the same problem with Oneiric Ocelot.  Same speakers too, logitech Z5's.  They have been working fine for 2 months since my latest ubuntu install, then just quit the other day, and I can't figure out for the life of me why.  The speakers work fine if I plug them into my Win7 Dell Laptop from work, but not my desktop running 11.10.  Did you ever find out how to fix this??

---

### Post by rgillies on 2012-08-07
My Logitech Z5 speakers were not listed as an output device on a new Ubuntu 12.04 install, yet they worked fine under 10.04. I had a soundblaster Xfi soundcard installed, which worked fine, On a hunch I removed the Xfi card and booted 12.04 from a live CD. Ubuntu found my Z5 speakers!
I'm guessing 12.04 disables USB speakers as the default device. Go figure.

---

