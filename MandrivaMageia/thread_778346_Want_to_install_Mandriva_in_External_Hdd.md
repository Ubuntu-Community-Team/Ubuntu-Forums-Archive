---
title: "Want to install Mandriva in External Hdd"
date: 2008-05-02
forum: Mandriva/Mageia
---

### Post by Mohamed Fahim on 2008-05-02
Hi Guys,
  I have windows xp and Ubuntu Hardy Heron on my internal Hard disk now i have one external Hard disk i want to install mandriva spring init but without disturbing my grub which already have in my internal hard disk how to do it let me know guys

---

### Post by Vorian Grey on 2008-05-02
> **Mohamed Fahim said:**
> Hi Guys,
  I have windows xp and Ubuntu Hardy Heron on my internal Hard disk now i have one external Hard disk i want to install mandriva spring init but without disturbing my grub which already have in my internal hard disk how to do it let me know guys
Do a regular install and when you get to the grub part, don't install to MBR but to first hard drive (I hope that's right). Then restart to Ubuntu and go to /boot/grub/menu.lst on the partition you installed MDV and copy the info and then open Ubuntu's /boot/grub/menu.lst in gedit as sudo and paste the info there. When you restart you can then choose Ubuntu or Mandriva.

At least that's the way I do it. There may be easier ways.

---

### Post by wolfen69 on 2008-05-02
my advice would be to unplug all other drives except the usb drive. that way it has no choice but to put grub on the external drive. then at bootup, you can choose which drive to boot to. im assuming this is a regular drive and not flash. but then again, i could be wrong about all of this.(ive never installed to a extenal hd) at least i know unplugging all other drives first will prevent a mishap. maybe adam will shed some light on this.

---

