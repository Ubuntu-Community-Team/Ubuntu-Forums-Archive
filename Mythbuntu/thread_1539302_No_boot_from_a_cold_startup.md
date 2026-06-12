---
title: "No boot from a cold startup"
date: 2010-07-26
forum: Mythbuntu
---

### Post by gnnash on 2010-07-26
Hello,

I recently installed Mythbuntu (with ubuntu 10.04), and am having issues starting up my computer.  I was also having these problems during installation, but didn't notice what I did to fix the problem.  Now, I think I have narrowed down the problem.

Whenever I start up my computer from a power-off state, I can't boot into Mythbuntu.  GRUB will load and select Mythbuntu, but the computer will stop with a flashing cursor.  If I start into Windows 7 first, then reboot into Mythbuntu, all is well.  The same is true for a restart from Mythbuntu.

I feel some sort of hardware isn't getting enumerated correctly.

I have a Core i3 530 running on a Biostar H55HD motherboard, using an NVidia Geforce 9800 GT.

Interestingly, when I first got the install to run, I had removed my Geforce, and enabled the integrated graphics.  I then noticed this problem again right after installing the card and related drivers.  This may be a coincidence with my cold/warm startups, but now is definitely related to whether I start into linux with a cold or warm restart.

---

### Post by ian dobson on 2010-07-26
Hi,

Maybe try booting with the option splash and quite disabled (edit boot menu in grub), this will display a long list of kernel messages and the last few are interesting.

It sounds as if some hardware in your box needs a firmware loaded (which windows is loading).

Regards
Ian Dobson

---

### Post by gnnash on 2010-07-26
Thanks for the reply.

Exactly what are the command line options for this?  Isn't there also a key I could hit while booting to accomplish the same thing?

---

### Post by ian dobson on 2010-07-26
Hi,

When the grub menu comes up, press e to edit an entry and just delete the quiet and splash options from the kernel command line.

If you don't see the grub menu, press the shift key and hold it down just before the bios ends and the linux loader process starts.

Regards
Ian Dobson

---

