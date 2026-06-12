---
title: "[Karmic]FL studio WineASIO; no mic"
date: 2010-05-24
forum: Multimedia Software
---

### Post by karl.lensson on 2010-05-24
I have set up FL studio 9(Windows Program), to run on ubuntu. I want to record sound through VOCODER via my mic, whenever i select it as input all i get is static. I dunno why it won't work, may have something to to with my JACK setup, but i know that FL9 sound is first routed through WineASIO, then to JACK. WineASIO is a specially emulated version of the sound driver used when running FL on Windows.

Attached is a screenshot of the inputs i have availible in FL9

:guitar::confused:

---

### Post by shaneo1 on 2011-07-08
Ok My setup is,

Ubuntu11.04, with jackd, wineasio0.9 64bit deb, wine 1.3 and fruityloops9

I have managed to somehow set jack in realtime whilst running wineasio through it.
Set the input in qjackctl to your Mic and output to your sound card. Im using the standard realtek internal one in my laptop, make sure realtime is checked.  

In your sound preferences make sure your input is your microphone, min is a usb ALESIS mono mic.

Now start jackd, and then run FL9, notice on the screenshot I have one system input which is going to FL_ in_1, on the qjack connect window, now in fl9 choose a mic channel in the mixer window and select 'in_1'

This should all work, if you are getting crackling sounds check your qjack messages for overruns, if this is the case then try changing the settings in qjack, turn off realtime, and try again.

---

