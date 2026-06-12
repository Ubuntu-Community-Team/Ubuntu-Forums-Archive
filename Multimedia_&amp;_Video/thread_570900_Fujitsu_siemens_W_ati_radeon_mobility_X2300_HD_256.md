---
title: "Fujitsu siemens W/ ati radeon mobility X2300 HD 256mb"
date: 2007-10-08
forum: Multimedia &amp; Video
---

### Post by dgrafix on 2007-10-08
New PC:Fujitsu siemens W/ ati radeon mobility X2300 HD 256mb

Live Cd did not work but managed to get the text installer to work.

X server will not start I have tried vesa and limiting it to low resolutions and still not able to get the X server started. How can i tell if its on a different PCI location? And what do i need for the most bog standard of vesa settings, so i can at least get in to the system?

---

### Post by ddrichardson on 2007-10-09
Try booting with the noapic option added to the kernel line in grub, or from the live cd added with F6 at the main menu first

---

### Post by BigBishop on 2007-10-09
I am having the same problem with my new board and it is making me very mad.  From what i can gather it is because of the BIOS and the chipset being used.  I have seen a few diffrent solutions but turning off the ACPI is the one i saw the most.  Bad part is I'm not new to Linux but im far from an expert and dont know what im doing when editing the GRUB file.  Guess i will have to figure it out tonight when i get home.

---

### Post by dgrafix on 2007-11-12
Get Gutsy works great.

---

