---
title: "relocated pci ethernet card problem"
date: 2006-01-12
forum: Networking &amp; Wireless
---

### Post by macsimski on 2006-01-12
hello all,

i had to relocate my ethernet card to anothe pci slot to free space for a isa sound card. since then i have to manually enable my card in the kde control center. is there a way that this is done automatically?

specs: AMD k6-II@400 on asus p5a running breezy 5.10

and i get errors on activaton of my sound card.

read:[http://ubuntuforums.org/showthread.php?p=651212#post651212]("http://ubuntuforums.org/showthread.php?p=651212#post651212")

---

### Post by az on 2006-01-12
[QUOTE=macsimski]hello all,

i had to relocate my ethernet card to anothe pci slot to free space for a isa sound card. since then i have to manually enable my card in the kde control center. is there a way that this is done automatically?

specs: AMD k6-II@400 on asus p5a running breezy 5.10

and i get errors on activaton of my sound card.

read:[http://ubuntuforums.org/showthread.php?p=651212#post651212]("http://ubuntuforums.org/showthread.php?p=651212#post651212")[/QUOTE]

If you remove your sound card and keep the ethernet card in the current slot, your problem may go away.  If this is the case, it is because the isa card is trying to use a ressource (port or irq) that is conflicting with your ethernet (or another) piece of hardware.  

Can you find out what irq and port your card is trying to use and allocate it to the isa bus in your bios?  That should solve the problem(s).

---

### Post by macsimski on 2006-01-13
[QUOTE=azz]If you remove your sound card and keep the ethernet card in the current slot, your problem may go away.  If this is the case, it is because the isa card is trying to use a ressource (port or irq) that is conflicting with your ethernet (or another) piece of hardware.  

Can you find out what irq and port your card is trying to use and allocate it to the isa bus in your bios?  That should solve the problem(s).[/QUOTE]


i would love to, but i have no idea how. during boot there is a list briefly visible. but it goes away as soon as grub kicks in. only 3 seconds. what i can see is that one card is using irq 14/15. yes, two irq's? 

after this there still is the problem of the ethernet card. I'm coming from the macintosh side, and i'm not aware if irq's are coupled to pci card positions or not. relocating cards in a mac does'nt require configuration.



allocating a irq in the bios is simple though.

---

### Post by az on 2006-01-13
[QUOTE=macsimski
after this there still is the problem of the ethernet card. I'm coming from the macintosh side, and i'm not aware if irq's are coupled to pci card positions or not. relocating cards in a mac does'nt require configuration.

[/QUOTE]

It is not a question of architecture, but technology.  ISA cards are different from pci cards.  The kernel can detect and configure pci cards.  It cannot with ISA cards.  YOu sometimes need to do it by hand - some isa hardware has jumpers for this, sometimes you do it in bios.

I think it is your ISA card that is causing trouble for your pci card. The isa card is the new addition, right?

I cannot tell you how to configure your bios/cmos, since it is different from each machine.

Usually, you need to press a key as you are booting...

---

