---
title: "bluetooth issues"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by rmetzger on 2009-11-20
While poking around the PC I found that my bluetooth wasn't functioning (compaq cq60-420 with 9.10).  I installed blueman (1.22) and get the following error when starting "Bluez daemon is not running, blueman-manager cannot continue."  From the "http://blueman-project.org/downloads.html" site I completed the following to no avail:

In Ubuntu **Karmic** you can add blueman repositories by issuing this command:
**sudo add-apt-repository ppa:blueman/ppa**[URL="https://help.launchpad.net/Packaging/PPA/InstallingSoftware"]

[/URL]And to install it run:
[B]sudo apt-get reload
sudo apt-get install blueman[/B]

any suggestions?

thanks
Ron

---

### Post by dazzakoh on 2009-12-04
I have a smiliar problem:   blueman was working fine until sometime this week, when it started giving me the "Bluez daemon is not running..." error.

I have reinstalled anything to do with bluetooth, but still nada.  Nothing working. 

Any ideas what next?

---

### Post by dazzakoh on 2009-12-04
Okay.  Looking a bit sheepish, but please check your setup in the BIOS of your computer:  for reasons unknown, mine had the bluetooth device disabled.  Why"?  I do now know as I did not disable it.. but in the course of the last few updates, it must have happened.

Once that was turned back on, life returned to normal...

---

