---
title: "Big problem, creating DVD with Bombono-DVD 1.2.1"
date: 2013-04-08
forum: Multimedia Software
---

### Post by picrard on 2013-04-08
Hi,
I hope that someone could help me with this problem under **Ubuntu 12.04.** with **Bombono-DVD 1.2.1**,
the fact is, that every time I want to create a DVD with a menu,
it shows me an error like this(hm, its german, I hope it shows you the problem):
[IMG]http://media.cdn.ubuntu-de.org/forum/attachments/56/14/5498397-Bild.jpg[/IMG]
I have done some things to solve the problem but without any success,
first of all I had a problem with the **dvdauthor**, so I have tried to compile another version,
I also had problems with **avconv**, so I have compiled this one too, 
first I only had an error, when Bombono has finished the work on rendering and when it started to build the
dvd structure, so it was a problem with **dvdauthor**, now I have the error at the beginning of the rendering process.
It shows me that I have installed a stripped version of **ffmpeg** and it doesn't support **mpeg2video**.
So does anyone have this problem creating DVD's with Bombono???

I also use Bombono under a Debian 6.0 derivate, it it's just **Bombono 1.0 **but it works fine, i think that the **dvdauthor** and **avconv**
(I think that with this lnux it's still ffmpeg) are other versions.
So here some info about my installed packages I hope it would help you,
maybe you could solve my problem, thank you!

- DVDAuthor::dvdauthor, version 0.6.18.
- avconv version 9.4, Copyright (c) 2000-2013 the Libav developers
- ffmpeg version 0.8.6-4:0.8.6-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers   built on Apr  2 2013 17:00:59 with gcc 4.6.3

---

### Post by picrard on 2013-04-09
so, no feedback?! ...

I've made some other things to solve my problem,
but that did not work.
First of all I've removed the self compiled versions of **DVDAuthor** and **avconv**.
now I have installed all Ubuntu 12.04. included packages which have the version numbers.:

[B]avconv version 0.8.6-4:0.8.6-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers   built on Apr  2 2013 17:00:59 with gcc 4.6.3
[/B]and[B]
DVDAuthor 0.7.0-1.1build1[/B]

but that did not work. Now I had the problem at the end of the rendering process,
when Bombono-DVD wants to complete the DVD.

[IMG]http://250kb.de/u/130409/p/lXYM0Vsv3Opk.png[/IMG]

I've used instead of** Bombono-DVD** the **DVDStyler**, it works with** dvdauthor **and **avconv**, no problems,
I've rendered a project with menu and clips included,
but I prefer the workfow of **Bombono** more than **DVDVStyler**, so does someone have an idea?

any suggestions???

please :(

---

### Post by picrard on 2013-04-09
O.K. I solved it by my own way !!!

more :

[http://forum.bombono.org/viewtopic.php?f=1&t=21249&p=46447#p46447](http://forum.bombono.org/viewtopic.php?f=1&t=21249&p=46447#p46447)

---

