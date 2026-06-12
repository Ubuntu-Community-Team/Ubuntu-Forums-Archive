---
title: "clonezilla not making a good 'clone' other suggestions"
date: 2011-04-24
forum: Mythbuntu
---

### Post by geekyhawkes on 2011-04-24
Hey guys;

so before 11.04 comes out (and due to some recent tweaking moving me ever closer to the 'perfect' setup) i want to backup my mythbuntu O/S drive (250gb WD).  I had previously been using clonezilla but i must be doing something wrong as I have never actually managed to get a clone onto my samsung 250gb HDD that i could simply boot from. 

In my head, if i get a good quality clone of the WD drive i should be able to just swap the SATA cables and be back up and running (in a RAID style).  Sadly, with clonezilla doing a device-device clone I end up with a non bootable clone (although the data seems to be on the drive).  I get a starting GRUB line then just a cursor flashing - this is different to my normal 10.10 startup when i dont see the starting GRUB line at all.

Can anyone recommend some software that will allow me to make a complete, bootable 1 for 1 clone of my current OS drive (preferable from a live CD i guess).

Thanks;

Andy

---

### Post by nickrout on 2011-04-24
did you make an image or did you make a clone?

did you clone the boot loader?

if you have a working system why update at all?

---

### Post by geekyhawkes on 2011-04-24
I asked it to clone device-device thinking i didnt want a image (and jsut a full drive backup).  I did answer yes to the boot loader option, but still no joy.

The reason to update is to get mythtv .24 with some of the extra (albeit minor) features.  It just seems i might as well do this at the same time as the paried OS release comes out.

---

### Post by nickrout on 2011-04-24
0.24 is available now in previous mythbuntu versions.

---

### Post by sammiev on 2011-04-24
I make a full image backup to my usb drive with clonezilla and have used it many of times in the last month to restore my HDD as I have been trying all the different versions of Linux. I have never tried to boot off my backup as I do verify my backups each time. GL :)

---

