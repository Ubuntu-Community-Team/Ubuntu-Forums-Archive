---
title: "CLI limitations-play Movies with Mplayer?"
date: 2009-08-20
forum: Multimedia Software
---

### Post by pw_f100_220 on 2009-08-20
Hi, I almost always use mplayer from the command line, and since I now have two computers, I hope to use the slow one with maybe debian without a gui (MAYBE).  I'm wondering what the limitations are without ever loading X, specifically if it's possible to play a movie/music from the command line interface.

Basically I want this computer to play music and movies and run lynx (or another recommended web browser).  This desktop is almost ten years old, and if all three of these are possible without X, it should be blazing fast.

Thanks!

---

### Post by xzero1 on 2009-08-20
I might suggest trying _Puppy Linux_. There is an option to use X or not when booting. So yes, these things are possible without X. Puppy is extremely responsive due to its light weight window manager and since the entire os loads and runs from ram.

[http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm)

---

### Post by pw_f100_220 on 2009-08-20
i know there are ways to have the option to boot to cli then start X if you decide, but I want to know if it's possible to play a movie with mplayer _without ever starting X._  

I appreciate the suggestion and quick response though.

---

### Post by xzero1 on 2009-08-21
To clarify, 'X' is not the same as 'gui'. For graphics there must be some graphical server. Puppy does not require the same X as Ubuntu but can use Xvesa, a stripped down graphical server. Since it runs off a live cd (no install necessary), just try it.

Technically, one can run mplayer in a text console using ascii only video output using '-vo caca' or '-vo aa' but this is probably not what you want.

---

### Post by pw_f100_220 on 2009-08-21
I know X isn't the same as gui, but the only thing i'll need the graphics just for a video every once in a while.  no gui necessary.  I like the sound of the stripped down graphical server, but if I could just choose to run it in the background when i run a movie file, that would be awesome.  I have tried Puppy, and i've enjoyed smaller distros (DSL, SliTaz) and lighter weight DE's as well (ratpoison), but I just want CLI with movies.  I don't want to start a DE just for a movie.

SO!!  New goal:  run X server (stripped down as possible) in background behind a CLI to enable mplayer video playback WITHOUT STARTING A DESKTOP ENVIRONMENT.  not even ratpoison.

I like the sound of Xvesa as a stripped down graphical server, I'm also going for boot-up time, so i'm going low on services and shtuff.

Thanks for the ideas...

---

