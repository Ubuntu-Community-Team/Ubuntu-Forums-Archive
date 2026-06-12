---
title: "restore recordings after new install"
date: 2009-02-01
forum: Mythbuntu
---

### Post by itlarson on 2009-02-01
Because I had to replace a crashed motherboard, I need to re-install linux and mythtv.  How do I restore my recordings?- I am using the same hard drive, so I should still have all my data..

---

### Post by ian dobson on 2009-02-01
Hi,

Just because your motherboard died, it doesn't mean you need to reinstall linux. The kernel contains most of the drivers for all supported hardware. You might have problems with the graphic card if you change from ATI to NVidia or intel, but the system should boot without too many problems.

I'd recommend just swapping the motherboard and then fixing the small hardware problems that pop up.

Regards
Ian Dobson

---

### Post by itlarson on 2009-02-01
Tried to boot the suse based install which is on my hard drive, but it gets confused as to which disk it is booting off of halfway through the boot.  fstab modifications have no effect.  I found a possible solution using grub-install and mkintrid, but neither of these are available an the xubuntu disk I am using for rescue.  I am interested in trying mythbuntu anyway, so I'm just going ahead with a new install.  Further research has revealed that I can simply save a copy of the mythconverge file and restore from there.  Thanks anyway for the advice.

---

