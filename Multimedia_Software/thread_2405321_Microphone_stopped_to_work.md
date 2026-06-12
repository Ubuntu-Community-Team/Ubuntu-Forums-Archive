---
title: "Microphone stopped to work"
date: 2018-11-04
forum: Multimedia Software
---

### Post by alain.roger on 2018-11-04
Hi,

on my mon's laptop there was Kubuntu 18.04 and till yesterday morning everything was working great.
for an unknown reason, yesterday evening we tried to do some video call and her microphone was not working anymore.
hangout, skype, facebook... everywhere webcam works and speakers too.... but microphone is not working anymore.

i removed alsa-base pulseaudio and reinstalled them but nothing helped.
i upgraded her linux dist. to KUbuntu 18.10 so with new pulseaudio 12.2 but still the same issue.

i checked alsa-mixer, everything seems ok.

INTERNAL MICROPHONE is not working anymore.

Any idea how to check what;s going on ? because i do not believe the microphone is out of order suddenly.

thx

---

### Post by alain.roger on 2018-11-05
this is the alsamixer report:
[IMG]http://i65.tinypic.com/2a8pb9g.png[/IMG]

---

### Post by alain.roger on 2018-11-05
this is the alsamixer report:
[IMG]http://i65.tinypic.com/2a8pb9g.png[/IMG]

chipset for sound card is [COLOR=#333333][FONT=Ubuntu]ALC269VB[/FONT][/COLOR]

---

### Post by Adam_GUI on 2018-11-05
It looks like your microphone is muted in alsamixer.
Right arrow over to the "Mic" bar and press the M on your keyboard.  This should un-mute the mic.  You should be good to go afterward.

---

### Post by alain.roger on 2018-11-06
i saw hat too and even if i press M to activate Mic, i have the same result.... Mic does not send any signal so no voice over video call e.g.

---

### Post by alain.roger on 2018-11-12
Nobody knows ?

---

