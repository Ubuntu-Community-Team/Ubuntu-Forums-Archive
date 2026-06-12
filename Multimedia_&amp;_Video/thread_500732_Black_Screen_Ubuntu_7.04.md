---
title: "Black Screen Ubuntu 7.04"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by LyokoHaCK on 2007-07-14
I bought a new monitor (Samsung 19" widescreen). When I start ubuntu (grub), I select the right one, then the loading screen goes by fine. Then, instead of showing the login screen I see a black screen but still hear the sounds of my login screen. I can even type <username> [enter] <password> [enter] and I will hear the welcome theme at the beginning.

nVidia 7600GT.

I previously used a 15" CRT.

---

### Post by Damanther on 2007-07-17
Log into recovery mode and check your /etc/X11/xorg.conf file.

Make a backup copy of it first. Then, make sure all the entries there are correct for you new monitor.

Restart and see how it goes.

Damanther

---

