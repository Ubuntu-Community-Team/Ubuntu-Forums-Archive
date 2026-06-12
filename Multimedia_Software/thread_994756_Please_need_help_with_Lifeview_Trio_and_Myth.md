---
title: "Please need help with Lifeview Trio and Myth"
date: 2008-11-27
forum: Multimedia Software
---

### Post by scrumpy111 on 2008-11-27
Hi All,

I am trying to install the Lifeview flydvb trio but can only see 2 cards in Mythtv backend and cannot get any channels either.
I have been looking and reading ever thing I can find for the past week but have no luck.
I did find a post from April 2007  Unknown TV tuner + feisty
it suggests doing this

"sudo rmmod saa7134-alsa"
"sudo rmmod saa7134"
"sudo modprobe saa7134 card=84 tuner=61" (I tried everything in the video4linux list here too)

I believe my card=84 and Tuner=61
but when I try the above I get

neil@neil-desktop:~$ sudo rmmod saa7134-alsa
ERROR: Module saa7134_alsa does not exist in /proc/modules
neil@neil-desktop:~$ sudo rmmod saa7134
ERROR: Module saa7134 is in use by saa7134_dvb

What or how can I resolve this

By the way I am complete noob on Ubuntu Ibex

Thx in advance

---

### Post by scrumpy111 on 2008-11-27
Doesnt anyone have any ideas or info

---

