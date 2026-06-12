---
title: "Dual Monitor, Grub(?) and Luks"
date: 2012-03-08
forum: Multimedia Software
---

### Post by creiss on 2012-03-08
Hey folks.

I got a HP notebook here (Powerbook) with a docking station. The notebook is closed and the docking station has two monitors (vga, dvi) connected to it. When I am booting I see the nice (cough) lilac boot screen which prompts me to enter my LUKS passphrase. But I only see that on one (l) monitor, the other (r) is lilac, too, but without the prompt. When I boot up the (r) monitor is all garbage, cant make up anything. Seems like incorrectly initialized. Maybe some dual-monitor foo at grub time freaks it out?

However, If i press ctr+alt+del during the LUKS passphrase I force a reboot (doh). Next bootup I get the Debian Grub Splash Screen, I can see the login prompt on BOTH monitors and dual monitor goodness works.

So far I am helping myself by turning on the pc, rebooting, entering pw and then off to work. This aint cool, man ;)

Any help / ideas?
Greatly apprectiated.

**Fix:** Set grub to text mode, timeout to 2 seconds. After that it automagically boots with dual monitor goodness - problem solved.

-Christian.

---

### Post by creiss on 2012-03-14
Hey folks,

to better understand what I am saying I have attached 3 screenshots.

prob1: Passphrase prompt at first boot. Note: Both displays on, but prompt only on one screen.
prob2: The result: only one monitor is working in the X enviroment.
prob3: 2nd boot after exiting first try with ctr+alt+del. Both screens feature the same output, but in X i have multiple monitor goodness.

Any help would be awesome!
-Chris.

---

### Post by creiss on 2012-03-20
Depserate bump!

---

