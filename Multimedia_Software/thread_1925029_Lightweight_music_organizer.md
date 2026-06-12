---
title: "Lightweight music organizer"
date: 2012-02-13
forum: Multimedia Software
---

### Post by didiandrade on 2012-02-13
Hi, just started using Lubuntu and I'm looking for a lightweight music organizer. Any sugestions?

---

### Post by wolfen69 on 2012-02-13
There's [Pragha]("http://linux.softpedia.com/get/Multimedia/Audio/Pragha-48558.shtml") music manager.

---

### Post by Rodney9 on 2012-02-14
Pragha is in Synaptic



For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by didiandrade on 2012-02-14
Hi, I didn't find Pragha in Synaptics.. so I tried to compile from the source downloaded from the reply above.
When I try to do ./configure I get the following error:

checking for alsa >= 1.0.15... not found
*** The required package alsa was not found on your system.
*** Please install alsa (at least version 1.0.15) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.

I tried to install alsa using apt-get but it said that alsa-base (version 1.0.24) is alrealdy installed.

---

### Post by Rodney9 on 2012-02-14
Have you installed Lubuntu Restricted Extras - 

[http://ubuntuforums.org/showthread.php?t=1880394](http://ubuntuforums.org/showthread.php?t=1880394)

Rodney

---

### Post by didiandrade on 2012-02-15
I did it now and solved the problem, but I have a new one:

checking for flac >= 1.2.1... not found
*** The required package flac was not found on your system.
*** Please install flac (atleast version 1.2.1) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.

I have already installed flac-1.2.1 but it still doesn't work.

---

