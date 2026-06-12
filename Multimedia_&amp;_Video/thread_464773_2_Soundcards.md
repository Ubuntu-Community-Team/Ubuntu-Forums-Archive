---
title: "2 Soundcards"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by Nighto on 2007-06-05
Hi,
I have Ubuntu Feisty running on my Acer TravelMate 2480 notebook, with the crappy Realtek ALC883 audio chip.
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```
I'd like to listen to some music using headphones, but the soundcard headphone jack doesn't works. I've googled for a solution, but found none - it's not an ALSA related bug, it's a hardware's, because it happens with Windoze users too.
So i bought a cheap USB soundcard:
```
Bus 002 Device 002: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
```
which works OK as a second audio card. 
But, **how can I make it be the primary card?** I can only get some sound from it configuring each program (for instance, i like to listen to music with Amarok, but I can only find an option to change soundcards in XMMS). Disabling the sound card in BIOS is not an option, because there's no such possibility.
Also, it'd be great if the onboard soundcard would be disabled only when I plug the usb one (maybe a script to be run when it's detected?) and re-enabled when unplugging.. that'd be perfect :guitar:

Thanks in advance,
Nighto

---

### Post by Pragmatist on 2007-06-05
Have you tried turning it off in the BIOS?

---

