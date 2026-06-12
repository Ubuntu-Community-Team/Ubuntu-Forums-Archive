---
title: "Toshiba U300 microphone not working"
date: 2008-05-28
forum: Multimedia Software
---

### Post by Webspot on 2008-05-28
Sound problems always annoy me on Ubuntu. I never know what to ask to get help, and usually end up giving up or breaking my system more!

I have a Toshiba U300-11V laptop. It has an integrated microphone next to the webcam. I am unable to record from this microphone.

From lspci, I can see my audio device:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

I have also tried hooking up some audio into the microphone port of the laptop. This does not work also. I have tried all of the input sources of the device in the volume control application.

Where should I go from here?

---

### Post by eap1935 on 2008-05-29
Have you tried this?

[http://maxmanders.co.uk/linux/gutsy-realtek-hd-audio-and-the-toshiba-u300/](http://maxmanders.co.uk/linux/gutsy-realtek-hd-audio-and-the-toshiba-u300/)

sudo apt-get install linux-backports-modules-generic

If you try, please reply with whether it works. I'm thinking of buying one of these (it's on sale), but if the mike won't work, forget it.

---

### Post by eap1935 on 2008-05-29
Here's another page offering the same solution.

[http://www.itopen.it/2007/11/22/ubuntu-linux-toshiba-satellite-u300/](http://www.itopen.it/2007/11/22/ubuntu-linux-toshiba-satellite-u300/)

This is probably the right module for hardy tho:

linux-backports-modules-hardy-generic

This module is, according to the package manager, "Backported drivers for generic kernel image". Does anyone who knows what they're doing know why this works and whether it's actually a good thing to do?

---

### Post by Webspot on 2008-05-29
Backports are improved packages that are in a separate repository.

I guess in a previous version of Ubuntu, there was a fix to the audio. I installed that package at the time. This caused my audio out to work. But my audio in has never worked.

I believe there are many variations of the U300 laptop that have many different components. I have the U300-11V.

Thanks for sharing what you found.

I do have to say, apart from the microphone issue, it is a great little laptop. Everything works fine, apart from the mic, after I followed the second website you linked, when I first got my laptop.

---

