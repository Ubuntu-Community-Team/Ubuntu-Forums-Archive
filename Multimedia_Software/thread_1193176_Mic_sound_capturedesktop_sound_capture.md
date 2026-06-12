---
title: "Mic sound capture/desktop sound capture"
date: 2009-06-21
forum: Multimedia Software
---

### Post by Pawcio on 2009-06-21
Ok, this is very nasty.
When I capture my webcam with Cheese it captures audio from my desktop and not mic.
When I run gnome-sound-recorder it captures mic OK.
When I run gtk-recordmydekstop it captures audio from mic.  (hw:0:0) is set in audio options.
There is no slider or switch in gmix or alsamixer that would give me feedback from mic to my speakers. (and I checked A LOT, thoroughly)
When I capture webcam with Kdenlive it starts to give me proper feedback from mic to my speakers (once "Record" button is pressed), however in output clip sound is badly distorted.

I have separate webcam and mic.

Jackd is out of question, because my gstreamer applications (Totem and Cheese) freeze if jackd is running.(however jackeq works ok)

I have Presario CQ50 laptop with HDA Nvidia.
Ubuntu 9.04 Desktop.
Any suggestions?

---

