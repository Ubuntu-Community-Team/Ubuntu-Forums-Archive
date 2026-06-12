---
title: "challenge question: need to access laptop without booting it locally"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by carbonrodney on 2009-07-01
ahoy there mon freres,

this one may well be a hard one. i have a broken laptop (lets call it old yeller), as in windows xp wont boot from it (and my beloved thesis is on the desktop).

the challenging part is this... it has no cd drive (i have an external usb one), no floppy and my bootable usb pen drive wont boot from it (neither does the cd drive). it does have a boot from ethernet port option though.

so what i want to do is connect up an ethernet cable to my other computer (let's call it jaunty) and through either linux or xp, mount the harddrive on jaunty and collect my thesis.

pleease halp...

---

### Post by Iowan on 2009-07-01
IF the laptop was set up to share it's hard drive (or at least the folder with your thesis), you may be able to mount the "share" via Samba.

---

### Post by MaindotC on 2009-07-01
Not gonna happen - OP is confusing what Network boot means.  If you have another machine just remove the hard drive from the laptop and plug it into the Jaunty machine.  When you boot into Jaunty you should see the hard drive and be able to browse its contents.

---

### Post by chili555 on 2009-07-01
> If you have another machine just remove the hard drive from the laptop and plug it into the Jaunty machineMight be challenging to plug a laptop drive into Jaunty if it's a desktop machine. However an external USB enclosure should work perfectly.

---

### Post by dmizer on 2009-07-01
> **strAlan said:**
> Not gonna happen - OP is confusing what Network boot means.  If you have another machine just remove the hard drive from the laptop and plug it into the Jaunty machine.  When you boot into Jaunty you should see the hard drive and be able to browse its contents.

No problem to do this. Just need to configure a thin client with local device support: [https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

Local device support: [https://wiki.ubuntu.com/EnableLTSP5LocalDevices](https://wiki.ubuntu.com/EnableLTSP5LocalDevices)

However, I agree that the most expedient and least baldness inducing method here would be to pull the drive and use a USB enclosure.

---

