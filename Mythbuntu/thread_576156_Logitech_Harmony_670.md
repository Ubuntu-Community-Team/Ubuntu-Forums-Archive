---
title: "Logitech Harmony 670"
date: 2007-10-14
forum: Mythbuntu
---

### Post by w00tfest99 on 2007-10-14
I have a logitech harmony 670 remote.  I've read many other threads that say it's not possible to update the remote in Linux.  I'm fine with this as I have another machine with Vista on it that I can update it on.  However, I'm worried that I won't be able to actually control mythtv with the remote.  I've gotten the remote that came with my TV Tuner to work.  What am I going to need to do to get the logitech to do the same?

---

### Post by superm1 on 2007-10-15
You just need to map your harmony's buttons to have identical buttons as your tv tuner remote.

When you do your mythbuntu install, just choose your normal remote control.  Since the buttons are mapped over identically, the harmony should "Just Work" (TM)

---

### Post by dmfrey on 2007-10-15
I can verify that this works.  I have a Harmon 880 and it is mapped to MCE (Philips version).  Selecting the correct remote and the existing harmony configuration just works after a fresh install of mythbuntu.

---

### Post by w00tfest99 on 2007-10-15
I'm sorry, I'm really new to this.  How do I map my harmony's buttons to have identical buttons?

---

### Post by superm1 on 2007-10-17
Well what IR receiver do you have?

If you have a mceusb/mceusb2 receiver, then its a matter of just choosing "Microsoft Media Center remote" in your Harmony configuration software.  Likewise if its a hauppuage, you'll choose that in your Harmony software.

---

### Post by oPossum on 2007-10-19
Many Harmony remotes can be programed from Linux.

[http://www.sourceforge.net/projects/harmonycontrol](http://www.sourceforge.net/projects/harmonycontrol)

---

### Post by newlinux on 2007-10-19
> **oPossum said:**
> Many Harmony remotes can be programed from Linux.

[http://www.sourceforge.net/projects/harmonycontrol](http://www.sourceforge.net/projects/harmonycontrol)

Yes, this is what I use for my 680. Works fine. Just use the old web interface to the harmony software and then download the config file and have this utility upload it to your remote.

Leaving me with only one piece of software left that I need windows for...

---

### Post by newlinux on 2007-10-19
My harmony emulates the Media Center remote using the mceusb2 driver. I changed a few things around, but works great.  What remote do you currently have working?

---

### Post by hinge on 2007-12-01
I've just setup the linux software for the harmony remote - but now I can't fing the harmony website that ligitech used to have ... is it just me or did they close it - anybody have it their bookmarks ?

:(

---

### Post by B3rt on 2007-12-06
I cannot get the installer to run..

I downloaded the package en ran: make (tried also sudo make)

I get an error back:
 make
g++ -g -Wall -O2 binaryfile.cpp harmony.cpp remote.cpp web.cpp libusb/libusbhid.cpp usblan.cpp remote_z.cpp xml_headers.h -o harmony -lusb 
make: g++: Opdracht niet gevonden
make: *** [harmony] Fout 127

Translated: command not found & error 127

Why I try to install libusb I get also an error:

sudo apt-get install libusb
[sudo] password for robert:
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Reading state information... Klaar
E: Kon pakket libusb niet vinden

Translated: could not find package libusb

When I use the synaptic manager and search on libusb it reports:
libusb-0.1-4  version 2:0.1.12-7 (installed)
libusb++-0.1-4c2 (installed)

What do I wrong here?

(running on ubuntu 7.10)

---

### Post by superm1 on 2007-12-07
You probably need to install build-essential

---

### Post by newlinux on 2007-12-07
> **hinge said:**
> I've just setup the linux software for the harmony remote - but now I can't fing the harmony website that ligitech used to have ... is it just me or did they close it - anybody have it their bookmarks ?

:(

members.harmonyremote.com

---

### Post by Slade Winstone on 2008-06-03
Hi,

It looks like the HarmonyControl project at sourceforge has been renamed "Concordance" [http://sourceforge.net/projects/concordance/](http://sourceforge.net/projects/concordance/)

Slade.

---

### Post by djbon2112 on 2008-08-06
I followed your advice, but when I try to connect, Congruity gives me a segfault, and concordance says it can't find the remote:

joshua@laptop-001:~/Desktop$ /usr/bin/congruity Connectivity.EZHex
/usr/share/congruity/remote.png
/usr/share/congruity/icon-unstarted.png
/usr/share/congruity/icon-in-progress.png
/usr/share/congruity/icon-complete.png
/usr/share/congruity/icon-failed.png

(python:25633): Gtk-WARNING **: Theme directory scalable/places/22 of theme black-white_2-Gloss has no size field

[I press the "Next" button]

Segmentation fault

joshua@laptop-001:~/Desktop$ concordance Connectivity.EZHex
Concordance 0.20
Copyright 2007 Kevin Timmerman and Phil Dibowitz
This software is distributed under the GPLv3.

Error initializing libconcord: Error connecting or finding the remote

---

### Post by newlinux on 2008-08-06
try using sudo - I always need root priveleges when I use concordance.

---

### Post by djbon2112 on 2008-08-06
>.< Am I an idiot! I thought I'd tried that, but I guess not. It worked!

---

### Post by honeybear on 2011-08-21
> **newlinux said:**
> members.harmonyremote.com

and then what you do iwth the exhez file. Even with MS VISTA OR MICROSOFT XP it does not work...

Man, I will give this i300 back. What a piece of non-working device. Usually logitech do good, but then, here we have a complete failure... :(


And installation under windows is highly complicated : 

> 
==== BASIC INSTALLATION ====

0. INSTALL REQUIRED SOFTWARE

You need one these Development Platforms:

a) Microsoft Visual C++ 6.0 with Service Pack 6 (SP6)
b) Micosoft Visual Studio 2005 (8.0)
c) Micosoft Visual Studio 2008 (9.0) - Express Edition

And you will also need to install the platform SDK.

1. BUILD THE SOFTWARE

Open the Project tree in your Development-System, by (letters here correspond
to development environment above - pick one):

a) Open the Workspace-File for Visual C++ 6.0 '.\win\concordance.dsw'
b) Open the Solution file for Visual Studio 2005 '.\win\concordance.sln'.
c) Open the Solution file for Visual Studio 2008 '.\win\concordance.sln'
   (the 2005 sln-file format will be converted to the new (2008) format
    automatically the first time you open the project tree.)

Now you should see four Projects in your Workspace/Solution-Tree

- libconcord_libusb: a dynamic link library using the libusb package (see note 1)
- libconcord_winhid: a dynamic link library using native win-usb support

- concordance: a cli that utilizes the library

- consnoop: A debugging program for concordance developers


---

