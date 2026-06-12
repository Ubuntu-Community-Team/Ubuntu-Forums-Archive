---
title: "Open Sound (OSS4)"
date: 2011-01-01
forum: Multimedia Software
---

### Post by Runaway1956 on 2011-01-01
Alright - I'm in the middle of installing a fresh Ubuntu onto real hardware.  (as opposed to yet another virtual machine, lol)

I want OSS4 instead of Alsa and all the rest.  (primarily, because it handles sound from virtual machines, whereas Alsa falls on it's face)

Purging and blacklisting Alsa, then installing OSS4 is a minor headache.  Has no one yet created a script to do this, all automagically?

More importantly - when is Ubuntu going to support OSS4 in the repositories?  Really, OSS4 is superior to Alsa and Pulse in several ways.  At this point in time, a guy should be able to choose Alsa or OSS during setup, and Ubuntu should just install everything, with no post-install tampering by the user.

Alright, so my post makes it obvious.  I'm not a real Linux guru, AND, I'm a bit lazy.

All the same - if anyone knows of a good, simple, and tested script to make installing OSS4 painless - PLEASE post a link here!

Thanks!

---

### Post by Yellow Pasque on 2011-01-01
I wrote a guide ( [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound) ) to install OSS4. It's not quite as easy as a script, but if you can follow directions and know how to copy+paste, you'll be okay. Sorry, but I'm probably not going to put much effort into doing things for OSS4 anymore since I no longer use it on most of my installs, it's not very actively maintained/developed, and Debian/Ubuntu devs don't want to support it (oh, and I'm fairly lazy as well :P ).
As a final nail in the coffin, Ubuntu has stripped OSS support from its kernel in Maverick. In general, the repo version of OSS4 in Debian-based distros doesn't work, and I haven't seen any recent interest from Debian or Ubuntu devs in fixing bugs in OSS4-related packages.

---

### Post by qamelian on 2011-01-01
Whether or not OSS is superior is a matter of taste. I've tried it in my home recording studio and found it crap compared to Pulse+ALSA.

---

