---
title: "Problem configuring alsa-utils"
date: 2006-07-05
forum: Multimedia &amp; Video
---

### Post by d3dtn01 on 2006-07-05
I'm trying to compile the latest ALSA release. The alsa-utils is giving me a problem. When I try to configure it, I get the following output:

```
checking for initscr in -lncurses... no 
checking for initscr in -lcurses... no 
configure: error: this packages requires a curses library

```

I'm not real familiar with curses libraries, but here are the ones that Synaptic says are currently installed:

lib64ncurses5
libncurses5
libncursesw5
ncurses-base
ncurses-bin
ncurses-term

Is there some other one that I need? Or is there some way to specify which ncurses library to use?

---

### Post by LordRaiden on 2006-07-05
[quote=d3dtn01]I'm trying to compile the latest ALSA release. The alsa-utils is giving me a problem. When I try to configure it, I get the following output:

```
checking for initscr in -lncurses... no 
checking for initscr in -lcurses... no 
configure: error: this packages requires a curses library

``` 
I'm not real familiar with curses libraries, but here are the ones that Synaptic says are currently installed:

lib64ncurses5
libncurses5
libncursesw5
ncurses-base
ncurses-bin
ncurses-term

Is there some other one that I need? Or is there some way to specify which ncurses library to use?[/quote]

you probably need the -dev package for ncurses, something like ncurses-dev and libncurse5-dev

---

### Post by killerjay_47 on 2006-07-05
Agreed. I installed libncurses5-dev when I did my build, and that fixed the problem when I was building.

Jay

---

### Post by d3dtn01 on 2006-07-05
[QUOTE=killerjay_47]Agreed. I installed libncurses5-dev when I did my build, and that fixed the problem when I was building.

Jay[/QUOTE]


Thanks to you both. That worked.

---

### Post by virtualcoder on 2008-01-29
Thank you!

---

### Post by mosquito princess on 2008-04-14
Hi,I've been having the same problem while compiling the alsa-utils.
The thing is that when I gave **"sudo apt-get install libncursesw5-dev**" and "**sudo apt-get install libncurses5-dev"**,it gave :

[I]Package libncurses5-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libncurses5-dev has no installation candidate[/I]

libncurses5 & libncursesw5 are installed.
Any help on that??
Thnx in advance!

---

