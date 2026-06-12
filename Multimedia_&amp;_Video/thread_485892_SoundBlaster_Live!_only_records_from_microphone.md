---
title: "SoundBlaster Live! only records from microphone"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by jdburto on 2007-06-27
I am running Ubuntu 7.04 and I am trying to get audio recording working.

I have a SoundBlaster Live!. lspci gives the following information.

01:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 03)
01:07.1 Input device controller: Creative Labs SB Live! Game Port (rev 01)

The problem is that only the microphone works. Line in does not work. CD input does not work. 

I have tried changing the settings in alsamixer and kmix, but nothing changes. The soundcard will only recognize input from the microphone.

I have upgraded the alsa-driver, alsa-utils, and alsa-lib to 1.0.14. It didn't work.

I have tried several other soundcards, including the onboard NForce2, a SoundBlaster Live! value, and a Forte Media FM801. I could not record anything from them.

This is probably a simple configuration problem, but I can't find any information on how to fix it. Any help would be greatly appreciated.

---

