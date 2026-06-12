---
title: "lenovo 3000 n100 sound in gutsy 32 bit"
date: 2008-01-08
forum: Multimedia &amp; Video
---

### Post by stephenjbarr on 2008-01-08
Hello,

I have a lenovo 3000 n100. I had a 32 bit version of gutsy installed on it, and sound was working fine. I even had the patched-alsa installed to fix the headphone not-muting bug. I installed 64 bit gutsy, decided against it, and reinstalled 32 bit gutsy. I have everything working perfectly how I want it, except sound. I have tried applying every fix I can find with no success. What fix can I apply that works? I think I see what the problem can be from the following commands, but I don't know how to fix it from here. Perhaps I tried to apply too many fixes and broke sound even more.

Thanks for the help, -stephen

Here is some useful output:
steve@neutron:~$ sudo modprobe snd-hda-intel
[sudo] password for steve:
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
steve@neutron:~$ 

from dmesg:
[  299.956000] snd_hda_intel: disagrees about version of symbol snd_dma_free_pages
[  299.956000] snd_hda_intel: Unknown symbol snd_dma_free_pages
[  299.956000] snd_hda_intel: disagrees about version of symbol snd_dma_alloc_pages
[  299.956000] snd_hda_intel: Unknown symbol snd_dma_alloc_pages
steve@neutron:~$

---

