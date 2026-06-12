---
title: "mythbuntu 10.10 serious errors were found while checking the disk drive"
date: 2011-02-04
forum: Mythbuntu
---

### Post by Morgennebel on 2011-02-04
Hi There,


my mythbuntu 10.04 64 bit LTS system worked like a charm. But I had to upgrade to mythTV 0.24 with daily repos and to mythbuntu 10.10.

Now, as back in old times I get after every 2nd or 3rd reboot the following error:

    Serious errors were found while checking the disk drive

If I choose Manual Recover, call "mount -a" in the root shell all drives are mounted correctly and the system boots as expected.

I am using grub2. /etc/fstab is based on UUIDs:

# /var was on /dev/sda7 during installation
UUID=54ba6a64-b42c-405d-ae73-d0ed2f28bc1d /var            xfs     defaults  0       2
# swap was on /dev/sda2 during installation
UUID=f6672a4d-22b8-4a4f-b1ed-edaccc175362 none            swap    sw  0       0
# livetv
UUID=ea576c50-ba60-4342-8a39-739dc0f331f5       /var/lib/mythtv/livetv/1500GB xfs     defaults,allocsize=512m 0       2
# livetv 2
UUID=974d9906-493c-4bb1-944b-662835261c1c       /var/lib/mythtv/livetv/750GB xfs     defaults,allocsize=512m 0       2
# recordings
UUID=3f93c1aa-5826-4b20-8aef-4c51fbee3f61       /var/lib/mythtv/recordings/1500GB       xfs     defaults,allocsize=512m 0       2
# recordings 2
UUID=94533cab-c6d3-4b2d-a6d7-eede09ad3cb2       /var/lib/mythtv/recordings/750GB xfs     defaults,allocsize=512m 0       2
# music
UUID=a0f62daf-53a1-4937-a8d4-d42653f3f296       /var/lib/mythtv/music   xfs defaults        0       2

Filesystem is xfs. 

I have no idea why the system does mount the partitions during boot phase.

Any pointers/links are welcome.

Thanks, -MN

---

### Post by nickrout on 2011-02-04
boot from a live cd or flash drive and run xfs_repair on the drive.

---

### Post by Morgennebel on 2011-02-21
> **nickrout said:**
> boot from a live cd or flash drive and run xfs_repair on the drive.

Apologies if my error description was not correct - but the filesystem reports no errors.

Again:

  a) Turn on the system

  b) OS reports serious fs errors on either hard disk 2 and 3
      disk 1 = Intel SSD, operating system, all filesystems xfs
      disk 2 = SATA recordings 1, all filesystems xfs
      disk 3 = SATA recordings 2, all filesystems xfs

  c) Drops me to root shell

  d) forced fsck on disk 2 or 3 do not report any errors

  e) mount -a works without any errors and system continues to boot

Just to be sure I migrated all partitions on disk2 and disk3 to ext4 - and experience
the same error every 4-8 reboots!

I honestly do not believe that this is a filesystem bug (xfs or ext4 are quite - different).

For me it looks like the systems boots too quick (Quad Core with SSD) so that partition structures/and kernel structures are not "ready". This might be caused with the ureadahead solution which accelerates the boot time even further - with 10.04 LTS I had less errors and none with 9.10. Just guessing to be honest...

Is there a way to disable ureadahead and slow down the boot procedure...?

Thanks, -MN

I honestly do not believe as well that this is a hardware error - as the version of the operating system creates a visible difference.

---

