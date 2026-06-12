---
title: "Lost all sound, package audio does not exist"
date: 2010-12-03
forum: Multimedia Software
---

### Post by ricky222 on 2010-12-03
Hi, I was trying to get help with video tearing but now I've lost all sound. This happened after using these two commands:

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo dpkg-reconfigure -phigh xserver-xorg

I tried this:
ubuntu-bug audio 
and got:
package audio does not exist
and:
ubuntu-bug -p alsa-base 
and got:
Warning: The options -p/-P are deprecated, please do not use them.  See /usr/bin/ubuntu-bug --help

Any help appreciated.

---

### Post by SlugSlug on 2010-12-03
what dist you using?

I dont think xorg does the sound these days..  
you could try
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.broke
sudo mv /etc/X11/xorg.conf.old /etc/X11/xorg.conf
sudo reboot

---

### Post by ricky222 on 2010-12-04
Sorry for the delay replying, I'm using Ubuntu 9.10-Karmic Koala Gnome Desktop, I will try those, thanks.

---

