---
title: "little problem with video files"
date: 2009-02-13
forum: Multimedia Software
---

### Post by GaVrA on 2009-02-13
The problem i am having is that when i open some video file it starts in all black, but when i jump it little forward i get the picture. Then i have to stop it in order to get picture from begining. :confused: 

I am using VLC player, and i have installed all these things they say i should:

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

Maybe its some bug in vlc, dunno... Anyone know how to fix this?

---

### Post by GaVrA on 2009-02-13
fixed... switched to gnome mplayer...

---

### Post by UbuntuNerd on 2009-02-13
in a terminall type this:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get install libdvdcss2 w32codecs
```
also in a terminal:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by GaVrA on 2009-02-13
Everything is fine now... ;) I have followed instruction on this topic:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

And installed gnome mplayer... :)

---

