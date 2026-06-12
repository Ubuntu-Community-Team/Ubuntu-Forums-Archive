---
title: "xmms-xf86audio + libglib1.2 : problem installing"
date: 2008-05-13
forum: Multimedia Software
---

### Post by Lucky LIX on 2008-05-13
I'm trying to get XMMS 1.2.10 working with the (Logitech) keyboard multimedia buttons, the Itouch plugin makes XMMS crash and I'm having trouble installing the xf86audio plugin:
when trying to install xmms-xf86audio_0.4.4-1_i386.deb gdebi prints "Error: Dependency is not satisfiable: libglib1.2"

These are the packages I have installed on the system related to libglib:
libglib1.2ldbl
libglib2.0-0
libglib2.0-cil
libglibmm-2.4-1c2a
libglib-perl

The problem was not solved by installing libglib1.2-dev so I uninstalled that one after testing.

In ubuntu 7.10 I used an other program to bind the media buttons to XMMS but I can't remember the name or find it in the repositories...

Anyone who can help me? All help appreciated!

PS: an alternative mediaplayer is not an option; I've tried Audacious, Banshee, BMP, Amarok and others but they all have trouble with my (rather long) playlist, lag or crash randomly or... XMMS just works the way it should: fast, very responsive, without any trouble
(my computer is powered with an AMD Athlon Palomino 1500+ and 1GB DDR, running Ubuntu 8.04)

---

### Post by Lucky LIX on 2008-05-16
The program I used to use as an alternative is Keytouch.
But I'd prefer to use the plugin instead of adding yet an other program that runs constantly... Anyone?

---

