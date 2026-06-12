---
title: "2 graphics cards causing Ubuntu lock up during instal."
date: 2005-11-16
forum: Multimedia &amp; Video
---

### Post by waynem on 2005-11-16
Hello!

    New to Ubuntu and I apologize if this has come up before.
I have two graphics cards in my system: 
    1) An onboard I810, with no way of disabling it through BIOS or via a jumper on the motherboard.  I have a cheap Emachines T1150 with a Lomita mainboard and a Intel Celeron running at 1.3Ghz.
    2) An Nvidia GeForce 440MX PCI graphics card, which I currently use as the default graphics card under Windows XP.

    Here's my problem, when installing Ubuntu, everthing goes fine up until 80% though the 2nd phase of the install or configuration phase.  Then my monitor goes blank with a blinking curser in the upper left corning.  I know it has to do with xserver not recognizing my nvidia card as the default card.  I know this from running  sudo dpkg-reconfigure xserver-xorg.  It always dedects the onboard I810 as the default.  I've tried reconfiguring by specifying Nvidia or nv, but to no avail.  Is the any boot parameters that can be passed to the kearnel, while installing, that would tell Ubuntu to use the Nvidia card as the default graphics card?  Any other suggestions that may be of some help or some tutorial on using sudo dpkg-reconfigure xserver-xorg?  I may not be doing something correctly.:(

---

### Post by waynem on 2005-11-18
Well, obviously I'm not going to get any answers from this forum.  So long, Ubuntu!  Back to Xandros 2.0, at least it installs without a glitch.

---

### Post by Thunderguy on 2005-11-18
I'm not sure about your machine, but there could be a bios setting in there,  I'm sure if there were two video cards it would have been confused from the start..  You could try the 'expert' boot param and see if anyways down it might ask you to configure such things, I don't understand what you mean by 80% of the install are you already booted into the OS on the hard drive? if so you might could look at '/etc/X11/xorg.conf' that is the file that the Xserver parses before it runs, there are some guides on Nvidia in the wiki.

I don't think Emachines has a great reputation for any other OS besides XP anyway.... but if Xandros works, Hey.. :)

---

