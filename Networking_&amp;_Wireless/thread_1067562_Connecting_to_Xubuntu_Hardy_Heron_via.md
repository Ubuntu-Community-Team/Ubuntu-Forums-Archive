---
title: "Connecting to Xubuntu Hardy Heron via ???"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by FJ62Driver on 2009-02-12
Sorry, I'm sure the solution to this is obvious to many of you, but I'm a relative newbie, and have spent hours trying to figure this out. Here's the rundown:

Installed Xubuntu 8 on an old tower (Dell 500MHz) a week ago. All is well, get ssh running, etc...

The end goal is to leave it plugged in somewhere in the house connected via wifi, and have me connect to it via ssh (which I've done, but not yet wirelessly) and have it do some number crunching/math simulations for me while my laptop (MacBook Pro) is wherever, checking in.

I have Ubuntu 8 running on a VM (VMWare) on my laptop. I've been using the OS X Terminal to do most of the software installs. 

Here's the breakdown: I'm a total newbie, and many of the instructions require access to the GUI, which I don't have because I don't have a monitor for the box, and actually prefer to learn how to run the thing from the command line. I'm trying to set up any remote desktop type operation. I've tried a number of howto's, and have come up dry. Ideally, I'd like to remote into ye olde' Xubuntu box via 1.) X11 or 2.) Remote Desktop Viewer. Both computers are connected to my Airport Extreme WiFi router. 

I couldn't find anything on using the Mac OS X X11 client, and the Remote Desktop Viewer generates the error "Connection to host "192.168.1.7:5900" was closed. From the Ubuntu VM, I can easily ssh into that same IP address (although my limited knowledge indicates it's port 22 instead of 5900).

Any ideas? Again, sorry if this is obvious. I've just gotten the accursed ndiswrapper to work, and am about out of steam.

---

### Post by cariboo on 2009-02-12
I would suggest trying vnc there are several vnc clients and servers in the repositories, I would suggest tightvncserver on the Ubuntu computer. I'm quite sure there are vnc clients for the Mac operating system.

Jim

---

### Post by FJ62Driver on 2009-02-12
Okay, color me stupid, but maybe I don't understand...

I need some kind of vnc server on the Xubuntu box, right? My installation of the Ubuntu VM on my laptop was in an effort to make it easier to connect to the headless Xubuntu box. 

Maybe it boils down to knowing what I need to install on the computer I want to control remotely, and what I need to install on the computer doing the controlling. I had assumed that Remote Desktop Viewer was what I needed on the computer doing the controlling, and that all I needed to do to the computer being controlled (Xubuntu headless) was enable or allow the connection to come in.

I can ssh in, ssh -X, and get the xclock to come up (not sure if that's even relevant).

All the settings need to be done via command line. Is the desktop environment not running if the keyboard/monitor aren't connected during startup?

---

