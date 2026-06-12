---
title: "old radeon works with 9.04 64-bit not with 9.1 64-bit"
date: 2009-11-02
forum: Multimedia Software
---

### Post by ericrdrayer on 2009-11-02
I have, intel quad 6600, 9.04 64bit sda1, 9.1 64bit sda6.
I have forgotten the terminal command to find the info on my PCIe radeon card.I copied the xorg.conf file from my 9.04 installation (I have a fresh install with updates) but when I went to sda6:/etc/X11 I did not see a file called xorg.conf.

I think that if I could use the standard driver that was available in 9.04 it might work.

The symptom is:
bios loads.
grub select 9.1.
black screen... hang.
//////////
I can get to a command prompt but when I start x its back to the black screen.

I have an idea that there is some apt request that could get me back to the right driver.

---

### Post by ericrdrayer on 2009-11-02
update on machine information.
ati rv250 radeon 9000.
LCD samsung 2333SW monitor.

---

