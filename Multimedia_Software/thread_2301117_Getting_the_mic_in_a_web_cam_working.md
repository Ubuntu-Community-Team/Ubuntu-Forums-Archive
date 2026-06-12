---
title: "Getting the mic in a web cam working"
date: 2015-10-30
forum: Multimedia Software
---

### Post by oygle on 2015-10-30
Have been using Skype with headphones. Works fine, web cam as video and headphones as audio. Now I need to use the PC speakers as output and the mic in the web cam as input.

The speakers work fine, but even though I have tried using Pulse to test the mic in the web cam, can't get it to work.

Possibly I don't have the 'full' Pulseaudio setup, to use for trouble shooting. The computer is about 7 years old, has an onboard sound card, and the webcam is USB.

Any thoughts please ?

---

### Post by oygle on 2015-10-30
Installed pavucontrol and I can see the meter moving on the web cam microphone. So it seems it is working. 

Just **NOT** in Skype.

Edit: I can even see the microphone meter levels moving in Pulseaudio/Volume Control, but it still fails the Skype sound test, on the mic only. Can hear sound quite fine in all apps and Skype.

---

### Post by oygle on 2015-11-01
Skype was the problem. Saw many posts from others who had microphone problems with Skype. Seems since Microsoft took over Skype, they changed from ALSA to Pulse, but can't fix the mic problems. Am using 2 headphone sets by way of adaptors. The webcam mic is turned off.

Changed over to Google Hangout. Too many problems with Skype and it's not open source.

---

