---
title: "Unable to rip an audio CD"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by etienne.sandre on 2008-03-10
Dear all,

I am unable to rip an audio CD.
When I insert an audio CD, it is correctly recognized by konqueror or k3b, and I can have the song names list. If I try to rip the CD, it fails (with an unhelpful error message, such as "error reading from device")
After this, it is impossible to read anything from the CD drive, even if I eject and insert a data CD which worked before. 

At this point, cd paranoia -vsQ gives :
Checking /dev/cdrom for cdrom...
        Testing /dev/cdrom for SCSI/MMC interface
                SG_IO device: /dev/hda
                Drive is neither a CDROM nor a WORM device

        Testing /dev/cdrom for cooked ioctl() interface
                Device /dev/hda is not a CDROM


mount /dev/cdrom with a data cd blocks forever, generating syslog messages:
Mar 10 09:37:20 galinette kernel: [17920.353222] hda: status timeout: status=0x80 { Busy }
Mar 10 09:37:20 galinette kernel: [17920.353227] ide: failed opcode was: unknown
Mar 10 09:37:20 galinette kernel: [17920.353230] hda: drive not ready for command

I have to reboot the system for using the cdrom.

The cdrom is working well if I do not try reading audio cd's, and I can even burn.

I am using an updated ubuntu v7 AMD64 with the default kernel vmlinuz-2.6.22-14-generic, and I did not hack anything

Ripping CD's works well under winXP.

This looks bad and I've not found a similar issue by googling...

Thanks if you can help!

Etienne

---

