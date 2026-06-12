---
title: "Mplayer Compiling Help Please."
date: 2006-08-04
forum: Multimedia &amp; Video
---

### Post by GoLoGo on 2006-08-04
I installed all the needed packages. I copied the latest essentials codec package to my /usr/lib/win32 directory. Downloaded the latest Mplayer from the official website. Used the code:
```
./configure --prefix=/usr --enable-gui --disable-arts --disable-smb --enable-sdl --enable-x11 --enable-theora --confdir=/etc/mplayer --with-win32libdir=/usr/lib/win32 --enable-menu --enable-tv-v4l --enable-tv-v4l2 --disable-liblzo --enable-largefiles  --disable-libdv --disable-aa --enable-xvid --disable-divx4linux --enable-x264

```

Everything seemed fine. Now the next step is to compile... when I use the command **make** it tells me "bash: make: command not found" - What could be causing this? I am new to Ubuntu, thanks.

---

### Post by Jagot on 2006-08-04
Have you installed the build-essential package?  Is there any reason you're not installing mplayer from the repos?

---

### Post by GoLoGo on 2006-08-04
Alright thank you, decided to just use sudo apt-get install mplayer - installed flawlessly, I guess I was just making something simple, more complicated for myself thanks :).

---

### Post by Jagot on 2006-08-04
Yep - always a good idea to check if a package you need is available in the repo's before searching elswhere!

---

