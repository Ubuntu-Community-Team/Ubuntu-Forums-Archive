---
title: "Broadcom 4322 worked in 9.10 RC, but not in final"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by bsmith1051 on 2009-11-01
I have a new Dell Vostro 1520 laptop with a Broadcom BCM4322 wi-fi adapter.  This is a dual-band g/n model.  I've been reinstalling different OSes for the past month and I thought I'd settled on Ubuntu 9.10 since it worked perfectly with the Release Candidate just a week ago or so.  (It might have been with the beta?)

Now, I've got a fresh reinstall of 9.10 'Final' and the System > Hardware Drivers recognizes my wi-fi but then balks at activating it; I click 'Activate' and nothing happens.

How do I troubleshoot this and what could have changed (since this worked without incident before) ?
_________

Actually, I think it might be failing to authenticate my password?  It doesn't say anything about that but that seems to be how it's acting.

---

### Post by CrazyMike on 2009-11-06
I had this same problem.  I had to plug in the ethernet cable on my router to get the initial updates loaded then had some success:

I updated by sources.list by uncommenting the preinstalled comments then ran the update manager.  After a reboot, I was then able to access and activate the Broadcom driver.  Twice it locked up my computer trying to get the driver to activate, however, once it did, it has been working fine with the exception of some poor transmission continuity as we are discussing here:  [http://ubuntuforums.org/showthread.php?t=1316195](http://ubuntuforums.org/showthread.php?t=1316195)

My computer is a Dell Studio XPS 13 (1340)

---

### Post by bsmith1051 on 2009-11-06
Thanks!  I'll plug it in and download all the recent updates, then try it again...

---

