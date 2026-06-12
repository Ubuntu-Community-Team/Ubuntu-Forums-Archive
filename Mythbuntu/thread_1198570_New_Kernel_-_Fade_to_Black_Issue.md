---
title: "New Kernel - Fade to Black Issue"
date: 2009-06-27
forum: Mythbuntu
---

### Post by SeanOB on 2009-06-27
So I updated to the new 9.04 kernel 2.6.28-13 today.
And now the dreaded 'fade to black' issue has appeared.

After a period of non-activity, the screen fades to black with only the mouse cursor present.

Once this happens I have no control - and have to reboot the machine.

I don't think that it's the screen saver - since I have it configured for a non-blank saver.  And the power save options are all set to off.

Any tips?

Important note: I auto launch the frontend when I boot the machine.  I remember that last time I had this issue I had to create a script to delay the launch of the frontend at boot.

-Sean

---

### Post by ian dobson on 2009-06-27
Hi,

Are you sure it's not the screen saver? On my box I kill xscreensaver in a script, and haven't seen any problems anymore.

Also have a look in the frontend logfile in /var/log/mythfrontend.log for messages about enabling/disabling DPMS.

Regards
Ian Dobson

---

### Post by SeanOB on 2009-07-23
The issue has disappeared!
Probably some update fixed it without my noticing.

Thanks for the help.

-Sean

---

### Post by Caysho on 2009-07-23
I had this too - the screensaver got switched on in a recent update.

---

