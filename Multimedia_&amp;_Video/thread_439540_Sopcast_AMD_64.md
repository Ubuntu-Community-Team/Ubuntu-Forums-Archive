---
title: "Sopcast AMD 64"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by LordOfTheBoards on 2007-05-10
Hi everyone! 
I'm trying to get Sopcast to run on my new install, the feisty. But there's a problem: 
I have the 64 bit version and the two packages I downloaded, gtk-sopcast and sopcast, won't install, because of architecture problems. I also tried the command line version, which would be enough for me, but when I run sp-sc or ./sp-sc it says file not found. Eventhogh i can see the file, it's in the folder and also in /usr/local/bin.
NBA starts in an hour and I just don't know what to do! pls help

LOTB

---

### Post by realzippy on 2007-11-29
...1 hour? A bit late now,but a simple:

sudo dpkg -i --force-architecture gtk-sopcast_0.2.8-1_i386.deb

would have done it,if you use the gtk-sopcast_0.2.8-1_i386.deb.

---

### Post by sxjast on 2008-02-09
Anyone able to get Sopcast working on AMD 64?

---

### Post by nuaimat on 2008-02-28
guys, please offer help

the dpkg -i trick installs sopcast fine, but how to run the gui ??

please help ?

---

### Post by parumi on 2008-03-15
> 
guys, please offer help
the dpkg -i trick installs sopcast fine, but how to run the gui ??


just run *gsopcast*
also, from the menu *Applications, Sound and Video, Sopcast TV Playe*r
tested in  ubuntu gutsy amd64. my hardware is a macbook core2duo

in general, to know the executable (binary) of an installed package you can list the installed files: 
```
$ dpkg -L gtk-sopcast
```

---

