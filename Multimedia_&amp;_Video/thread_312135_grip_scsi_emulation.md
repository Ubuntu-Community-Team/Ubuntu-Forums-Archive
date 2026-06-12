---
title: "grip scsi emulation"
date: 2006-12-03
forum: Multimedia &amp; Video
---

### Post by logos34 on 2006-12-03
Can anyone please advise me on whether to enable scsi emulation for Grip?  It's the best linux replacement for Exact Audio Copy I can come up with, but slow as molasses without the latters' degree of precision.  Grip help (section 3.3 'Increasing Ripping Performance') reads:

'If you are using an IDE CDrom drive, using SCSI emulation can
give a significant performance increase. Apparently, dma is not used
by the IDE driver (at least in 2.4 kernels). To enable SCSI
emulation, add "hdx=ide-scsi" (where the "x" in "hdx" is is replaced 
with the appropriate letter for your CDRom device) to end of the
"kernel" line in /etc/grub.conf (if you are using grub), or as a
line after "root=/dev/something" in /etc/lilo.conf (if you are using
lilo).'

Firstly, dma is already enabled for my cdrom (/dev/hdc), so is it already operating at full speed?  If not, what if I enable scsi emulation in the Grub config file (/boot/grub/menu.lst) by editing the 'kernel' line to read:  

/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash hdc=ide-scsi

Is that how it should look?  If the worst happens and I can't reboot the system, can I use sudo nano from the console to take out the edit?

I just don't want to screw up and be forced to reinstall Edgy yet another time!

---

