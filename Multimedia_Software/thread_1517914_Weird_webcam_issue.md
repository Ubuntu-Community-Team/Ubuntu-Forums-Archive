---
title: "Weird webcam issue"
date: 2010-06-25
forum: Multimedia Software
---

### Post by rivera151 on 2010-06-25
I have a webcam that is a little bit of a hurdle to get working.  The shell says GE, but lsusb reports a Microdia webcam.  The default module sn9c102 does not have a vflip module parameter.  I found a link in these forums to a group dedicated to module work for these cams, and I downloaded their driver, sn9c20x, compiled it, and installed it, and I blacklisted the sn9c102 module b/c it interfere.  So far, I have run into the following situation:

1. When I click on any video-using program (skype, kopete, and cheese) through KDE, I get the image upside down.

2. When I run any of the above commands through the terminal, the image shows up correctly.

I am so stumped.  I checked ~/.bashrc ~/.bash_aliases, and /etc/bash.bashrc, and nothing.  Can someone suggest something I might have missed?

---

