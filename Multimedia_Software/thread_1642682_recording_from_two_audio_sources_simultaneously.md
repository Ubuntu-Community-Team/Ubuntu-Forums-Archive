---
title: "recording from two audio sources simultaneously"
date: 2010-12-10
forum: Multimedia Software
---

### Post by otkaz on 2010-12-10
Hi, I'm trying to set up a call monitoring system for work (I work for a non-profit, we're broke so a commercial solution is out of the question) We have two phone lines, so I built two wiretaps with built in amps. I hooked one of them to the mic input on my ubuntu server. I wrote a script that uses rec from sox with a silence filter. It works perfect for that one line. Problem I'm having is I cant figure out how to record from my second tap. In alsamixer I can only set one recording device even after I installed a second sound card. I was originally trying all this with pulseaudio, but was unable to get any of it to work until I removed pulseaudio. Only way I can think to get this to work is to plug both of the taps into linein and have each of them record on one of the stereo channels, but this is not preferable. I would like to be able to record each phone call on either line into its own separate file even if both lines are in use at the same time. It would be very nice if I could do this all on one computer (as again were broke and don't have spare computers laying around). Another thing I would like, but this part isn't as important right now. If my script is running and I try to use "ssh [host] dd if=/dev/dsp | dd of=/dev/dsp" to listen in live it tells me the hardware source is in use. Anyone have any ideas or directions they could point me?

---

