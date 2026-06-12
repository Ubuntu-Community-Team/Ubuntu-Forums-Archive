---
title: "Dual monitors ati x1650pro gutsy"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by at4z on 2007-10-22
Ok I am a total linux noob and have been struggling to get dual monitors working for about a week. I finally got it working and thought I would give you the steps i took. Some of the steps might be useless, but it's exactly what I did.

All of this is working off a fresh gutsy install.

First, follow this guide [http://ubuntuforums.org/showthread.php?t=575843]("http://ubuntuforums.org/showthread.php?t=575843") and install the driver from the ati website. If you find that a step wont work. Restart and try that step again. The only step that didn't work for me was the very last one, glxinfo | grep direct.

Now press ctrl+alt+backspace

Now open up the terminal and enter:
```
 sudo aticonfig --initial=dual-head --screen-layout=right --vrefresh=1,60
```

you can substitute left/vertical for right depending on your setup.

press ctrl+alt+backspace and you should have dual monitors!

if they are the wrong orientation you might have to go into xorg.conf to change them
```
sudo gedit /etc/X11/xorg.conf

```

Now we need to make it so you can drag the windows back and forth by editing xorg.conf again.
```
sudo gedit /etc/X11/xorg.conf

```

Look for Section "Server Layout" and add this to the end:
```
Option "Xinerama" "On"
```

press ctrl+alt+backspace

Hopefully it works for you.

---

