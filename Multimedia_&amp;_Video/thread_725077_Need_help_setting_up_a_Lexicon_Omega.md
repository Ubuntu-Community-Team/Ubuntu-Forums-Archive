---
title: "Need help setting up a Lexicon Omega"
date: 2008-03-15
forum: Multimedia &amp; Video
---

### Post by unreal4evr on 2008-03-15
Hello, I recently installed Gutsy on my comp and I'm having trouble getting my Lexicon Omega recognized by ALSA. I want to be able to use it with JACK along with Ardour/Rosegarden but ALSA isn't recognizing the audio ports. I can get the MIDI ports to work but for some reason ALSA can't recognize the USB Audio ports. I would really appreciate some help with setting up ALSA to recognize the usb audio.

---

### Post by dillinger417 on 2008-05-20
I have the same problem.  Seems like people have had success but I don't think I have JACK setup properly yet. Trying to get Sound Blaster Live! 24-bit (CA0106), ALSA, JACK, Ardour working on a AMD64 gutsy install w/ the Ubuntu Studio additions.

*Edit* I now have a working setup. :) The Lexicon Omega really is plug-n-play if you know JACK- which I didn't but am learning. In jack I have my input and output device set to HW:2 (Lexicon Omega), and using ALSA_pcm:capture_1 as the input for the tracks (Ardour). That's all I really had to do. ALSA seems to insist that I use 2 periods- so that is different then the 3 or 4 I've seen recommended.  Also, I can't currently use realtime option in JACK although i'm using the real-time kernel.  After a quick google it seems to be an authentication issue w/ the sound group.

---

