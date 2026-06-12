---
title: "Dell D630, Intel soundcard, Pulseaudio and KDE3"
date: 2009-01-14
forum: Multimedia Software
---

### Post by slakkie on 2009-01-14
Hello all, 

I had a problem with my sound (no sound) on my laptop (Dell LATITUDE D630), and I managed to fix it.

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

The solution to the problem is:
[http://wiki.archlinux.org/index.php/PulseAudio#Drop-in_replacement_for_ESD_.28EsounD.29](http://wiki.archlinux.org/index.php/PulseAudio#Drop-in_replacement_for_ESD_.28EsounD.29)


as root run: ln -sf /usr/bin/esdcompat /usr/bin/esd

Goto your system settings > sound system > hardware > enlightenment sound system (ESD). And save. This will make sure sound is enabled.

Since it took me a while before I fixed this. Gnome users do not have a problem since it comes default with Pulseaudio (at least all of my co-workers run Gnome with this laptop and they didn't have any problems with sound. 

Hope this helps all of you who have this problem!!

---

