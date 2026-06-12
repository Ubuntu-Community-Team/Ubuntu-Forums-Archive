---
title: "Using a laptop as a tapedeck"
date: 2009-01-02
forum: Multimedia Software
---

### Post by vok33 on 2009-01-02
Hi,

I would like to use my laptop as some sort of an modern version of a tape deck so that I am able to record some of my old records, record from (internet) radio, etc.

My major problem is the following:
I use my old Thinkpad X23 with a port replicator which has a line-in and line-out. The line-out works but the line-in is a bit strange.
I have played with the audio setting of the laptop (according to Thinkwiki, the X23 has an CS4299 AC'97 Audio controller), and I was able to feed the sound from the stereo into the laptop and receive it again from the laptop to the stereo so that I could hear it on the stereo. However, I was never able to use, e.g., Ardour3 to record the sound.
Ardour3 records from a device "capture", and to me it seems that "capture" is defined by the sound-setting of the laptop (mic, line-in, aux, etc.) But as I said, I was not able to change these settings. The only input that always worked was the microphone.

The microphone would in theory be fine, but it amplifies the input, which is not good.

So, my major question is: does anyone have an idea, how I can access the line-in? How can I switch between mic-input and line-in?

I use the latest ubuntu from the net, including all updates.

thanks a lot in advance,
best,
Volker

---

### Post by nlz on 2009-01-02
Hi Volker,

I would advice you to try to record with audacity. If you're new to audio editing and ubuntu, ardour can be a bit, uhm, demanding. So just install audacity, probably you can just hit the record button and there it goes.

About the amplification of your mic input: go to the right upper corner of the screen and right click the little speaker and select 'Open Volume Control', then go to Edit > Preferences and select 'Mic Boost', 'Capture' and anything else you like. From that moment on you can select if you boost your mic with 20 dB or not, or at what input/output volume your pic should be.
Watch out for feedback, it can hurt (the effect that the sound can go from speakers into your mic that makes that irritating high sound).

good luck.

---

