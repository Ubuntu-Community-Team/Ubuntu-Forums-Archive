---
title: "Sound Dialog Problem"
date: 2006-11-13
forum: Multimedia &amp; Video
---

### Post by Megatog615 on 2006-11-13
I get the following when I select anything other than OSS for sound capture(which also does not actually capture sound at all):
```
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.
```
How do I fix this?

Also, does anyone know how to get dsnoop working on the C-Media PCI CMI8738-MC6?

---

### Post by czer323 on 2006-11-17
Same issue.

---

### Post by domkle on 2006-11-27
I have the same issue here after I disconnected my usb headset,
any idea would be very welcome

---

### Post by domkle on 2006-11-29
OK Guys, I solved it on my side.
Nailed it down to some configuration problem with alsa

Whet worked for me is to get rid of the current
~/.asoundrc file
then into system->prefs, sound and put alsa again in input

good luck

---

### Post by thepizzaking on 2006-12-09
> **domkle said:**
> OK Guys, I solved it on my side.
Nailed it down to some configuration problem with alsa

Whet worked for me is to get rid of the current
~/.asoundrc file
then into system->prefs, sound and put alsa again in input

good luck

I'm having the same problem, but unfortunately this solution is impractical for me as I use my ~/.asoundrc file to define which sound output device I want to use.

---

### Post by ilantz on 2007-04-08
thanks for the lead :)
worked great.

---

### Post by king20878 on 2007-04-12
That worked perfectly.  Thanks for posting the fix!  :)

---

### Post by Chilleh on 2007-04-16
I am having this exact same problem, however no ~/.asoundrc file exists. Any ideas? I really would like to figure out why I can't get my mic to work in any application.

---

