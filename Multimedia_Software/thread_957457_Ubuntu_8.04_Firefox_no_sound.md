---
title: "Ubuntu 8.04 Firefox no sound"
date: 2008-10-24
forum: Multimedia Software
---

### Post by brian_utd7 on 2008-10-24
Hey guys, about a month ago, I became sick and tired of the fact that I couldn't use Rhythm Box or any other audio device after I had played a flash video. Looking for a solution to this I searched online and found this tutorial [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) . It seemed like it had worked for a lot of people so I decided to follow it. It didn't do much for me except install pulse audio. I can still listen to audio from Rhythm Box and other sound applications but not from anything in Firefox. This is greatly disturbing. I don't want to boot to windows but if I must to watch flash videos then i will. Also, on any flash video's I have to click them before they will begin loading. There is gray play button and it must be clicked to start loading before I can watch a video without any sound. One other thing, I cannon type responses in my hotmail account. Its as if it is a flash based editor and with flash being off or not working correctly I can't type. All of these things are causing me to boot back to windoze and I hate it. Please if you have any suggestions let me know.

Thanks

Mikinley

---

### Post by Yellow Pasque on 2008-10-24
If you're using PulseAudio, did you set all your playback to PulseAudio in System -> Preferences -> Sound and install the libflashsupport package?

---

### Post by maerlin on 2008-10-24
> **Temüjin said:**
> If you're using PulseAudio, did you set all your playback to PulseAudio in System -> Preferences -> Sound and install the libflashsupport package?

I love you :biggrin:

---

### Post by brian_utd7 on 2008-10-27
Yea I have done that and it still doesn't work. I notices that my libflashsupport is version 9, and I think that I have heard of there being a 10. Also when I use pulse audio and look in the volume control playback, there is no stream when i play a video on youtube

---

### Post by lixy on 2008-11-16
I had the same problem for months, ran across this thread, tried enabling PulseAudio in the sound panel and everything works like a charm now.

---

### Post by psyke83 on 2008-11-16
Using libflashsupport to enable PulseAudio support in Flash works, but it makes Firefox *extremely* unstable. You've been warned.

See [bug #192888]("https://bugs.launchpad.net/bugs/192888"), and my [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide for instructions to get sound working properly with PulseAudio.

---

### Post by jakobtritten on 2008-12-04
"I had the same problem for months, ran across this thread, tried enabling PulseAudio in the sound panel and everything works like a charm now." - lixy

Thank you everyone.  This thread directly addressed the problem i was having.  All i had to do was install the plugins (Gnash SWF Viewer and Adobe Flash non-free) using synaptic and then do what Temüjin said.  It worked for me like it did for lixy.

Brian_utd7, i hope you've found the solution for your system.  Every computer is different, it seems.  Good luck.

---

