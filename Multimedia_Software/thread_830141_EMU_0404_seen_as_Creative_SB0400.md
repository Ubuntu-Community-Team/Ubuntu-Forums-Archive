---
title: "EMU 0404 seen as Creative SB0400"
date: 2008-06-15
forum: Multimedia Software
---

### Post by jkeigs on 2008-06-15
Hi,I'm trying to get my EMU 0404 working in 8.04 i386 and when I look at my pci cards with lspci my emu is showing up as a Creative Labs SB0400 Audigy2.  I updated alsa to the most current version which didn't help, I think it may be a firmware issue but I couldn't figure out how to flash the card.  Has anyone had and solved this problem?  Any help would be appreciated.  Thanks

---

### Post by DwayneKong on 2008-11-18
My 0404 PCI does too:
02:05.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value

I was able to get my 0404 PCI to work on a new install of 8.04 i386 in only a couple of hours today (not 3 days like last time).

I just went to
[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)
 where you see  Current versions

get    * alsa-driver-1.0.18a
get    * alsa-lib-1.0.18
get    * alsa-utils-1.0.18
    * alsa-tools-1.0.18
get    * alsa-firmware-1.0.17
    * alsa-plugins-1.0.18
    * alsa-oss-1.0.17
    * pyalsa-1.0.17 

I added "get" because I didn't need the others (yet.)

Then do configure, make, make install as described in the middle of this page: 
[http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1)

Note he didn't do alsa-firmware, but I found that to be necessary, even tho it doesn't list the 0404.

There were errors along the way but Googling the error messages found all the solutions.

AND

I disabled the internal sound card in the BIOS; not sure if that was necessary.

---

