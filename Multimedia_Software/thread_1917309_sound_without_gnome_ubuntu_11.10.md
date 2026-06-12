---
title: "sound without gnome? ubuntu 11.10"
date: 2012-01-29
forum: Multimedia Software
---

### Post by sneilan on 2012-01-29
I'm using Ubuntu 11.10 with Xdmx/Xmonad without Gnome on a macbook air 4,2. 

Xdmx is an X Server that allows you to use other Linux computers running X11 as monitors. Literally, monitors connected by ethernet.

Xmonad is a window manager that is like Vim for your desktop. It manages your windows for you so you can focus on more important things like programming.

When I go onto my computer, I first stop gnome with sudo service gdm stop and then run xinit & xmonad. This means that xmonad is running directly on top of a bare bones X11 server.

Unfortunately, there is no sound and doing 
sneilan@sneilan-MacBookAir:~$ sudo service pulseaudio start
 * PulseAudio configured for per-user sessions
doesn't turn it on.

If I run alsamixer, I get
sneilan@sneilan-MacBookAir:~$ alsamixer
cannot open mixer: No such file or directory

Sound works normally in Gnome and Xmonad running on top of Gnome.

How would I start my sound up without going into gnome?

Thank you for your time.

---

