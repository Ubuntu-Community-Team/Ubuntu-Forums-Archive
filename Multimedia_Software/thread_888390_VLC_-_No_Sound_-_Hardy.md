---
title: "VLC - No Sound - Hardy"
date: 2008-08-13
forum: Multimedia Software
---

### Post by ramontayag on 2008-08-13
Hey everyone!

I don't know why it doesn't work and I need the community's help :)  The video is fine but there's no audio that comes out.  It really sucks coz I have to boot into Windows to watch videos. :(

I've already installed the codecs as described in an [UbuntuGuide wiki]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Codecs").

I've also started it via command line "wxvlc", then opened a file.  No error messages about audio.

Thanks!

---

### Post by hades_6_6_6 on 2008-08-13
Do you always have the problem, or only when Firefox is running in parallel?

---

### Post by ramontayag on 2008-08-13
Oh!  I just had to turn off Firefox and it started playing sound.  However, VLC audio still worked after starting FF again!

Thank you :)  I hope when I reboot and all the sound will still stay.

---

### Post by blom on 2008-10-03
My guess is that it was OK after a reboot? (for a while at least)

This (apps sharing sound device) has been a frustration of mine for a VERY long time.  It seems ridiculous that Windows has managed it OK since the dawn of time and yet various distros still to this day are still trying out different sound servers to sort it out and there are thousands of different guides on how to get all your apps to work and play nice.

(I'm only commenting as I still have this problem with 8.10 and was searching the internets to figure out which text files might need messing with this time).

---

### Post by Roasted on 2008-10-03
Blom - I've had a slew of troubles with my sound, playing sound through certain audio programs as well as youtube on firefox, only to find out it was a simple setting that allowed the apps to run in parallel and play nice.

Offhand, I forget what it was in VLC... But I'm sure it's similar to Amarok, and I know in Amarok I set my engine to autodetect, whereas I actually use alsa on my system. I can run YouTube in FF and Amarok at the same time without any issues.

So, granted, Windows has their sound server hammered out. But Windows has also been around since... when? Whereas Ubuntu came out in 04. To top it off, at least there are extra plugins available by default, which enable somebody like me to run my apps in autodetect and let the OS figure out what it wants to do, therefore giving me the ability of listening to YouTube and Amarok at the same time... not that I'd ever need to. :guitar:

---

### Post by markbuntu on 2008-10-03
If you want you get ALL your applications sharing the sound card, you can read my guide here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

