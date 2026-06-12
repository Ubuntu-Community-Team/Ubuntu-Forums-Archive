---
title: "How to set GRUB root to (hdx,y) notation?"
date: 2011-01-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Irihapeti on 2011-01-03
I notice that grub in Natty has a line that looks like this:

set root='(/dev/sdb,msdos1)'

whereas in Lucid it reads:

set root='(hdx,y)'


It causes a few problems on my computer, because the device labels (sda, etc) aren't always assigned to the same drives. This issue isn't unique to me, by the way.

I know I can hand-edit /boot/grub/grub.cfg, but the moment there's a kernel update, it will go back to the default.

What file do I need to edit, and how specifically, so that it will default to the behaviour I want when there's an update?

---

### Post by efflandt on 2011-01-04
That was a problem for me with an earlier version of Kubuntu Natty installed to a USB hard drive, because the kernel parameters set in grub.cfg used that /dev/sdx instead of UUID and that grub did not even understand a UUID.  During installation on my laptop from iso on /dev/sdb, the Knatty USB hard drive ended up as /dev/sdc.  But then when attempting to boot the completed installation it was /dev/sdb.  Or when booted from my desktop, it was /dev/sdc during boot and /dev/sdg after boot (due to built-in USB memory reader). 

But as far as I know regular Ubuntu Natty has always use UUID, so that should not be an issue.  Although, I have been out of town for a week booting Lucid from a USB hard drive, so not sure if anything broke Natty grub lately.

I don't know why grub devices were changed, because (hd0) was always the drive booted from, regardless of how many drives were on that computer or which drive it ended up as after booting.  But /dev/hda, /dev/hdb, etc. is not a constant, so using those in grub.cfg seems to be a regression.

---

### Post by gacb on 2011-01-04
I discovered that if you mark grub-pc for re-installation in Synaptic from the partition or drive of choice, it moves the boot order back to where you want it.

---

### Post by psusi on 2011-01-04
Wow, that is borked.  /dev/sdb is not a valid grub device name.

---

