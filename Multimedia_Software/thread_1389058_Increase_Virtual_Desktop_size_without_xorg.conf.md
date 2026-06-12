---
title: "Increase Virtual Desktop size without xorg.conf"
date: 2010-01-23
forum: Multimedia Software
---

### Post by Tronman on 2010-01-23
Hello everyone,

I've been trying to extend my desktop via my S-video out. After some searching, I found the xrandr guide here ([http://ubuntuforums.org/showthread.php?t=728157](http://ubuntuforums.org/showthread.php?t=728157)) and can turn the S-video out on and off, which is neat. Ideally I want my laptop monitor at 1280x800 and my TV-out at 800x600 (well, maybe higher, but I'd settle for 800x600). 

This works, but I can only clone an 800x600 size portion of my Laptop display onto the TV out, not make have it have something separate. It seems as though my virtual desktop size is only set to be a maximum of 1280x1280, where I need mine to be 2080x800. But trying to use xrandr -fb to set it higher, it just complains again about only having a max size of 1280x1280 (presumably since X needs to be shut down to change its size). 

Searching around, the suggested advice seems to be to set up a larger display in Xorg.conf. But...using 9.10 I don't seem to have an Xorg.conf, and I can't find any way to increase it's size without it! I tried booting into just a command line, but none of xrandr's options worked as there was no x server running.

So if any knows how to increase the size and make it persistent between reboots, I'd appreciate it! Thanks.

On a (somewhat) related note, would it be possible to have 2 seperate Gnome's running on each display (or even a gnome and an  Xfce or something?) That'd be neat.

Edit: I also noticed the TV out seems to blank when I close the lid. Any advice on that would be helpful too! Thanks.

---

