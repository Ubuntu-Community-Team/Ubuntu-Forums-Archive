---
title: "Flash Player  9 124 version on openSuse 11....."
date: 2008-10-25
forum: Multimedia Software
---

### Post by sirzeta on 2008-10-25
Flash Player  9 124 version on openSuse 11 x64 with nvidia driver works like a charm, seems using hardware accelerated function on fullscreen(tested with youtube videos), and the same version of flash on Ubuntu 8.04 x64 is really pain slow(unresponsive also when you want change volume, minute of track, or just close fullscreen)... so weird. (doesn't matter if compiz is activated, openSuse just do the work nicely)

For example, if you go fullscreen, the text of youtube videos "Press Esc to exit full screen mode" in Ubuntu 8.04 x64 it's pixelated, and the openSuse 11 x64 have a nice bilinear filtered texts. Same xorg.conf, same fonts.config, same gconf settings.... weird weird weird...

I don't understand this issue, i copied

libflashsupport-000-67.1.i586.rpm
nspluginwrapper-0.9.91.5.99.20071225-22.1.x86_64.rpm
flash-player-9.0.124.0-10.1.i586.rpm

from openSuse 11 x64 DVD if there are optimized config o something different, but i can't extract them, are signed rpm, i imported pgp asc from the DVD, but still can't extract(already installed rpm related tools from repositories).

Well, if there someone with more skills want track want damn happens, give a shot.

If anyone already posted something in launchpad on this issue, feel free to report this info(I never posted there, and I don't have time to do it now).

Well, i hope this resolve soon. Bye bye, take care guys.

PD: Sorry my english. :lolflag:

EDIT: I know there are 10 version of flash, but why Ubuntu can't and openSuse can?

EDIT2: I tested "vesa" driver on xorg.conf, and fullscreen flash videos runs well, obviosly without bilinear effect, but's it's responsive, not like with nvidia driver enabled.

---

### Post by gandaran on 2008-10-25
> I know there are 10 version of flash, but why Ubuntu can't and openSuse can?



well, I don't know the answer, but I can tell I tried opensuse 11, I used to be a opensuse 10 user before coming to ubuntu and I didn't see any deference with flash 9.124, in fact I have never had any issue with flash 9 on ubuntu 8.04, never needed to install libflashsupport, ubuntu 8.04 just worked perfectly out of the box for me, maybe it is because my sound capture is set to alsa not pulseaudio, pulseaudio is a headache for many users.

> I don't understand this issue, i copied



libflashsupport-000-67.1.i586.rpm

nspluginwrapper-0.9.91.5.99.20071225-22.1.x86_64.rpm

flash-player-9.0.124.0-10.1.i586.rpm

the flash in the rpm package is the same one you use in ubuntu, it's made by adobe no deference



by the way I had to give up on opensuse 11, there was just one problem for me, yast window size, couldn't re-size, couldn't install any application only use the command line.

---

