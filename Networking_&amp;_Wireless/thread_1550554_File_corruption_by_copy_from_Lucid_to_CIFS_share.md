---
title: "File corruption by copy from Lucid to CIFS share"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by waldgeist_di on 2010-08-11
Source System: 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux on a Dell Precision T5400

Destination System: Win 2003 Server R2 on a Dell PowerEdge 2900

There are a number of shares on the destination system; for the purposes of this thread I used D$ and F$ (corresponding to those partitions). These shares are mounted permanently via CIFS (entries in fstab) on the source system.

Today I copied an ISO image of some 3.5 GB from source (S) to destination (D). md5sum on S gave a different checksum for the source ISO than that calculated by HashCheck Shell Extension for the destination ISO. I know some would argue that I shoud use the same md5sum programm for both images.

To circumvent that I 7zipped the ISO, verified it's integrity and copied that archive from S to D. Verification of the acrchive by the Win version of 7z failed.

To see if it's a protocol problem I copied both ISO and archive of ISO to another D this time using sshfs (it's an Ubuntu server). Flawless copies.

Then I copied both files to another Win-based server on the same network. Flawless copies.

Mystified, I checked the partition's file system integrity (NTFS) where the errors occured. Minor inconsistencies (no errors according to chkdsk). So I copied both files again, once to another partition (D:) of the original D, once to that partition causing the error in the first place (F:).

(D:): archive corrupt, checksum okay
(F:): this time around both okay.

What the hell can I do to nail down the problem?! I don't even know whether it's a problem of the source system or the destination ...

Any suggestions are greatly appreciated!

***edit***
All copy trials where done with Krusader on a Lucid Lynx Ubuntu box.

***edit***
Also tried with MC and a simple cp on the command line. I get the suspicion it might be the destination system (i.e. the Windows Server) since I don't get problems while copying to other systems irrespective of the OS.

---

### Post by waldgeist_di on 2010-08-12
No ideas?

---

