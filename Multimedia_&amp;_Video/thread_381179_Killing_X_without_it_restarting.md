---
title: "Killing X without it restarting"
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by jswhite on 2007-03-10
I've got a (more or less) fresh install of Edgy on an Alienware laptop with a GeForce FX Go5700 card. I used to run MEPIS on here, but recently made the switch to just Ubuntu. NVIDIA drivers are notoriously difficult to get running properly on this computer, so I can expect this to be something of a tedious process.

Here's what I usually get. After installing nvidia-glx, setting xorg.conf to use the "nvidia" driver instead of "nv", and restarting X; X will frequently end up just displaying a mass of junk on my screen. It looks like a fractal image, with lots of purples and blues. Kinda hard to explain beyond that. I can tell from sounds that Gnome (or KDE, if I happen to use that) actually did load, and I can still click on things if I happen to have my cursor in the right place, but I get absolutely no visual display other than that damn scramble junk.

That situation is generally remedied by a half-ton of experimentation with xorg.conf settings, and it takes a while to figure out. In the mean time, I will need to quickly and easily switch between "nvidia" (which, most of the time, will just display useless junk) and "nv" (which is just fine and lets me work in Gnome). I could handle that if I could quickly kill X and bring up a command line, because at least then I could edit xorg.conf with nano or something.  Is there any way to do that?

And please don't say CTRL+ALT+BACKSPACE. That does kill X, but immediately restarts it again, which kinda defeats the purpose of what I'm trying to do. :)

---

### Post by vayde on 2007-03-10
Hit Ctrl-Alt-F1 to pull up a virtual console.

Log in there and do whatever editing you need to do to xorg.conf.

When you want to restart type one of the following as appropriate:

```

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
sudo /etc/init.d/gdm restart

```



To go from virtual console to gui hit Alt-F7 or Ctrl-Alt-F7

---

### Post by jswhite on 2007-03-10
Awesome, that was exactly what I was looking for. Thanks for the help!

---

### Post by vayde on 2007-03-10
My pleasure.

---

