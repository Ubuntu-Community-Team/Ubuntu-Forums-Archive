---
title: "New install, X is crashing"
date: 2011-04-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by epblash on 2011-04-07
Just installed, select the latest option from GRUB on bootup, and I get the dialog that says "It seems that you do not have the hardware required to run Unity...", etc. So I try to hit the close button. No go - mouse doesn't move, keyboard is frozen. Can't hit ctrl-alt-F2 for a virtual console. Only thing that responds is hitting the power button.

Trying to repair broken packages in recovery mode runs, but doesn't find anything. Trying to run the failsafe graphics mode gets me a dialog saying that Ubuntu is in low-end graphics mode, and I can't click "OK" on that either. 

Any ideas?

---

### Post by nagasowski on 2011-04-07
Hello,

Have the same problem.
It started to crash today, after upgrading all packages to the newest version (apt-get upgrade). Yesterday I could log in.
I have a Lenovo T400 with Intel graphics.

Any ideas?

Greetings

Got answer (thx to jacekalex)
It looks like You have got the same problem - udev.
[New udev]("http://aptosid.com/index.php?name=PNphpBB2&file=viewtopic&t=1093")
Pluging USB mouse and keyboard after boot solves the problem temporally. 
Thinking of downgrading udev to earlier version.

---

