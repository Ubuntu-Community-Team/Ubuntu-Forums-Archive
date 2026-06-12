---
title: "Compac audio driver"
date: 2007-02-24
forum: Multimedia &amp; Video
---

### Post by elints on 2007-02-24
Where do I find an audio driver for an old Compaq Deskpro EN. circa 1999. The onboard ID is SB (i815) ADI SoundMax Integrated Audio 1.00A. The systems had Win 2000 and the sound worked. The systems are PII 266mhz with 196mb and xubuntu does ok on them (installed the first one last night)..

This case involves a small number of these units that a local shop wants to offer CHEAP for just web browsing, email, etc. I offered to put xubuntu on them for him just to help expand linux exposure in this area.

Any help would be appreciated.

---

### Post by tgalati4 on 2007-02-24
The SB designation makes me think that it is Sound Blaster compliant.  What is the output of the following?

lsmod
aplay -l


Also go into BIOS and turn off PnP operating system and temporarily turn off parallel port, usb port, serial port.  This frees up interrupts to maximize the chance of sound working.  Once working then you can turn them back on one by one.

Xubuntu should be good for those machines.  Bumping the memory to 256MB or greater would help as well.  Be sure to create a decent size swap file (500 MB to 2 GB, depending on how large the disk is).

Good luck

---

