---
title: "Intrepid kernel: downgrade to UDMA/33 bug !"
date: 2009-04-06
forum: Mythbuntu
---

### Post by dibuntux on 2009-04-06
OK, I discovered why my myth box is slow.

There is a bug affecting all PATA disks in the new kernels. We have it in 8.10 and in 9.04.

If I run a dmesg I get a message that says that :

ata1.00: limited to UDMA/33 due to 40-wire cable

which of course is false, since the system has an 80 wire cable and BIOS is reporting UDMA/100 for the drives.

So transfer rate is 1/3 and HD playback is SLOW.

Anyone? TIA

---

### Post by joshoekstra on 2009-04-06
No problem here with a frontend using a PATA-disk with 80-wire cable, tried changing the cable?

---

### Post by august495 on 2009-04-07
Do you happen to have the Asus M2V motherboard? I swapped it out because of the exact same problem.I couldn't for the life of me find a fix for it.

---

### Post by dibuntux on 2009-04-07
No, the motherboard is an old MSI K7T Turbo, Via Apollo based. It is old, but perfectly functional. It worked with Windows, Mandriva & Ubuntu 7.10 - cables are ok.

I cannot just change motherboard, because I would have to trow away CPU, memory, video card and disks (besided the effort)....

---

