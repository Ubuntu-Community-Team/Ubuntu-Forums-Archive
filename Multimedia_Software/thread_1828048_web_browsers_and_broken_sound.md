---
title: "web browsers and broken sound"
date: 2011-08-18
forum: Multimedia Software
---

### Post by jbeiter on 2011-08-18
I feel like I go searching for some fix for sound on Ubuntu at least once a year.

I'm running 10.10 and sound works great... **except for with web browser**s. Namely Chrome and firefox.

I've tried just about every thread I can find to fix this. pulseaudio is loaded, alsa-oss... flash-nonfree-**** loaded.

This really shouldn't be this hard, should it? Hell I've been working with linux since it was distributed on fidonet and have admined unix for 20 years. WTF?

any suggestions would be greatly appreciated.

---

### Post by An Sanct on 2011-08-18
Try Flash Aid, the firefox add-on, it does magic with flash.

You did not tell us what you are trying to do ... so my guess is, you are having flash related problems. Flash is non-free, thus not a Linux problem. Well it actually is a problem, but since it is closed source we cannot do anything about that.

ps. (> W.. well, that does not bother me, but some admin might be bothered)

---

### Post by gordintoronto on 2011-08-18
Did you install the "restricted extras?"

What specific sound is not working? Youtube? A radio station?

---

### Post by lidex on 2011-08-20
Have a look here:
[http://www.webgapps.org/tutorials/firefox/troubleshooting/flash-issues-and-solutions](http://www.webgapps.org/tutorials/firefox/troubleshooting/flash-issues-and-solutions)

---

### Post by jbeiter on 2011-12-27
was working, spontaneously stopped working again. flash-aid already installed, updated to the latest stable.

tried the asound.conf route, no asound-gtk for  10.10, apparently.

WTF does this fail so much?

Anything with sound via web browser (google voice, youtube, etc...)  I have to boot windoze to listen to a google voice mail... how embarrassing.

---

### Post by gordintoronto on 2011-12-27
It wouldn't hurt to describe your computer a bit, including output from the command: lspci

I would be surprised if the problems persisted if you did a clean install of 11.10. You could always try a Live CD.

---

