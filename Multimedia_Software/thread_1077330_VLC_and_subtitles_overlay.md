---
title: "VLC and subtitles overlay"
date: 2009-02-22
forum: Multimedia Software
---

### Post by juanbretti on 2009-02-22
Hello,

I'm using VLC and Ubuntu 8.10.

I've this issue:
I have a movie (DivX) and a subtitle (SRT) and I want to see the sub in an overlay from the movie.

I mean, when I play de movie and load (by drag and drop) the subtitle, the subtitle shows like it is embed in the movie.

What I want, is to have the subtitle in a separated layer so it can be sharp and crysp. And also I will be able to move the subs outside the movie area (I have a 4:3 monitor, so I have plenty of black space where the subs could go).

I hope someone has understood my issue... and that is not a repost :)

Thanks!
pepemosca

PS: I think the solution goes by changing the "Video output module". How? Help?
Thanks!

---

### Post by juanbretti on 2009-02-24
Nada, no ideas?

Help?

I leave attached a picture of the subs position.
I want the subs to be in the bottom black area.

Thanks!

---

### Post by juanbretti on 2009-02-24
OK, here is some sort of solution using SMPlayer

[http://positionrelative.blogspot.com/2008/03/set-subtitle-position-outside-movie.html](http://positionrelative.blogspot.com/2008/03/set-subtitle-position-outside-movie.html)

```
With smplayer this can be added in Preferences/Advanced/Options for MPlayer/Video filters:
scale=800:-3:::0.00:0.75,expand=:640

This rescales the image to 800px wide (height is then expanded to 640px); this is the common LCD aspect ratio; with bigger numbers (>1024px) the playback was choppy for me. 
```

Check the attached pics.
Still, not the best solution.

Any other ideas?
Thanks!

As far as I can see on VLC forum: is not possible:
[http://forum.videolan.org/viewtopic.php?t=3041](http://forum.videolan.org/viewtopic.php?t=3041) :(

---

### Post by rvm4000 on 2009-02-24
In smplayer it's easier, no need to enter filters manually. The option *Video -> Filters -> Add black borders* does everything.

There's also an option in preferences to add the black borders automatically when switching to fullscreen.

---

### Post by juanbretti on 2009-02-25
> **rvm4000 said:**
> In smplayer it's easier, no need to enter filters manually. The option *Video -> Filters -> Add black borders* does everything.

There's also an option in preferences to add the black borders automatically when switching to fullscreen.

Ohhh! Coooool!
I'll look for these settings!
Thanks!


:guitar:

---

### Post by juanbretti on 2009-02-25
> **rvm4000 said:**
> In smplayer it's easier, no need to enter filters manually. The option *Video -> Filters -> Add black borders* does everything.

There's also an option in preferences to add the black borders automatically when switching to fullscreen.

Question: Which **video mode** do you recomend? (I mean in SMPlayer) X11, gl, gl2...? Any tutorial? Links?

Thanks!

---

### Post by rvm4000 on 2009-02-25
*xv* should be the faster. If you have any trouble with it try *gl*, with recent versions of mplayer it's very fast (I can even play HD videos with it).

*x11* is the slowest, but sometimes it's the only one that works ok when desktop effects are enabled.

---

### Post by juanbretti on 2009-02-25
Cool, cool, cool!

So many SMPlayer information on one post!
Thanks!

---

### Post by DiegoBretti on 2009-03-02
> **rvm4000 said:**
> In smplayer it's easier, no need to enter filters manually. The option *Video -> Filters -> Add black borders* does everything.

There's also an option in preferences to add the black borders automatically when switching to fullscreen.

NICE!
Thanks a lot!

---

