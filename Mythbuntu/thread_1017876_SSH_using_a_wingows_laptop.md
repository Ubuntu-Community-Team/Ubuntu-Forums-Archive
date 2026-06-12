---
title: "SSH using a wingows laptop"
date: 2008-12-21
forum: Mythbuntu
---

### Post by Vague Craig on 2008-12-21
Hi all,

Trying to sort out my myth box and am struggling to get ssh working on a windows machine. I've tried following this 
[http://blog.lib.umn.edu/welsh059/blog/2008/09/x_on_windows_you_bet_1.html#more](http://blog.lib.umn.edu/welsh059/blog/2008/09/x_on_windows_you_bet_1.html#more)

but I can't find the xorg-x11-base package in the select packages during setup of cygwin, and when I search for startxwin.bat it isn't where it's supposed to be and doesn't work when run.

Any clues?

---

### Post by albinootje on 2008-12-21
> **Vague Craig said:**
> Hi all,

Trying to sort out my myth box and am struggling to get ssh working on a windows machine. I've tried following this 
[http://blog.lib.umn.edu/welsh059/blog/2008/09/x_on_windows_you_bet_1.html#more](http://blog.lib.umn.edu/welsh059/blog/2008/09/x_on_windows_you_bet_1.html#more)

but I can't find the xorg-x11-base package in the select packages during setup of cygwin, and when I search for startxwin.bat it isn't where it's supposed to be and doesn't work when run.

Any clues?

Looks like you need a ssh-client on the Windows-machine, no ?
Then putty is an easy installation :
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

With putty it should be possible to use the X11 forwarding too.

---

### Post by Vague Craig on 2008-12-21
Thanks, clearly that's much easier! Still don't understand why the other method didn't work,

Thanks!

---

