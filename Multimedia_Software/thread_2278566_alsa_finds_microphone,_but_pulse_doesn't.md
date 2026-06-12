---
title: "alsa finds microphone, but pulse doesn't"
date: 2015-05-17
forum: Multimedia Software
---

### Post by neverminder on 2015-05-17
I've installed Ubuntu 15.04 on my Pixel LS laptop with a patched kernel ([https://github.com/tsowell/linux-samus](https://github.com/tsowell/linux-samus)). Problem is - pulseaudio (pavucontrol) doesn't recognize the microphone - "no input devices". If I run alsamixer, mute speakers enable headphones and unmute stereo microphones - I can hear microphone input in my headphones (more details: [https://github.com/tsowell/linux-samus/issues/4](https://github.com/tsowell/linux-samus/issues/4)).

  How can I make pulse recognize my microphone? Can someone at least nudge me in the right direction? Thanks.

  alsa-info dump: [http://pastebin.ca/3004491](http://pastebin.ca/3004491)

---

### Post by dino99 on 2015-05-18
Recently pulseaudio has became very sensitive to the bios setting (set 'hda' not 'ac97') and the plugged jacks have to be into the right place (same colors)
That is what i've also learned the hard way ;)

---

