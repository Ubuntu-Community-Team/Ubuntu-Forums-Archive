---
title: "Xorg, mplayer and other"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by illusionist on 2008-01-27
Hi all!
I have 3 questions.

1. I need to run mplayer in full-screen under X without desktop (KDE, gnome) and without any login manager (kdm, gdm...).
I tried command:
$ xinit -e mplayer -vo x11 -zoom -loop 0 -fs file.avi
And it works, but I don't want to see this background and xterm before starting Xserver.
How to run program in xorg without xterm? (as runs kdm, gdm...)

2. I need to attach a banner at right part of screen, and a marquee
string at bottom. In back place will run mplayer.
How I can do that?

3. How to disable mouse? I disabled mouse in xorg.conf, but mouse appears and works. 
If I delete the xserver-xorg-input-mice package, xorg will not start, because 'mouse' driver not found

All this is needed for the computer, thats will be located somewhere in supermarket and will show advertising

Sorry for my English!

---

