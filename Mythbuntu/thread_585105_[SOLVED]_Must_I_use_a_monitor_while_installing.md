---
title: "[SOLVED] Must I use a monitor while installing?"
date: 2007-10-21
forum: Mythbuntu
---

### Post by meanmrmustard on 2007-10-21
I'm installing on a box that presently has Knoppmyth and has only a TV connected.
How can I get the TV to display the installation process?

---

### Post by uopjohnson on 2007-10-21
How are you connected to the TV?  Can you see the POST when you restart?  If you are using the TV out on a video card you should be able to do the install on the TV without a lot of trouble.  If you are using the TV out on a PVR-350 I don't think there is any way to make it happen unless you build a custom ramdisk on the install media with modules for the 350s tv out, but that is probably far harder than dragging a monitor in from the office and setting it on the floor for an hour.

You could also try modifying the directions for an unattended ubuntu install:
Google [  Search Link]("http://www.google.com/search?q=unattended+ubuntu+install&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a") turns up a few guides.

---

### Post by meanmrmustard on 2007-10-21
It's an S video output from an Nvidia card.

I see the POST and the progress bar screen and I hear the audio when the desktop should appear but by that point the screen is black.

I'll have a look at the links - thanks for the input.

---

### Post by superm1 on 2007-10-21
Something else to consider trying would be safe graphics mode.  The nv driver doesn't support tv out, but i think the tv out will remain if you use the vesa driver.

---

### Post by meanmrmustard on 2007-10-21
That did it.

Thanks

---

