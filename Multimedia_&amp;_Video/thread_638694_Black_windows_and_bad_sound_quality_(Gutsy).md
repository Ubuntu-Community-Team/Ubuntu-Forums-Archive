---
title: "Black windows and bad sound quality (Gutsy)"
date: 2007-12-12
forum: Multimedia &amp; Video
---

### Post by Zteam on 2007-12-12
Hi there!
I'm having 2 problems with my Ubuntu (gutysy) installation that I can't fix...

1. sometimes my when I open a new window it is completly black, thats really annoying,is this a bug in the nvdia driver or something?

2. my sound quality is "noisy" most noticeable then I play music..

Hardware configuration:

CPU: Amd 64 3500+
Motherboard: Asrock 939-DualSATA2
Soundcard: ALI M5455 (Integrated on the mobo)
graphicscard Nvidia 6800LE 128 mb ram

(As a notice everything works just fine under Windows XP)
I'm using the official nvidia driver from restricted driver manager.
desktop effects is on btw...
Any help is appreciated :)

---

### Post by Zteam on 2007-12-13
Isn't there any one out there who even has a single hint? :o

---

### Post by siouzi on 2007-12-13
Nope :( I have the black window problem and Nvidia as well. Now it just became too annoying so I too am looking for an answer... It's application independent and usually the content can be seen after resizing the window.

Edit: It appears to be yet another bug in nvidia. [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/125566]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/125566")

---

### Post by jcarlock on 2008-04-02
Write a script to launch compiz, or launch it from the command line with --indirect-rendering

For example

#  compiz --replace --indirect-rendering

JC

---

