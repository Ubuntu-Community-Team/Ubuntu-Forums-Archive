---
title: "Very minimal install"
date: 2010-08-02
forum: Multimedia Software
---

### Post by mattshaw on 2010-08-02
Hi there

I am quite a recent ubuntu convert, but have been using debian for a few years now

Let me explain. i have a mini itx board, and small composite screen
to put in the car as a music player, courtesy of mpd and conky.

to test i setup a little vm, and followed a brilliant ubuntu 10.04 minimal install guide over at [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal), where I copied this stage to install x and a window manager etc.

sudo apt-get install xorg xterm gdm icewm menu firefox gksu synaptic --no-install-recommends

that is a good little setup, but I want my install even more minimal. I just need x to start, launching mpd and conky, no menu's, no status bar etc, just an x display with absolutely nothing else.

i know i also need nvidia drivers, to set the graphics card to tv-out rather than vga for my little screen, and to turn off mouse and keyboard (i intend using lirc and a remote control), but cutting down the desktop is my question for now

Can someone please help ??

Regards

Matt Shaw
[email]matt@shagshaw.com[/email]

---

### Post by linux18 on 2010-08-02
I've got a small ubuntu-based distro (see sig) just install and run 
```
 sudo apt-get install fluxbox xterm xinit xorg --no-recommends 
```
then use "xinit" to start x and "fluxbox --replace" for window management 

thats as lightweight as you can get on ubuntu

---

