---
title: "No autoshutdown on WOL slave backend 9.10"
date: 2009-12-06
forum: Mythbuntu
---

### Post by blackoper on 2009-12-06
I cant get mythwelcome or the main backend to shut down my slave system. This slave backend is used very rarely and the wake part of it is fine using wake on lan. The main backend send the WOL packet about 4 minutes before the recording so the hard part is done. I've tried adding my myth user to sudoers file and just about everything else I've found online and the machine never turns off on it's own. If I run mythwelcome it does the countdown to 0 and then restarts the countdown to 120 but nothing ever happens as far as shutdown. I've run it in verbose mode and it doesn't give any details about trying to power down. I do sometimes notice a mythshutdown returns 1 randomly in the output. If I drop to terminal I can run sudo commands without entering password so it does appear the /etc/sudoers file is working. I am currently logging into the box through ssh and running sudo halt -p to turn it off. Am I missing something?

All systems running mythbuntu 9.10 and .22. My main backend is low power and on 24x7.

---

### Post by astrahle on 2011-01-22
Hi blackoper.Did you manage to get your secondary to shutdown after an idle period? Further, how did you get your master to send the wol packet to the secondary? I've got a master with no tuners and my secondary has one. I've got wakeonlan installed and can manually use it to fire up the secondary, but I don't seem to be putting the config in the right place. Can you advise?Cheers,Ashley Strahle

---

