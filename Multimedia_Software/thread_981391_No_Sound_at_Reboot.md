---
title: "No Sound at Reboot"
date: 2008-11-13
forum: Multimedia Software
---

### Post by edvar on 2008-11-13
I have been using Ubuntu since version 7.04 (Feisty) and then upgraded to 7.10 and another upgrade to 8.04 and 8.10. The machine was starting to get slow because of all the garbage from the previous upgrades. For that reason I decided to do a fresh install of Kubuntu 8.10 (Intrepid Ibex) on my Media Center computer basically because I really like what they did with KDE 4.1. Looks so much better than Gnome!

Since it's a Media Center box hooked up on my TV and my receiver, I need the best sound and the best video I can get from the OS. I had some sound issues with my Hardy installation before so I thought a fresh install of Intrepid would solve all my problems. B*llsh*t! It was even worst! Honestly I thought the developers would get their stuff right this time after all the issues on Hardy but I was really disappointed. Anyway...

After the installation I had no sound at all. I searched the forums for hours and tried several things: I installed the latest ALSA driver 1.0.18, uninstalled PulseAudio and tried everything on [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto). I finally got it working however every time I reboot my box I lose all sound. Basically the PCM and Master channels startup muted. Just putting them to full volume on alsamixer doesn't do the job. To get it fixed I have to:

sudo alsa force-reload

and then go back to alsamixergui and unmute both channels. After that I have my sound back however if I reboot my machine I have to do it all over again. It's really annoying!

I tried 'alsactl store' and 'alsactl restore' but it doesn't do anything.

Any ideas on how to solve this? It would be really appreciated!

---

### Post by edvar on 2008-12-08
Bump!

---

