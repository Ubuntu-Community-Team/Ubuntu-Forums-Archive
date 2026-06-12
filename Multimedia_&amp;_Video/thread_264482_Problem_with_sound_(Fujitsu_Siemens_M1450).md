---
title: "Problem with sound (Fujitsu Siemens M1450)"
date: 2006-09-24
forum: Multimedia &amp; Video
---

### Post by gejr on 2006-09-24
Hi all,

I've just installed the latest Ubuntu version 6.06, but I can't figure out why the sound isn't working properly. It works perfectly if I plug a headset into the laptop, but the speakers on the computer isn't working. I had WinXP on here before, and the sound worked well there, both in the speakers and in my headset. Can anyone please pinpoint why the speakers won't work in Ubuntu, but the headset will? Thanks for reading!

-gejr

---

### Post by gilgongo on 2006-09-24
This is just a hunch, but try running "alsamixer" from a command line. That will bring up a mixer app (that looks like it was made in about 1980). If any of the vertical bars are at zero or have "MM" under them then it's possible the speakers may be muted - you can unmute them by using the arrow keys to navigate and hitting the "m" key on the keyboard.

---

### Post by gejr on 2006-09-25
I finally found a solution. I played around with the settings in alsamixer and discovered that if I unmuted the "Side"-bar the laptop speakers started playing music. Anyone know why this is?

---

### Post by gejr on 2006-09-25
Problem is..It's difficult to adjust volume when its like this, i have to open volume control or alsamixer to adjust the "side" volume. Is there somewhere possible to change the standard volume from PCM to Side or even better, make it so that PCM is the volume bar for my pc speakers?:=)

---

