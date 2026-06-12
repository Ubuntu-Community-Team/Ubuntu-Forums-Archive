---
title: "Asrock ION no (multichannel) SPDIF sound in XBMC (Ubuntu 9.04 Jaunty)"
date: 2009-09-22
forum: Multimedia Software
---

### Post by OobieDoob on 2009-09-22
Hardware: Asrock ION 330 (DVD)
BIOS: 1.60
OS: Ubuntu Jaunty (9.04)
Display drivers: 185.18.36
Alsa drivers: 1.0.21

First things first, I want multichannel audio (AC3/DTS) over SPDIF in XBMC (via HDMI isn’t necessary). Before I started with my days of struggle through xbmc and linux threads (yes I’m a linux noob), I had sound over SPDIF in XBMC but as so many unfortunately only 2-channel ([http://ubuntuforums.org/showthread.php?t=1212523](http://ubuntuforums.org/showthread.php?t=1212523)). Now after my hellish search I lost my SPDIF sound, but only in video files which are played by XBMC.

This was after my last try to disable pulseaudio by this post: [http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)
All my tries with /etc/asound.conf and ~/.asoundrc didn’t work so I removed the files but unfortunately no luck. If I’m getting sound back in video files I still think it’s only in 2-channel stereo. Before disabling PulseAudio I had the strange thing that my amp thought it received a 2-channel stream but it’s was in fact a 5.1 channel stream but only played over my L and R speaker. I can tell you, it sounds very strange ;-)

Does someone have an idea because I’m clueless at this point. Help much appreciated!

---

### Post by OobieDoob on 2009-09-23
**UPDATE:** closing thread after a 3rd clean Ubuntu Jaunty install and replies (or lack off replies) to just clean install Ubuntu Jaunty again (on other forums).

For the people with the same crappy problem, I tested in Windows 7 today and everything works like a charm without even installing extra display and/or sound drivers: full HD display and DD5.1+DTS sound over SPDIF and/or HDMI.

Why is this such a problem within the latest Ubuntu version. Unbelievable!

---

### Post by zorniki on 2009-10-29
Hi OobieDoob!

I´ve had the same problems with my ION330 since 9.04 released. No help in sight it seems. I´ve pretty much abandoned my Ubuntu partition since then... :(

---

