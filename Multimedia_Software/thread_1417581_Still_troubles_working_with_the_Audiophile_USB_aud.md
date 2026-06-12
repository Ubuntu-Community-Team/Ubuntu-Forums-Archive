---
title: "Still troubles working with the Audiophile USB audio card"
date: 2010-02-27
forum: Multimedia Software
---

### Post by el.einad on 2010-02-27
Hello to everyone,
I'm trying to work with this usb audio card but, when I try to capture from the microphone, I just obtain white noise. I'm using Ubuntu 8.04.
I've already read many resources, such as the thread found at [http://ubuntuforums.org/showthread.php?t=282217](http://ubuntuforums.org/showthread.php?t=282217), 
the kernel documentation file (/usr/src/modules/sound/alsa-kernel/Documentation/Audiophile-Usb.txt) and the guide at [http://people.uleth.ca/~daniel.odonnell/Blog/using-the-m-audio-audiophile-usb-digital-audio-interface-with-linux](http://people.uleth.ca/~daniel.odonnell/Blog/using-the-m-audio-audiophile-usb-digital-audio-interface-with-linux)

The explanations said that I have to:
-turn off my audio card
-remove the snd-usb-audio module
-reload the module with modprobe snd-usb-audio index=1 device_setup=0x09 (parameter can be changed properly)
-turn on the audio card

I've done this procedure, just changing the index number in index=2 (with "cat /proc/asound/cards" my audiophile has been found at the index 2). Doing so, in fact, the card is recognized by the system and I can choose it through jackctl as hw:2,1
But,nonetheless, when I try to record from the mic with Ardour I only obtain white noise...
Any suggestion??
Thank you in advance...

---

