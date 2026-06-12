---
title: "Compiling libdvdread"
date: 2011-05-26
forum: Multimedia Software
---

### Post by bjem85 on 2011-05-26
Hi All,

I'm trying to troubleshoot a block seek error with a *particular* DVD (most DVDs work with my computer, just a random few that fail).  The failure is (I presume) caused by incorrect information on the DVD itself to try to fool unlicensed players.

I get a libdvdread error "Can't seek to block ...".  I have traced this error message to three sources in dvd_reader.c .  I have modified the error message so that it also prints the file name and the line, but I am having such a hell of a time trying to compile libdvdread that I am posting this question on the forum here.

I have installed libdvdcss2-dev, and most of the other obvious development packages.  However, the instructions for compiling lindvdread make no sense (I am assuming they want me to run the 'configure2' script here) and it is throwing up all kind of weird compiler errors.

This can obviously be compiled somewhere for a binary package to exist.  Does anybody know how this is done?

Kind Regards
Bart

---

### Post by bjem85 on 2011-05-26
P.S. the exact DVD is 'The Games' Series 1 Disc 2, Distributed by Umbrella Entertainment Australia, All Region, UPC 9-322225-034013

---

