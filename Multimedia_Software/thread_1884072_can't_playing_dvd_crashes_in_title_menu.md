---
title: "can't playing dvd crashes in title menu"
date: 2011-11-20
forum: Multimedia Software
---

### Post by Chiel92 on 2011-11-20
Hi all,

I think the thread title explains the problem.
I just want to play a (music and video) dvd, which fails because any mediaplayer will hang when I choose any entry in the title menu.

I tried vlc and movieplayer.
Movieplayer gives the error: could not read from resource.
Vlc just doesnt do anything at all.

regards

EDIT: HM, from what I read on the internet and the errors I get when running vlc in terminal, I guess the DVD is encrypted. I will need some css libs or something.

---

### Post by Chiel92 on 2011-11-20
I came upon a up-to-date solution. (I already found a similar one, but the packages mentioned were out of date.)

First
```
sudo apt-get install libdvdread4
```
and then
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Maybe reboot is necessary.

---

