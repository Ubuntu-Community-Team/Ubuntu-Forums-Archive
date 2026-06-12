---
title: "[SOLVED] Failed to start X server with MythTV"
date: 2007-09-19
forum: Multimedia &amp; Video
---

### Post by middlewordie on 2007-09-19
I have the same problem as [here]("http://ubuntuforums.org/showthread.php?t=515473") - when i boot up after installing a new video card (after numerous problems - see [here]("http://ubuntuforums.org/showthread.php?t=553297")).

I click Exit after getting the "failed to start" screen

Then I get loads of stuuf about X Window System etc...

including

Using Config file: "/var/log/Xorg.conf"
(EE) No devices detected.

Fatal server error:     <EXIT>

When I click EXIT I get

Would you like to view the detailed X Server output as well?

I clicked <Yes>

Then I get More X Window stuff

and another <EXIT>

I'm then told X Server is now disabled and to restart GDM when i is configured correctly <OK>

I click OK and I don't get the opportunity to go to the command line because boot then carries on until:

* Checking battery state... [OK]
* Running local boot scripts (etc/rc.local)  [OK]

then nothing happens...

any thoughts?

---

### Post by w4ett on 2007-09-19
the easiest way to get to a command line will be to boot into recovery mode from the grub boot menu:

---

### Post by middlewordie on 2007-09-19
ok i've reconfigured it and i now have a working machine back! hooray

---

