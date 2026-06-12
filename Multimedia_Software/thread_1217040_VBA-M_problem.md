---
title: "VBA-M problem"
date: 2009-07-19
forum: Multimedia Software
---

### Post by swoopdawoop on 2009-07-19
Whenever I (attempt to) execute it, nothing happens.

---

### Post by DEagleson on 2009-07-23
I have the same problem here too.
Wont start on Ubuntu 9.04 on my ASrock ION 330.

---

### Post by sukigenseki on 2009-08-06
Even though the package claims dependencies are satisfied if you try to launch gvbam from terminal it says that it fails to initialize "libgtkglextmm-x11-1.2-0", and installing that dependency from synaptic, or if you want you can use

sudo apt-get install libgtkglextmm-x11-1.2-0

and it solved the problem for me!

BTW I had to choose vba-m over the vba in the repository because the repo version wouldn't recognize my sweet new logitech dual action gamepad, and thankfully the vba-m version had no problem.

---

### Post by sukigenseki on 2009-08-06
Matter of fact instead of doing that, first just try to run gvbam in the terminal, and if it gives you an error message that has a package in it just check synaptic with a search to see if that package is installed; messing around with vba-m has given me wierd dependency issues with the program, and i have had to install a few things from synaptic which changed with each install of vba-m, and all of them worked after using the terminal to see what it was missing. Hope this works for you guys!

---

### Post by harrypotter123 on 2010-03-29
I have Ubuntu 9.04. I tried to get the Pokemon games in Ubuntu, and when I used Synaptic, the VisualBoyAdvance file appeared in usr/share...inside the file, there was only a "vba.glade" and "vba-64.png file, no exe file.......How do I get to activate the VBA?

---

### Post by harrypotter123 on 2010-03-30
> **sukigenseki said:**
> Matter of fact instead of doing that, first just try to run gvbam in the terminal, and if it gives you an error message that has a package in it just check synaptic with a search to see if that package is installed; messing around with vba-m has given me wierd dependency issues with the program, and i have had to install a few things from synaptic which changed with each install of vba-m, and all of them worked after using the terminal to see what it was missing. Hope this works for you guys!

How do you use the terminal for gvbam?

I use Ubuntu 9.04 Jaunty Jackalope......Please reply fast.

---

