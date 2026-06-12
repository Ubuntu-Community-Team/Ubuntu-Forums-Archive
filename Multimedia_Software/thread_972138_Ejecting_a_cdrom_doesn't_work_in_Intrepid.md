---
title: "Ejecting a cdrom doesn't work in Intrepid"
date: 2008-11-05
forum: Multimedia Software
---

### Post by peterdm on 2008-11-05
When I insert a cdrom it is correctly recognized: a cdrom icon is added to the desktop and and a content browser opens.
However, when I try to eject a cdrom by right-clicking on the item on the desktop and selecting "Eject", the tray briefly opens but immediately closes again before I get a chance to safely remove the disc.
Also when I unmount and then press the physical eject button on the front of the tray, it behaves like this.
This is rather inconvenient, is there a way to fix this?

For example, when I tried to copy a cd with Brasero: I insert the source, and select "Open with Brasero", which allows me to start copying. Then I get to the point where it asks me to insert a blank disc, the tray briefly opens and closes again, upon which nautilus gives me to "How do you want to open" dialog all over gain. I have to cancel it to get to the waiting Brasero dialog box, physically hit the eject button on the tray and insert a blank disc. When I close the tray, it gives me the "What do you want to do with this empty disc" dialog, which I cancel since meanwhile Brasero already started writing to the disc in the application behind it...

Please fix this!

Cheers,

Peter

---

### Post by DJ_Peng on 2008-11-05
You're not alone. Bug #[283316]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316") in udev (Ubuntu): “CD-ROM tray closes automatically after eject”. A fix has been released to intrepid-proposed.

---

### Post by ubuntu27 on 2008-11-05
Ohh What an annoying bug. Amyway, it has been fixed.

peterdm, Open SOftware Sources, and select "intrepid-proposed"

and then update the source

```
sudo apt-get update
```

and then update the software

```
sudo apt-get upgrade
```


For security reason, uncheck the intrepid-proposed again.

---

### Post by rfurman24 on 2008-11-06
This only fixed one of my two drives.

---

