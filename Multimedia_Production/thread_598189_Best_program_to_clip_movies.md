---
title: "Best program to clip movies?"
date: 2007-10-31
forum: Multimedia Production
---

### Post by Igniteflow on 2007-10-31
I want to clip some of my favourite scenes from movies (mainly .avi files) and compile them into one video.  Do you have any recommendations?  I'm not finding much from searching the forums

---

### Post by elliotjreed on 2007-10-31
Try using Cinelerra - it's an open source video editor.

It's pretty simpleish, a bit like a better version of Windows Movie Maker - it can cut, trip, crop all that jazz!

Here is a thing on how to install it:

[http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu]("http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu")

If you want to compile from source:

[http://heroinewarrior.com/download.php3]("http://heroinewarrior.com/download.php3")

After installing, and before running, do the following in the terminal:

```
sudo echo "0x7fffffff" > /proc/sys/kernel/shmmax
```

This makes it happy, but won't affect anything else!

---

### Post by orange2k on 2007-10-31
I use Avidemux: you can easily crop parts of movies, save them as separate files, and merge them together...

---

### Post by netyire on 2007-11-01
Avidemux is quite straight forward, works okay for simple editing. Try kdenlive if you need to insert text or if you want more editing power. Its quite similiar to moviemaker in windows and can export directly to dvd.

---

