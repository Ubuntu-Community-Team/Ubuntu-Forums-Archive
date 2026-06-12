---
title: "How can I upgrade my alsa driver?"
date: 2007-03-08
forum: Multimedia &amp; Video
---

### Post by bracc0 on 2007-03-08
Hi everyone,

I have no sound on my laptop. I have been kindly addressed to a fix but I am newbie enough to cannot execute that solution.

The solition consists in upgrading the alsa driver. My ubuntu edgy installation uses alsa driver 1.10.12 release. I want to install 1.10.14rc3.
I downloaded the three alsa packages (driver, util, dev), I uncompressed and untard them, I ran succesfully for all packages ./configure, sudo make, sudo make install but...
Synaptics keep showing alsa driver 1.10.12.

If I ask Synaptics to uninstall alsa stuff he warns that it will be removed about 20 more packages/libraries, so i stopped there. I ran "check for upgrades", but alsa 1.10.12 seem to be the latest approved by edgy.

Can anyone suggest a clean way to upgrade alsa driver?

Thanks
Claudio

---

### Post by Bwosc on 2007-03-08
What kind of laptop do you have? Can you post the link where you found the solution?

---

### Post by bracc0 on 2007-03-08
My laptop is a Fujitsu-Siemens Lifebook 1410.
The sound card is an Intel (requires snd-hda-intel driver).

My original post:
[http://www.ubuntuforums.org/showthread.php?t=376682](http://www.ubuntuforums.org/showthread.php?t=376682)

A solution for a different laptop but suitable for mine too:
[http://www.ubuntuforums.org/showthread.php?t=324764](http://www.ubuntuforums.org/showthread.php?t=324764)

Any idea about how to get rid of alsa driver 1.10.2 in favour of 1.10.14rc3?

Thanks in advance
Claudio

---

### Post by drpaul on 2007-03-08
I have a similar situation. I think that the only way to have solved it is to have built a .deb package from the results of the compile. 

then you could use one of the package tools to install it and update the database.

I don't know how to do that and am not motivated enough to learn.

Sorry.

Paul


BTW: if you have done the make install then you have the new driver; it's just that the package database is out of sync with your system. Probably will cause a future problem when a Ubuntu update becomes available.

---

### Post by bracc0 on 2007-03-09
Thank you,
I'll look for a tutorial about creating .deb packages starting from a compiled program.
I am motivated enough by the absence of sounds.

Claudio

---

