---
title: "Unable to get a response from USB interface into Ardour 6"
date: 2020-06-06
forum: Multimedia Software
---

### Post by Music_Guy on 2020-06-06
I am not able to see any signal from my USB interfaces in Arour 6.0.0 installed on Ubuntus 20.04.  I tested a 1st generation Scarlett 2i4 and a Behringer UMC404.  I tested at Kubuntu, Kubuntu with Ubuntu Studio 20.04 ppa and apps installed, and Ubuntu Studio 20.04.  I tried connecting the Scarlett directly to Ardour in the Audio/MIDI setup screen, and through JACK and qjackctl as well as JACK and Carla.  I tried selecting the Scarlett as the sound card in the alsamixer, and tested the other sound card choices also.  I can see a response in pulse audio input (pavucontrol).  I can see the Scarlett after lsusb, aplay -l, and cat /proc/asound/cards.  I tested this on both a Dell desktop and a Dell laptop.  I have also been searching on setting up Carla, JACK, and qjackctl.  I've used settings recommended in the Ubuntu Studio manual.  Finally I have no problem seeing and recording from either the Scarlett or the Behringer in Ardour 5.12.  Any ideas as to how to fix this?

---

### Post by Music_Guy on 2020-06-10
I resolved the problem I was having with Ardour 6.  In both Ardour 4 and Ardour 5, one could see the strength of the signal going into a track by connecting the track to the proper input (for example, USB interface), then doing whatever to cause a signal (sing into a microphone, strum a guitar, play a note on a keyboard or bass, etc.)  There was no need to arm the track in order to see a response.  Apparently there was some change made to Ardour 6 whereby one must arm the track in order to see a response on the meter on the track.  Once I armed the track, I easily saw a response to the input into my USB device.  I did not have to use either JACK or Carla; it worked with ALSA.

---

