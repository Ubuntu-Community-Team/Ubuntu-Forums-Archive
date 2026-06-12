---
title: "Mythbuntu install CD not booting after menu select"
date: 2011-03-21
forum: Mythbuntu
---

### Post by mikeg76 on 2011-03-21
Hello all,
Maybe someone can point me in the right direction here.  I recently inherited an unused IBM System X 7837-32u and thought I'd try turning it into a myth backend.  I burned the 10.10 64 bit iso and tried to boot to it.  Right after I select either 'install' or 'boot live cd' it will pause for about 30 seconds and then I will see green squares all over the screen.  It then hardlocks.  Any idea how to get around this?

rough specs:
Quad Xeon @2.27GHz
8GB RAM
80GB SATA drive (for testing naturally)
Dual Broadcom BCM5709C Nextreme 2 nics
Matrox G200eV graphics adapter

It does have a SAS controller, which the SATA drive is plugged into (downward compatible).  I was thinking it was some type of issue related to the SAS controller or the video adapter, but I'm unsure since I don't know the order of detection on Ubuntu.

I'm in the process of updating the system firmwares now, since I couldn't get it to boot to an Ubuntu live USB either...just in case it helps.

Can anyone point me in the right direction?  Thanks in advance.

--Mike

---

### Post by mikeg76 on 2011-03-22
Okay, after a firmware update of the system, I am now getting the following:

Kernel panic - not syncing: vfs: unable to mount root fs on root unknown-block(1,0)

I'm assuming now that it can't detect or configure either the cdrom or the hard drive to continue with the install.   Just how to proceed...

---

### Post by mikeg76 on 2011-03-22
Nevermind, 10.04 LTS seems to boot without an issue.  I suppose there's a bug somewhere, stopping 10.10 from booting on my specific system.  Oh well.

---

