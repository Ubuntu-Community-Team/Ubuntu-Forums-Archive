---
title: "LTSP server doesn't have client network card driver (Lucid Lynx)"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by Cenobite on 2010-09-01
Hi guys!

I'm setting up an LTSP server using Ubuntu 10.4 64bit, and PXE connecting with thin clients using Atheros cards. The ltsp environment is 32bit.

Unfortunately I get an error message with "No interfaces found! Aborting..." and a kernel panic early during PXE boot.

After an enormous amount of investigation, I've narrowed it down to (probably) being the fact that the ltsp chroot environment doesn't have the correct driver for my network card (I believe it's atl1c). The correct driver IS available in Ubuntu, though, as I can successfully boot the thin client from both 64bit and 32bit live CDs and bring up the network interface.

My main question is, how can I install the correct driver in the PXE environment?

Any help or advice is much appreciated!

**_Edit:_** May I please ask a mod to mark this as SOLVED? Thanks!

---

### Post by Cenobite on 2010-09-02
Nevermind, I got it working.

Basically I unpacked the initrd used by LTSP, manually copied the atl1c driver into the ramdisk environment, edited the /scripts/init-premount/udhcp script to force it to insmod the atl1c.ko file, repacked the initrd and it worked!

---

### Post by MaindotC on 2010-09-02
I saw this yesterday...wayyyyy over my head, but I'm so glad you got it figured out.  Maybe someday I'll be gosu enough to set up a ltsp environment.

---

