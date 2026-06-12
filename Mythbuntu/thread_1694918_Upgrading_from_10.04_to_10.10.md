---
title: "Upgrading from 10.04 to 10.10"
date: 2011-02-25
forum: Mythbuntu
---

### Post by TorstenS on 2011-02-25
Hi all!

I have upgraded from 10.04 to 10.10 though the update manager. I did not get any error messages, everyting seems to be smoothly working.

Just unfortunately, I have an empty desktop now after reboot.

What I mean is:

There is the "Application" menu, but it's empty. In the upper right corner, there is the network symbol and the clock, nothing else.

Any idea what might have gone wrong and how to fix it?

Regards,
Torsten

---

### Post by ajgreeny on 2011-02-25
Difficult to know, but try renaming the ~/.gconf folder in your home as ~/.gconfbak and see if you now get the default desktop layout.  If that works, you can either reset everything as you want, or try restoring the sub-folders of the old backup version until something goes wrong again.

---

