---
title: "Line 6 Pod XT Live rcording in Ubuntu"
date: 2007-11-30
forum: Multimedia Production
---

### Post by spaparat on 2007-11-30
I've got a Line 6 Pod XT Live and I used to use it to record the guitar in Windows through the USB port. I was wondering if there was a way to set this up in Ubuntu. It recognizes it when I plug it in but I can't figure out how to set it up in Ardour or in anything else to record. I've scoured google and can not find anything on how to do this.

Any suggestions?
Thanks in advance.

---

### Post by Stochastic on 2007-12-05
hmm, I have no experience with Line 6 gear, but I'll try to help.  If ubuntu recognizes it, then try opening qjackctl, open the setting window, and in devices, see if it's available.  If it is, select it, close the settings window, and try starting JACK.  Once jack is running simply open Ardour or any similar jack-based app (rezound, jokosher, audacity, etc...), connect the inputs in qjackctl, and record away.  Let me know how far this gets you.

---

