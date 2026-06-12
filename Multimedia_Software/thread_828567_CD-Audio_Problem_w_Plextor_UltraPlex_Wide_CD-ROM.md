---
title: "CD-Audio Problem w/ Plextor UltraPlex Wide CD-ROM"
date: 2008-06-13
forum: Multimedia Software
---

### Post by Michael_B on 2008-06-13
Hello:

I've recently installed Ubuntu 8.04 on an Intel P4-based system possessing an Adaptec 29160 SCSI adapter.  Attached to this adapter are a pair of internal SCSI hard disks, as well as a Plextor UltraPlex Wide SCSI CD-ROM (reported as PX-40TW by dmesg and /proc/scsi/scsi; output below.)  Cables and termination are fine.

Also attached to this computer is an external (USB) Plextor PX-810 UF DVD+RW burner.

The UltraPlex seems to work fine for reading *data* CD-ROMs with Ubuntu / Linux (in fact it was from this device that I installed Ubuntu 8.04 from the downloaded .iso.)  However, CD-audio, either played directly from, or ripped using this CD-ROM is completely garbled.  I have tried making a copy of a CD-ROM (using both k3b and Brasero) and the resultant (copy) CD contains only high-pitched squealing, chirps, and other noise.  Interestingly, on the copy (a) there are discrete tracks, and (b) the CD-TEXT information seems to have been read OK.

Additional information:

- If I try to simply *play* (not copy) an audio CD using this drive, I get the same result--  high pitched squeals and chirping sounds.  It seems like there is a fundamental problem in reading CD-audio from this drive with this version of Ubuntu / Linux.

- Audio played, ripped, or burned using my other drive, the PX-810UF, works perfectly, so it doesn't seem like a problem with the actual audio playing / extraction software I've tried.

- The UltraPlex Wide drive works fine for all data and audio (playing, extracting / ripping) tasks under Windows XP.  So the hardware is not faulty, nor is there a problem with the SCSI chain (termination, etc.) 

- This problem also exists with this same machine/setup under Fedora 9 (fresh install from the DVD .iso.)  In fact it was this problem that let me to give Ubuntu a try for the first time.  I'm quite impressed so far!

- My Ubuntu installation is 8.04 Desktop, with updated packages via apt-get update and  apt-get upgrade.    Again, this was installed with the UltraPlex Wide, so the problem seems to be audio-only.

I am inclined to think there might be an issue with the kernel, the SCSI driver, or some combination of the two.

I am curious if anyone else has observed behavior similar to this, and any pointers, suggestions, or fixes would be most appreciated!  Please let me know what additional system information might be useful and I'll be happy to post it.  

Best regards,
-Michael

Linux mdb 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux

[   67.725335] scsi3 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   67.725337]         <Adaptec 29160 Ultra160 SCSI adapter>

Host: scsi3 Channel: 00 Id: 06 Lun: 00
  Vendor: PLEXTOR  Model: CD-ROM PX-40TW   Rev: 1.05
  Type:   CD-ROM                           ANSI  SCSI revision: 02

---

