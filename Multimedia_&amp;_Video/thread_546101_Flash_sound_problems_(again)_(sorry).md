---
title: "Flash sound problems (again) (sorry)"
date: 2007-09-08
forum: Multimedia &amp; Video
---

### Post by Weird Al on 2007-09-08
OK I've searched the forum and Google about this and the following didn't work:

Using Flash 9 from Adobe instead of the repos
Using Flash 9 from the repos instead of Adobe
Using aoss and editing /etc/firefox/firefoxrc
Creating the libesd symlink (Since I'm not using ESD because it interferes with ALSA)

And the symptoms are not the same. I *do* have sound in Flash, but it's pathetic, and it's not actually the right sound. What it is is a very faint repeated sound, three short bursts of nothing in particular. It sounds like it could be whatever's meant to be coming through, but in short packets, three at a time, and then a pause. If I pause the video it doesn't stop trying to play the sound - I guess it's trying to keep up - but if I close the tab, it stops eventually, and if I close the whole browser then it stops immediately.

Sound works in everything else using either alsa or alsa-oss. I set my asound.conf exactly as on this page [http://www.thepenguin.org.uk/alsa/](http://www.thepenguin.org.uk/alsa/) and software mixing works perfectly. Could it be this that's doing it?

Any ideas?

TIA
al

---

