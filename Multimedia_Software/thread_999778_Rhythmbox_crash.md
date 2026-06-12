---
title: "Rhythmbox crash"
date: 2008-12-02
forum: Multimedia Software
---

### Post by taps on 2008-12-02
I'm on Intrepid, bang up to date on packages.

I use Rhythmbox as my music player and also for podcasts. I currently have a long backlog of a particular podcast. Every time I turn Rhythmbox on, it starts to download the podcast episodes, the programme crashes within a few minutes, with ```
Segmentation fault
``` as the only explanation in the console.

I don't know if it's relevant that the programme starts with the following error message: ```
(rhythmbox:27588): Rhythmbox-WARNING **: Could not open device /dev/radio0
```

---

### Post by xc3RnbFO8P on 2008-12-02
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/192624]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/192624")
> Stefan Glasenhardt  wrote on 2008-02-17:  (permalink)

There is a very easy workaround for this bug :

Reactivate the "display cover"-plugin in Rhythmbox. This can be done with "gconf-editor" :

"/apps/rhythmbox/plugins/artdisplay/active" has to be set to "true". After this Rhythmbox works normally.

In Terminal:
> gconf-editor

---

### Post by Nevermor7 on 2009-07-21
Mine was set to true- same issue persists.

---

### Post by mdgill on 2010-08-13
I have the same problem, which I describe here: [https://bugzilla.gnome.org/show_bug.cgi?id=625497](https://bugzilla.gnome.org/show_bug.cgi?id=625497)

Can anyone help me with Bug Buddy?  I installed it via Synaptic with all the indicated dependencies, but nothing "pops-up" when Rhythmbox crashes.

---

