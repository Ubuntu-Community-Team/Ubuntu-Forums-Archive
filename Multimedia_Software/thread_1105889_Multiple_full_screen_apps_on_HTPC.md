---
title: "Multiple full screen apps on HTPC"
date: 2009-03-25
forum: Multimedia Software
---

### Post by indie_design on 2009-03-25
I have an ubuntu-based HTPC, whose primary HID is a Logitech Harmony remote control, running commands via LIRC.

My aim is to have multiple, independent fullscreen applications, all of which share the same hardware (including monitor), these interfaces are:

* XBMC (primary interface at bootup)
* MythTV
* Gnome (I can plug in a keyboard when I want to use this)

Potential solutions and problems are:

1. Use compiz to arrange fullscreen applications on different sides of the cube:

PROBLEM:
* Compiz doesnt play well with XBMC
* I cannot find a command-line way to arrange which desktop an application resides.
* Doesnt restrict gnome windows to only the gnome side of the cube
* Gnome handling of events (e.g. DVD inserted) takes precidence.

2. Multiple independent X sessions

PROBLEM:
* No idea how to do this!
* Even if it is possible, there are likely to be issues with sharing hardware.

3. Use virtual machines

PROBLEM:
* very inefficent to have multiple installations to maintain.
* I doubt that nvidia's graphics drivers play well with a VM.

4. Use a bunch of scripts to start/stop different X sessions.

This currently seems like the easiest solution.

PROBLEM:
* Doesnt leave each application running in the background.

Given the flexibility of the remote and LIRC, I can be quite flexible about initiating scripts on the HTPC, but I dont have a mouse for the most part.

Anybody got any clever suggestions? In particular in the realm of multiple X sessions sharing hardware.

---

### Post by SR_ELPIRATA on 2009-12-26
Far as I remember, xbmc and gaming (both use 3d acceleration I think) dont work at all with compiz and the cube :(

I remember reading that they were working on an interface or plugin/script (if its not already completed) so that you could connect to your mythtv server and browse your recordings from xbmc.

About the keyboard... isnt it more simpler to just have a wireless keyboard already plugged in? Or just a normal keyboard and hide it somewhere.

The gnome thing I dont understand, xbmc runs on ubuntu which has gnome....

---

