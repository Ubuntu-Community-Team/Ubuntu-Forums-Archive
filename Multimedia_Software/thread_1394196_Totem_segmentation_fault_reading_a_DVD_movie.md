---
title: "Totem segmentation fault reading a DVD movie"
date: 2010-01-30
forum: Multimedia Software
---

### Post by DMurray on 2010-01-30
Hi everybody.
I upgraded my system from 8.04 all the way to 9.10.
Right now I'm trying to play a DVD (Pink Floyd Pulse) and Totem Player just crashes on me. I followed the medibuntu rep installation process found here:

```
http://shibuvarkala.blogspot.com/2009/10/how-to-make-ubnutu-910-karmic-koala.html
```

The reps were updated, packages downloaded and installed, but Totem still crashes. I took a look at /var/log/messages and when I ask Totem to read the DVD, it outputs this line:

```
Jan 30 12:46:17 localhost kernel: [ 5576.977430] totem[3556]: segfault at 1880 ip 00007f6cfa8fb081 sp 00007f6ce48b1ac0 error 4 in libpthread-2.10.1.so[7f6cfa8f2000+17000]
```

I don't understand why libpthread would cause any problem here. Do you guys have any suggestion?

Thanks in advance.

---

### Post by DMurray on 2010-01-30
I just tried the suggestion at:

```
http://ubuntuforums.org/showthread.php?t=1358691
```

Without success. I have all packages installed, Gnome MPlayer doesn't output anything too.

---

### Post by mc4man on 2010-01-30
Maybe try a different video output

In gnome-mplayer -> edit -> preferences -> and in the video dropdown under player tab try x11. If no go try gl2.

If you have vlc run from terminal to produce some errors (comm. assumes dvd in drive and /dev/sr0

```
vlc dvd://
```
or a temp output change 
```
vlc --vout x11 dvd://
```

---

### Post by DMurray on 2010-01-31
Hello, Mc4man.
I tried changing the video output in the gnome-mplayer preferences, but it didn't work. Since I was out of town, I couldn't test vlc, but let me ask you: doesn't it use the same libs as mplayer, so it would suffer with libpthread as well (assuming that libpthread is the problem)?
In fact, the current version of mplayer seems to be worse than previous, because now the screen will flash in white color some times in any video file.

---

### Post by DMurray on 2010-02-09
I ran dpkg-reconfigure on the following packages:
libdvdcss2, libpthread, totem
DVD playing is normal now. I thought the upgrade process already ran a dpkg-reconfigure -a, but apparently it doesn't.
It is solved.

---

