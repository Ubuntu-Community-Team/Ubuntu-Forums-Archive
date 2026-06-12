---
title: "Sound Card Isn't recognized: on board audio default on install"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by bluetang on 2007-10-27
Asus P5B Deluxe
Core 2 Duo 6400
2GB
7600 GT 512mb
M-Audio Audiophile 2496 (ice1712)

I'm starting to be bugged because I can't seem to get to the bottom of a very basic issue.

I'm a musician and podcaster. I've been trying to get Ubuntu to recognize my full-duplex recording card (M-Audio Audiophile 2496 (ice1712)) since I put this system together. 

Instead the on-board audio, though working fine, is loaded. It sounds like crap next to the 2496. I've tried editing the alsa.conf file in order to get the card and driver to load. I've read that the 2496  has good linux support.. 

I suck at the command line and get hung up. I know that it's key. I did go to the alsa project web site, found the page for my card, applied the commands, but couldn't seem to make to happen with my distro. Anyone?

---

### Post by disturbedite on 2007-10-27
you prolly need to disable the onboard sound "card" in your bios.  most bios have an option for that sort of thing.

---

### Post by bluetang on 2007-10-30
Thanks for the reply. Nope. My MB must be different because I've tried installing with ob audio off via the bios. No dice. the ice1712 driver still doesn't load. I've tried editing alsa.conf. Someone?

---

