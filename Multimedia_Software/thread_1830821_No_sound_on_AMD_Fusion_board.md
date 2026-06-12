---
title: "No sound on AMD Fusion board"
date: 2011-08-22
forum: Multimedia Software
---

### Post by CJxD on 2011-08-22
I'm using Ubuntu 11.04 (from a 'minimal installation' disk) on an AMD Brazos AsRock E350M1 motherboard with 7.1 audio + S/PDIF.

I have the Alsa package installed for sure, and I've played about with the curses gui, but I can't get sound to come out.
I have an audio system connected via fibre optic, another audio system connected with the 3.5mm Front(L/R) Audio jack, and HDMI connection to the TV. I get no sound from any of these devices.

XBMC also complained that it couldn't initiate the sound when I used that earlier.

Any known problems with this hardware device, or is it something I need to play with? (maybe install the actual GTK mixer application to set up the sound properly)

Thanks in advance.

---

### Post by CJxD on 2011-08-23
Never mind. Neither XBMC nor VLC had the correct audio device set. It had to be set to the ALSA HD Audio (not the HDMI option) with S/PDIF when available.

---

### Post by tjones00 on 2011-08-23
How did the install go? Any hiccups so far?

I'll be doing an install myself on a couple of Asus AMD C50 fusion netbooks next week.

---

