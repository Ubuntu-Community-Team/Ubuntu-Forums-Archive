---
title: "issues with speaker/headphones on Ubuntu 11.04?"
date: 2011-05-19
forum: Multimedia Software
---

### Post by soylentcola on 2011-05-19
So I'm having an issue with my speakers, headphones and my music.  Music plays fine when I play out my speakers, but as soon as I plug in my headphones, it mutes and won't play out either my headphones or speakers.  When I plug the headphones out, it'll play through the speakers again.  I ran alsamixer and hosted the output [here]("http://www.alsa-project.org/db/?f=35000dbe342d4d5292a0b2e34e5a892f3d83a645"), if it'll help.

I'm kind of green with this whole Ubuntu setup so if I'm slow picking things up, bear me with me.

---

### Post by soylentcola on 2011-05-19
**_Solved_**

This is what I did to get it to work! (you'll need to install gnome-alsamixer)

1) Open gnome-volume-control
2) Click on the "Output" tab.
3) Change "Connector" to "Analog Headphones"
4) Open gnome-alsamixer
5) Turn the "Front" channel up to maximum volume.
6) Close gnome-alsamixer
7) Use gnome-volume-control to adjust volume/mute/unmute.
If you want both headphones and speakers, open gnome-alsamixer and unmute the "Front" channel.

I'm running an ASUS K60I, so hopefully this'll fix it for others having the same issue. :)

---

### Post by daniobg on 2011-07-18
Thank you very much!!! It works perfect on Asus K50IJ :)

---

