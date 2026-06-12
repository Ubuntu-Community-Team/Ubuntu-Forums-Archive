---
title: "i915 video - solutions I've found here doesn't work for me"
date: 2005-11-03
forum: Multimedia &amp; Video
---

### Post by flower on 2005-11-03
Hi hardware geeks, I'm trying to spread Ubuntu in Bulgarian Academy of Sciences, but I have strange hardware problem.

New Intel Motherboard with integrated Video Card.
Breezy installs with NO problems and detects the Video Card as (Intel i915 integrated video card) and uses driver "i810". But .. when everything is loaded and switching to X .. the pc restarts.

I've searched the forum and I've found dozen solutions... tried them all and nothing works.

I've installed the i915 driver from freedesktop.org ... but it gives me strange error "i915Moduledata object data not found" ... googling for that message gives no answer ... 

I've tried other stuff also - like 855resolution package, but doesn't help aslo.

I've tried with "vesa" but the screens goes funny and no sane picture is visalized.

Hint : I booted in Knoppix3.7 which uses XFree86 for graphics and .. it works !!! damn ! in the xfree86 config file it uses "svga" driver ... I tried `svga` driver in ubuntu but there's no such installed 

so ... please help me with that... I really want to install Ubuntu on these machines. It's not for me... It's about spreading it after all ...

---

### Post by flower on 2005-11-08
I've read in Intel web site that i915 works only on XFree86 ... 
ans since I don't know this much .. is that's why it doesn't work (at all for me) with X.org ?

---

### Post by shof2k on 2005-11-17
Hi,
Have a look in /var/log/kern.log and /var/log/xorg.log and see if there are any meaningful messages there?  You could try installing the i810 and common modules from freedesktop.org as well?

Good luck!

---

### Post by jotape99 on 2005-11-18
On a dell GX280 with i915 integrated graphic card, on a fresh install of breezy, I do the following:
- install the 855resolution packet (with synaptic)
- on a real text console !!! (switch to it wiht CTRL+F1):  'sudo dpkg-reconfigure xserver-xorg' 
- restart the xserver (you can use windows method: reboot, or only restart gdm: 'sudo /etc/init.d/gdm restart' )

works ok for me.

PS: I run twice the command 'sudo dpkg-reconfigure xserver-xorg', at the first attempt my monitor wasn't recognised.

---

