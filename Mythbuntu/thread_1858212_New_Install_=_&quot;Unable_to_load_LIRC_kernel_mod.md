---
title: "New Install = &quot;Unable to load LIRC kernel modules.&quot;"
date: 2011-10-11
forum: Mythbuntu
---

### Post by fullmoonguru on 2011-10-11
I have a new install of 10.04 with MythTV.  I load LIRC with the Mythbuntu LIRC Generator & get this error when it finishes:

Loading LIRC modules                                                  [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

It's a Harmony remote set up to act as an mce remote, with an mce  blaster.  Only the directional arrows work on the remote.  I have the  same combo on another partition working fine, & it was installed with the Mythbuntu Lirc Generator as well.  Even if I move my  hardware.conf, lircd.conf, & lircrc files to the new install, it's  the same.  There must be something going on with a newer LIRC package.   Anyone know what's going on?

---

### Post by ian dobson on 2011-10-12
Hi,

Have a look at your /etc/lirc/hardware.conf file and see what modules are being loaded and make sure there installing on the broken build.

Note you can just copy kernel modules from one kernal version to another.

Regards
Ian Dobson

---

### Post by fullmoonguru on 2011-10-13
Thanks.  I modprobed both installs & the new one is missing a ton of stuff.  I think I installed something that hosed the new install so I'm just going to reload.

---

