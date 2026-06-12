---
title: "Can't burn DVD's"
date: 2009-07-12
forum: Multimedia Software
---

### Post by megawicked on 2009-07-12
Hi!

I have problems burning DVD's on my Packard Bell Easynote B3600 laptop.
I have a NEC/ Slimtype ND6500A DVD/CD RW+- Drive. There is no problem burning DATA/Audio CD-s.

I can also read Video DVD's. When i insert an empty DVD, linux mounts it correctly. So there's no problem mounting DVD's. The Drive also recognizes the empty disc. 
I've tried different types of DVDr discs, like:
- HP DVD+R 16x 4.7 GB
- Memorex DVD+R 16x 4.7GB
Burning software i've tried:
- Brasero
- K3b
- CD/DVD workspace
- DeVeDe

The tail -f in the kernlog file gives this fault during a burnprocess:
tail -f /var/log/kern.log

Jul 12 17:00:36 wicked-laptop kernel: [ 7258.613781] ata2.00: status: { DRDY }
Jul 12 17:00:41 wicked-laptop kernel: [ 7263.653121] ata2: port is slow to respond, please be patient (Status 0xd0)
Jul 12 17:00:46 wicked-laptop kernel: [ 3229.011688] ata2: device not ready (errno=-16), forcing hardreset
Jul 12 17:00:46 wicked-laptop kernel: [ 3229.011696] ata2: soft resetting link
Jul 12 17:00:47 wicked-laptop kernel: [ 3229.503371] ata2.00: configured for UDMA/33
Jul 12 17:00:47 wicked-laptop kernel: [ 3229.503400] ata2: EH complete

Can anybody me please?

---

### Post by megawicked on 2009-07-13
Is there anybody who can maybe help me?

---

