---
title: "jack and ATI HDMI"
date: 2010-10-01
forum: Multimedia Software
---

### Post by RasterBurn on 2010-10-01
Hello i am wondering how i can get Jack to work with my ATI HD video cards as that is set as my default sound card in Ubuntu 9.10 64bit (All audio and Video pass through 1 HDMI cable to the tv) this setup up to now works for everything aside from Jack

I would like to use my rear microphone input jack as the instrument input, i have created a cable to allow me to plug both the guitar and bass guitar in and use them on different channels of the microphone input, this cable works perfectly as per testing states...

In the process of testing i have been able to feed input 1 + 2 (microphones hw:0 for back input, hw:0,0 for front input) thru to output 1 + 2 (front headphone jack, rear line out jack) this would be perfect if i was using a normal screen and speakers but thats not the case

ok so the last part of things is that i cant just dig in the closet and hook up my logitech 5.1 computer surround system (the land lady complains about the bass) I also can not just run out and purchase a set of computer speakers, pretty much anything that will include spending money is out of the question (im cheap and dont make much of a wage)

ok so the dilema is simple, the adapter to feed the tv from the computer soundcard (hw:0) is the same size as the adapter to feed input, the 2 adapters are too wide to plug them both into the back at the same time, meaning if i want audio through the tv i need to plug input into the front (hw:0,0) i dont like this idea (have had 1/8" plugs break off inside the jack) in order for me to plug the input into the back (hw:0) i need to plug some headphones into the front (i dont like headphones to begin with)

according to jack control my HDMI outputs are labeled as:
hw:2
hw:2,3
hw:3
hw:3,3

other then that, i have tried all the output methods using jack control and none of them seem to effect anything leaving me with the audio I/O on hw:0 and hw:0,0

is anyone familiar enough with jack to be able to help me get things working so that i can feed the instruments in through hw:0 and out to the tv through the HDMI cable?

---

### Post by RasterBurn on 2010-10-03
Bump!

---

### Post by RasterBurn on 2010-10-08
bump!

---

