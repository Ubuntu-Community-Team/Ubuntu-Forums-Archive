---
title: "Trying to record form line-in: crappy sound. Voice is ok."
date: 2007-11-16
forum: Multimedia &amp; Video
---

### Post by tirengarfio on 2007-11-16
HI,

i'm trying to record some from my cd player (discman)  to ubuntu.

When i connect this discman to the line-in of the computer, i hear the sound of the tape recorder on the speakers of my computer but the sound is crappy.

I get recording it with Sound Recorder but when I play it, the sound is still crappy.

I have tried selecting Mic , Front Mic  and Line on Alsamixer.

Other clues:
- When i record my voice from a microphone the recording seems Ok, but im not sure, maybe it is a bit crappy also.
- when i open puredata and select Media>ALSA it shows this continously:

"tried but couldn't sync A/D/A"

Any idea?

br.
GARFF

---

### Post by Yellow Pasque on 2007-11-17
What kind of sound card do you have? Sometimesd, OSS  supports features or has better support for a card (and more rarelu, IMO) ALSA works better,

---

### Post by tirengarfio on 2007-11-17
Hi,

here you have all the information i find about my sound card (it is a 1mb .ogg movie file):

[http://www.filecrunch.com/file/~h2edkb](http://www.filecrunch.com/file/~h2edkb)


One more thing: when i go to System>Prefrences>Sound>Devices>Sound capture, I found these options:

STAC92xx Digital
STAC92xx Analog
ALSA
OSS
Sonido de prueba (Sound probe)
Silencio (Silence)

I tried these:

STAC92xx Analog
ALSA
OSS

and all three record but crappy from the line-in.

---

### Post by tirengarfio on 2007-11-17
Ok, 

It was a problem in alsamixer: getting down the levels of Capture (in my case I have three columns called Capture) solves it.

To open alsamixer, go to the terminal and type "alsamixer".

GARFF

---

### Post by tirengarfio on 2007-11-27
One more: take care with the volume of the source (mp3 player, cd player, radio, etc). Try it taking the volume to the lowest levels.

---

