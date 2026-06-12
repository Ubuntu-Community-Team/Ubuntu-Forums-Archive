---
title: "Defoult Programms in Ubuntu"
date: 2013-06-09
forum: Multimedia Software
---

### Post by maxbit on 2013-06-09
Hy i wondered why in non of the Distros is ever VLC used as default media player and also never Iron is used as default Browser.

On VLC i think it would be cool to integrate it in the Sound option like the Gnome Player is in Ubuntu.

Hope my input helped =)

---

### Post by oldos2er on 2013-06-09
You need to post to the appropriate developer's mailing list if you want them to see your suggestion; this forum is for technical support.

---

### Post by Yellow Pasque on 2013-06-09
While the Ubuntu install .iso passed the CD limit a while ago, Canonical still tries to keep it as small as possible. Using VLC would require more libraries (libav stuff). Since Totem is a gstreamer app, and Ubuntu already uses gstreamer-based Rhythmbox for its media player, Totem doesn't take as much space (same thing with Xubuntu and parole player).
I'm not sure about Kubuntu, but I think they generally prefer native KDE/Phonon player (Dragon).

Iron browser: sounds interesting, and you should suggest it to the lubuntu devs, since they already use chromium.

---

### Post by Cheesehead on 2013-06-10
This has been discussed several times before. The reasons are mostly historical.

Totem is the default Gnome player. In the past before Unity, Ubuntu tried to stay close to the Gnome defaults. Ubuntu has moved away from that, but does not change defaults lightly. Millions of users are affected by each change.

Also in the past, VLC's license did not permit Ubuntu to distribute it (or several of its codecs). That has been resolved.

VLC came late to dbus, and until recently did not integrate very will into the Gnome or Unity desktops. That has been resolved.

Finally, last time I looked, VLC plus only-used-by-VLC-dependencies was a bit larger than the corresponding Totem footprint.

Both players have their quirks and bugs. Neither is perfect. And both projects have had their active-development periods and their doldrums.

Integration into the sound menu is done by volunteer contributors within the Ubuntu community, not by paid Canonical Staff (they work on the releases and the Kernel), nor by VLC (who mostly work on Windows). Integrating into the sound menu is not difficult, and there are several good tutorials. Give it a try, and package the code.

---

