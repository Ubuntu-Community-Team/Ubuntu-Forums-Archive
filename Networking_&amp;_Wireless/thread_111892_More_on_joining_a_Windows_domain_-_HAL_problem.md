---
title: "More on joining a Windows domain - HAL problem"
date: 2006-01-03
forum: Networking &amp; Wireless
---

### Post by zachariah on 2006-01-03
Hello all,

I have finally got a Ubuntu box to join a Windows Domain, thanks to the SADMS program. Any user from the domain can now sit at the Linux PC and log in with their details.

For some reason, domain users always get a "Failed to initialise HAL" error while the desktop loads. Local users unique to the Ubuntu installation do not get this error. Is this anything to worry about?

Next step - using the network printers (via another Windows machine acting as a print server).

PS - Is the Linux HAL the same as the Windows HAL?

---

### Post by zachariah on 2006-01-13
Update - in GNOME there was nothing descriptive in the error, or in the event logs. I tried Kubuntu (latest version which at time of writing is Breezy 5.10). This showed that the error was with the sound driver (/dev/dsp).

The command 'chmod 666 /dev/dsp*', and 'chmod 666 /dev/dsp/mixer*' seemed to do the trick, but did not survive a restart. Any further ideas?

---

### Post by kaamos on 2006-01-13
Well, one option would be to add these commands to the startup scripts. Someone here can certainly lead you through how to do that.

---

### Post by zachariah on 2006-01-18
Thanks, I've looked it up and resolved it with the following:

Navigate to your /etc/init.d/bash.bashrc file

Add these lines to the end:

chmod 666 /dev/dsp*
chmod 666 /dev/mixer*

This will make sure all users can use sound, for ever and ever amen.

---

