---
title: "multiple outputs sample rates?"
date: 2006-04-08
forum: Multimedia &amp; Video
---

### Post by rnton on 2006-04-08
Hello,
This is my first post. I switched to Linux about a month ago for live music, and general computing. I have a couple of questions about my setup, so if anyone can help it would be greatly appreciated.
I am using Dapper with Fluxbox on a Sony Vaio.
I just plugged in an emagic emi 2|6 usb soundcard, and was deighted to see it work instantly! At least the outputs 1 and 2. Could anyone possibly tell me how to make use of the other four outputs.
In the Jack Connection Kit I only get alsa pcm out 1 / 2.
Also could anyone explain why Jack always defaults to 48000kHz? It is a mystery to me. I have tried changing various config files (asound / default.conf) to 44100kHz, but whatever I do Jack always reverts! This is crappy because I have years of sampling at 44100kHz.
Many programs dont have a problem playing back (they seem to convert?), but some (sooperlooper) plays the samples too fast and others (jackbeat) alias the samples.
Thanks in advance for any ideas.

---

### Post by dolson on 2006-04-08
QjackCtl should be able to help you with settings, but I'm not sure about the output thing.

---

### Post by rnton on 2006-04-08
Thanks very much. Unfortunatley whatever sample rate I use in Qjackctl, it still runs the server at 48kHz.
I thought at first it was just my internal soundcard, but i have the same issue on the emi 2|6 as well?
Well thanks anyhow.

---

