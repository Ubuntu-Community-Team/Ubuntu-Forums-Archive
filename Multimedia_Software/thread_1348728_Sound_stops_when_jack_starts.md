---
title: "Sound stops when jack starts"
date: 2009-12-07
forum: Multimedia Software
---

### Post by lhbecker on 2009-12-07
Hi 

I have upgraded to Karmic on my lenovo t61. After the upgrade I have also installed the realtime kernel, jackctl, Hydrogen and a number of other apps and did some configs to get my MobilePre USB sound card working. I am trying to set up a Studio.

Now I am able to play music either on my laptop's built-in speakers of via the MobilePre USB sound card. To use hydrogen however, I need to start jack. The moment I do that, the sound to my MobilePre stop and I can play Hydrogen's output only to my built-in laptop speakers. It seems to be some kind of setup/configuration problem, but I could not find any solution in the forums so far.

I am running jackd version 0.116.1 and using jackctl version 0.3.4. Looks like alsa is version 1.0.20. Pulseaudio 0.9.19.

 I will appreciate some help.

---

### Post by sojournerC on 2010-01-04
within jackctl setup you need to verify that you mobilepre soundcard is selected as the one jack is going to use. likely you will use the alsa driver. 

Below that is a selection box in which you can select the hardware. Likely your usb soundcard will be listed as hw:1 or something similar. running cat /proc/asound/modules in terminal will list your cards  and the numbers assigned to them. 

For me, jack always cuts off any other sounds coming from my computer, but if you are recording you should be able to record, listen, etc, anything you need while in jack through ardour, hydrogen etc. jack does this to avoid conflicting sound outputs from different software such as firefox, system sounds or totem.

---

### Post by lhbecker on 2010-01-05
Thanks. I was able to set it up this way. I was not aware that jack would intentionally cut of other sounds. Does this mean that pulseaudio is by-passed by jack? I am trying to understand the relationship between pulseaudio,jack and alsa. Can pulseaudio replace alsa, as it offers much the same functionality as alsa, or does pulsaudio exist in a layer above alsa. What is the relationship between jack and pulseaudio or do the exist next to each other in the same layer with different rolls?

---

