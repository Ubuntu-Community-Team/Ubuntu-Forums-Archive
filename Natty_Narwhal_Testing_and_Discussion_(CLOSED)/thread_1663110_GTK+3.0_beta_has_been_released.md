---
title: "GTK+3.0 beta has been released"
date: 2011-01-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-01-09
Now that GTK+3.0 beta has been released, Gnome3 is one step closer.
More on this here:
[http://www.phoronix.com/scan.php?page=news_item&px=ODk4NQ](http://www.phoronix.com/scan.php?page=news_item&px=ODk4NQ)

---

### Post by amano on 2011-01-09
But not for Ubuntu. With the new GTK+ theming engine introduced that late in the development cycle a new Ambience and Radiance theme would have to be written from scratch and tested. And this new theme will not be able to mimic the current theme completely. Thus GTK+ 2 and GTK+ 3 programs will look different which puts the whole GNOME 3 transistion at risk. It might well be that we will see the full GNOME 3 only for Ubuntu 11.10 (and just parts of it in Ubuntu 11.04.

---

### Post by ronacc on 2011-01-09
If Ubuntu wont integrate it for us we will just have to do it ourselves like we are GS .

---

### Post by godhika on 2011-01-09
> **amano said:**
> But not for Ubuntu. With the new GTK+ theming engine introduced that late in the development cycle a new Ambience and Radiance theme would have to be written from scratch and tested. And this new theme will not be able to mimic the current theme completely. Thus GTK+ 2 and GTK+ 3 programs will look different which puts the whole GNOME 3 transistion at risk. It might well be that we will see the full GNOME 3 only for Ubuntu 11.10 (and just parts of it in Ubuntu 11.04.

It already exists! [http://www.cimitan.com/blog/2010/10/14/murrine-and-ubuntus-light-themes-ported-to-gtk-30-with-a-ppa/]("http://www.cimitan.com/blog/2010/10/14/murrine-and-ubuntus-light-themes-ported-to-gtk-30-with-a-ppa/")

---

### Post by zekopeko on 2011-01-09
> **amano said:**
> It might well be that we will see the full GNOME 3 only for Ubuntu 11.10 (and just parts of it in Ubuntu 11.04.

I think that's the general plan. For the same reason Gnome-Shell isn't going to be in Natty repos.

---

### Post by amano on 2011-01-09
> **godhika said:**
> It already exists! [http://www.cimitan.com/blog/2010/10/14/murrine-and-ubuntus-light-themes-ported-to-gtk-30-with-a-ppa/]("http://www.cimitan.com/blog/2010/10/14/murrine-and-ubuntus-light-themes-ported-to-gtk-30-with-a-ppa/")

Sadly, not. This was just a port of Murrine to work with GNOME 3 in October. But in late December big changes to the GTK+ 3 rendering were done and Andrea Cimitan cannot port Murrine to that code. Thus a completely new theme has to be written to mimic Ambiance and Radiance for the new GTK+ 3 engine (which is very powerful and makes the former split between Clearlooks, Aurora and Murrine obsolete).

Sadly Andrea stated that he can create a new theme that looks similar to Murrine/Light, but that differences can be noticed. Which makes the mixed GTK+2/GTK+3 environment very ugly (which the Ubuntu developers had envisioned).

---

