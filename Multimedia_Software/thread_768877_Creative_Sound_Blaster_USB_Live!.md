---
title: "Creative Sound Blaster USB Live!"
date: 2008-04-26
forum: Multimedia Software
---

### Post by Krazeel on 2008-04-26
Hello,

I just noticed that I can't manage to reproduce any sound through my usb Sound Blaster device, as I do in Windows with no problems. I tried switching through different devices at the "Volume Control" settings - literally traduced from Spanish - but I get no sound from any player, no matter the type of file.

So I decided to ask for your help and just to make things a bit easier I figured that I should tell you my settings: 
- The speakers are connected directly to the SB device, which you can find here: [http://www.soundblaster.com/products/product.asp?category=1&subcategory=206&product=10702]("http://www.soundblaster.com/products/product.asp?category=1&subcategory=206&product=10702")
- I configured a few things at the Sound Preferences panel which can be accessed from "System > Preferences"; these are my settings:

[FONT="courrier New"]Sound Events: Autodetect
Music & Movies: Autodetect
Sound Conference:
-Sound playback: Autodetect
-Sound recording: ALSA
Default Mixer Tracks: 
-Device: SB Live! 24-bit (Alsa mixer)
[/FONT]

--This was also literally translated from spanish so I'm not sure if it's totally right.

So there it is. I would really appreciate your help.:popcorn:

Cheers

---

### Post by ninjamonkey26 on 2008-10-08
wow my first post where I can help someone with ubuntu 8-).

So under the system->preferences->Sound

change those settings from autodetect to USB Audio. That should be the setting under Sound Events, Music and Movies, and Audio Conferencing->sound playback.

Then under default mixer tracks->Device should be SB Live 24-bit External(Alsa mixer)

---

### Post by vdfbelial on 2008-11-29
Hello there. I have the same audio card and am using Hardy Heron. I managed to get the sound to my home theater but unfortunately only the front speakers are working (no subwoofer, no center or rear speakers).
What else can be done ?

---

### Post by GordonJ on 2008-11-30
Hi Krazeel -I've got the same sound card. I managed to get the sound blaster working by switching off the on board sound on the motherboard. Hope this helps.
GordonJ

---

### Post by vdfbelial on 2008-11-30
> **GordonJ said:**
> Hi Krazeel -I've got the same sound card. I managed to get the sound blaster working by switching off the on board sound on the motherboard. Hope this helps.
GordonJ
Do you use it in 5.1 mode ? Does your subwoofer work ?

---

### Post by GordonJ on 2008-12-01
Hi - I do not use surround sound speakers only stereo ones so cannot give an answer on that one.  The computer is in a small room so spaced is at a preimium.
GordonJ

---

