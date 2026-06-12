---
title: "HP dv7 laptop crackling sound on shutdown"
date: 2009-06-11
forum: Multimedia Software
---

### Post by GilbertEvanG on 2009-06-11
Hello,
I recently purchased a HP dv7 series laptop and am dual booting with windows vista.

Originally Ubuntu had no sound whatsoever, but after following the instructions here: [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568) I was able to get sound working. (ALSA was updated to version 1.0.20 I believe)

However, now whenever I shutdown Ubuntu, I get a loud crackling sound for about a second right before the machine actually powers off (ubuntu starts shutting down, you hear the sound near the end, and then it actually powers off).

My audio device is the following: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

I'm pretty new to linux, so any suggestions would be appreciated.
Thank you.

---

### Post by GilbertEvanG on 2009-06-11
bump

---

### Post by GilbertEvanG on 2009-06-11
While trying to fix another sound issue, I actually fixed this inadvertently.

I'm not entirely sure what I did, but while trying to fix something else I installed the asoundconf-gtk package and set the default card to "Intel", and I also changed all of my sound playback devices in System > Preferences > Sound to be "ALSA - Advanced Linux Sound Architecture" instead of "Autodetect".

Some combination of those changes seemed to fix my problem. I no longer have a crackling sound when Ubuntu shuts down.

---

### Post by dsonck on 2011-12-07
Unfortunately I don't use Ubuntu anymore due to a failed installation/upgrade but I do have the same crackling sound on shutdown. I use openSUSE and the last thing I changed is to use pulseaudio instead of ALSA. I have an Intel HDA card with an IDT 92HD75B3X5 chip.

As GilbertEvanG said he might have solved it using "ALSA - Advanced Linux Sound Architecture" instead of "Autodetect", I think this is a pulseaudio bug. I think that autodetect chooses pulseaudio (especially in the newer versions of ubuntu) over alsa.

I do recall that my desktop had the same problem for a while, which has an HDA Nvidia card with a Realtek ALC662 rev1 chip. It was more like a click, and it happened on boot-time too.

Unfortunately pulseaudio is necessary when you want more than one program to use your soundcard. Even simple notification sounds use a new channel, which only pulseaudio supports.

Daniël Sonck

---

