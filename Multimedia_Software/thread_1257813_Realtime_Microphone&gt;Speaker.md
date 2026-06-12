---
title: "Realtime Microphone&gt;Speaker"
date: 2009-09-04
forum: Multimedia Software
---

### Post by Magma828 on 2009-09-04
This is something quite simple which must be possible, but I've never known how to do it.

I have connected my microphone to the microphone port, and powered speakers to the speaker port. How do I set up the soundcard/driver/operating system/whatever to automatically send the microphone input to the speaker output, while also outputting any other sounds which happen to be playing. All the hardware works fine. I can record sounds from the microphone and play them back later, but I want this to just relay the sound instantly.

The only way I've ever done something like this before was by using SAM Radio on Windows which wasn't exactly a clean way of doing it anyway - I just used the software to make the mike-in play out which had to be running all the time.

---

### Post by SoftwareExplorer on 2009-09-04
I think it is the default for the operating system to do that. Do you have the microphone unmuted?

---

### Post by dudude on 2009-09-04
YMMV, but the method I found to output input is to enter this:
```
pacat -r | pacat -p
```
into a terminal.

A similar method is to do:
```
arecord | aplay
```
but this has quality issues.

This is working for me in Karmic, but I do not know the details of your setup. Both of the above methods give me somewhat random amounts of lag though, so again, YMMV.

I do not know of simple GUI based method of doing what you are trying to do though.

---

### Post by Magma828 on 2009-09-05
Thanks for the response dudude.

Pacat gave the error "Connection failure: Connection refused", and arecord worked nicely with a tiny bit of lag. This is all I wanted to do, thanks so much. If anyone else knows of a method with no lag feel free to post, but this will be fine for now :)

---

### Post by capla on 2011-04-19
The program you need is 'GNOME ALSA mixer':
which gives many more audio options including the ability to enable or disable the muting of the mic input.  I have tried ticking off the mute on the microphone input and this has resulted in the sound coming straight through the speakers with no noticeable lag (real-time playback).

---

### Post by SoftwareExplorer on 2011-04-28
Ok Thanks!

---

