---
title: "Onboard Sound produces high frequency noise"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by pirrax on 2007-09-25
My Onboard Soundcard produces on Dapper and Feisty an annoying high frequency noise through the monitor box.  If Ubuntu starts and playing the login sound, it is accompanied with an unpleasant hf noise.  It is just like a feedback, if a microphone is located too close to a loudspeakers.  Changing the volume level causes the soundcard doesn't work anymore.  I tried with > sudo alsactrl restart but it won't work.  Only after a restart, I get my soundcard working with annoying hf noise again.  How can I restart my sound module without rebooting my PC?  My sound card is identified as > 04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller by entering > lspci | grep Audio in the console.

---

