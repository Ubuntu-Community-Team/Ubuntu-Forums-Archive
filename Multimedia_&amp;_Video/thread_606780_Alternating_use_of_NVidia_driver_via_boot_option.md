---
title: "Alternating use of NVidia driver via boot option?"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by ccprog on 2007-11-08
I'd like to have the option at boot time to either load the restricted nvidia driver or stay with the nv driver - ideally simply by two different grub entries. Is there an easy way to do this?

This seems to amount to the question: what happens when the Restricted Driver Manager enables/disables the NVidia driver? Does it only change /etc/X11/xorg.conf? If yes, how could I control this at boot time?

(Background: Some of my software needs 3D acceleration, some other works better with DGA, which is not supported by NVidia. Yet I have not discovered a situation where I might need both at the same time...so this seems to be the least intrusive solution.)

---

### Post by MCMcButtah on 2007-11-08
I am not sure how to do this at boot but wouldn't it be more preferable anyway to do it on the fly? Like maybe a little script to load one copy or the other (depending on which driver you wanted) of xorg.conf and then restart the xserver. When I restart my xserver it loads in less than 2 seconds, def allot faster than a reboot. Just a thaught...

---

### Post by ccprog on 2007-11-08
Well, it takes maybe 5 seconds on mine, but that is an idea.

Now for the embarrasing Newbie-question: what would the xserver restart command look like?

---

### Post by MCMcButtah on 2007-11-08
well ctrl+alt+backspace is the keyboard shortcut...but you would probably want to logout first before you did that. If you are at the login screen there should be a menu option in their to restart X.

---

### Post by ccprog on 2007-11-08
No, what would I use in a script?

---

