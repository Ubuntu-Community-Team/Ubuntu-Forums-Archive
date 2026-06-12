---
title: "Intermittent Flash Issue in Jaunty"
date: 2009-05-01
forum: Multimedia Software
---

### Post by gotsanity on 2009-05-01
I am currently running into an issue with my flash install in jaunty. I am running the flashplugin-nonfree from the repos and have an issue where sometimes flash (like youtube) will show up but other times will just show as a blank white box. The only way to fix the blank box is to close firefox and reopen (and that doesnt always wok). Acording to synaptic i have version 10.0.22.87ubuntu2 installed. I have attempted to remove the install and install the official deb from adobe's site but run into a wrong arch error when attempting to install it (but I dont see any way to download any other archs)

Any ideas? Im stumped.

---

### Post by gandaran on 2009-05-01
you probably have 64-bits ubuntu, remove the 32-bits flashplugin-nonfree from synaptic and follow [this guide]("http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml") for installing 64-bits adobe flash

---

### Post by gotsanity on 2009-05-01
As far as i can tell I am indeed runing 32 bit. According to system monitor I am running:

```
Release 9.04 (jaunty)
Kernel Linux 2.6.28.11-generic
GNOME 2.26.1

Memory 2.9gb 
Proccessor 0: AMD Athlon(tm) 64 X2 Dual Core Proccessor 3600+
Proccessor 1: AMD Athlon(tm) 64 X2 Dual Core Proccessor 3600+

```

---

### Post by psyke83 on 2009-05-01
This is caused by nspluginwrapper segfaulting on Flash content - this manifests visually as Flash content turning white in Firefox. You most likely have "libflashsupport" installed - it causes instability with Flash and must be removed in order to ensure stability.

I recommend you follow the PulseAudio guide linked in my sig.

P.S. Although it's mentioned in the guide, this is the bug report for your issue: [https://bugs.launchpad.net/bugs/192888](https://bugs.launchpad.net/bugs/192888)

---

### Post by gandaran on 2009-05-01
> **gotsanity said:**
> As far as i can tell I am indeed runing 32 bit. According to system monitor I am running:

```
Release 9.04 (jaunty)
Kernel Linux 2.6.28.11-generic
GNOME 2.26.1

Memory 2.9gb 
Proccessor 0: AMD Athlon(tm) 64 X2 Dual Core Proccessor 3600+
Proccessor 1: AMD Athlon(tm) 64 X2 Dual Core Proccessor 3600+

```
then why do you get that wrong arch error?
to find out type **uname -a** in terminal post the results here

---

### Post by gotsanity on 2009-05-01
turns out I am running 64 bit... the odd part is that i dont remember installing it but i clearly remember thinking... well... i dont really need it :confused:

Thanks for the help anyway guys :)

---

