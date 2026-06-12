---
title: "flash audio lag/latency"
date: 2009-05-02
forum: Multimedia Software
---

### Post by sototallycarl on 2009-05-02
I am sure this is an issue that more than I experience. Its mildly annoying, but in my case sort of hindering actual work as I am a Flash developer. Flash Player on Linux (ubuntu) seems to lag about .5 seconds before it outputs audio and then after it programmaticly should have stopped playing.

Simple example, watch a youtube video. Audio and video work, but the audio takes a half second to output. Its in perfect sync, but just slow to output. This is very evident on a site with a sound effect synced to an event such as mouse events or an animation with sound synced.

Is there a way around this? It seems Flash Player requirements mention ALSA specifically. I am still a noob when it comes to the real inner workings of Linux and audio libraries/frameworks/systems but audio just seems like a real confusing mess.

For reference Banshee and other system sounds and VLC play with very little latency which I can't even notice. My hardware is a Sigmatel 9228 in a Dell M1330 laptop.

Thanks
-Carl

---

### Post by runokiab on 2009-05-07
I have the same problem with Ubuntu 8.04.2., Firefox and Flash 10.0 r12.

---

### Post by sototallycarl on 2009-05-07
I am starting to think its a sound system thing as Wine has the same exact issue. As far as I can tell my Wine Configurator is stuck on ALSA and the Flash specs mention ALSA specifically. Everything else is set to Pulse system wide.

Maybe a custom compile would do ALSA some good?

edit: Ubuntu 9.04 32bit, Firefox, Flash 10 r22 i think.

---

### Post by syntaxer on 2009-06-04
I have this problem with every version of Flash in every release of Ubuntu. In my case, Flash videos are in perfect sync (not just YouTube but any FLV video I play in Flash Player). But all events events which trigger sound effect, such some action in a flash game, are late cca half a second - just as Carl mentioned. I guess it has to do something with buffer length, but I don't understand it.
I wonder whether it could be hardware related since this problem doesn't seem to be widely documented.

I use onboard AC97 codec, Intel 82801I (ICH9 Family) HD Audio Controller to be exact (Asus P5KC motherboard).
I run fresh installation of Jaunty, Flash Player from adobe-flashplugin package, version 10.0.22.87-2jaunty1

---

### Post by sototallycarl on 2009-06-04
Its a shame there isn't enough info out there to debug this as this single bug literally forces me to use Mac OS as my production environment and ultimately 80% of the time OS. Its got to be a sound system thing as I have come across this on my eee900, iMac, alienware and dell 1330 running 8.04 - 9.04. All have different hardware speeds and audio cards ranging from super cheap to pretty decent and no matter what I do, its always slow when starting audio processing. No biggie on movies, little bit of a problem with animation synced sound effects like a character animation.

Thank you Adobe and your closed ways.

---

### Post by organelas on 2009-07-13
Any luck, ppl?

I could not find any solution for this problem also...

---

### Post by igorzwx on 2009-07-13
It is 100% Pulse, the evil.

---

### Post by organelas on 2009-07-13
Did you manage to adjust pulse settings and solve the issue, igor?

---

### Post by igorzwx on 2009-07-13
Yes!
Just removed Pulse and ALSA, and installed OSS4.

But this should be done carefully

read this story first:
[http://ubuntuforums.org/showthread.php?t=1207636](http://ubuntuforums.org/showthread.php?t=1207636)
[http://ubuntuforums.org/showthread.php?t=1207636&page=2](http://ubuntuforums.org/showthread.php?t=1207636&page=2)

But you have to decide yourself what is better for you.
We discussed this 12 hours ago on thi forum

---

