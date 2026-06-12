---
title: "Capture PCM on hda-intel ALC 880"
date: 2008-05-29
forum: Multimedia Software
---

### Post by gidra on 2008-05-29
Any idea how to record sound from PCM channel on my hda-intel ALC 880 soundcard? (bit of a newb here)

---

### Post by gidra on 2008-05-30
Is it possible at least on linux or do i have to revert back to windows?

---

### Post by gidra on 2008-05-31
anyone ?! :confused:

---

### Post by gidra on 2008-06-03
bump :(

---

### Post by gidra on 2008-06-03
bump :(

---

### Post by markbuntu on 2008-06-03
Sound recorder should do that, or any other sound capture app. Just open it and choose file,new and you will get a choice of where to record from. If your volume control is set to master and you choose mix it will record everything going to you speakers.

It works for me. If it doesn't work for you come back and let us know and we can try some other things.

---

### Post by sumdog on 2008-11-03
I've got an Index HDA and the ALSA driver gives me no such options. In the Gnome Volume Control panel, I only have the PCM listed as a playback option. The recording options have Capture 1 - 3 and Digital, and there are options for setting each of the sources to either Line, CD, Front Mic, or Mic.

I guess I could get a loopback cable and pump the audio back in, but that feels like janky. Is there any native way to do this?

Sumit
[http://penguindreams.org]("http://penguindreams.org")

---

### Post by clubsoda on 2009-03-31
Bump for an ALC889A on an AMD 780G mobo.

No PCM capture device in alsamixer, only Mic, Front Mic, Line or CD.

Is this a DRM-inspired infarction of HD audio or do we just need to tweak our drivers a bit?

---

### Post by Ole Juul on 2009-07-04
I've been asking a similar question here "PCM missing in 8.04". It's looking like we're going to have to live with it. :(

---

