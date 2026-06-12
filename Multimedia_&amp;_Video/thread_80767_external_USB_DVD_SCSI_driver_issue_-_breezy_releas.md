---
title: "external USB DVD SCSI driver issue - breezy release killed it?"
date: 2005-10-22
forum: Multimedia &amp; Video
---

### Post by mrguytx on 2005-10-22
I have been burning dvd's and cd's in Hoary and Breezy up until Breezy's final release using an app called "ToVid"...it was working great.

But now I seem to have an SCSI device/driver problem with the final Breezy release.

I can encode and prepare videos for burning but when the final stage comes to burn, I get this error:

```
Burning cue/bin image to /dev/scd0 with the following command:
cdrdao write --device /dev/scd0 --driver generic-mmc     --speed 12 "/tmp/Untitled_disc.xml.cue"
Supported SCSI transports for this platform:
Done. You should now have a working VCD or SVCD.
```

well, it never burns, because of this:
notice that the "Supported SCSI transports" is blank.
it never even hits the drive to write to it.

Is there some new external USB driver lib that needs to be installed?
SCSI driver?

It's just a standard USB 2.0 USB DVD writer and has always worked.
(and I just tested it on a wintel box and it's fine, not hardware related.)

Oh, and this is in /var/log/messages when I turn it off and back on:

Oct 22 22:15:50 localhost kernel: [4729571.631000] usb 3-2.2: USB disconnect, address 11
Oct 22 22:16:02 localhost kernel: [4729583.921000] usb 3-2.2: new full speed USB device using uhci_hcd and address 14
Oct 22 22:16:02 localhost kernel: [4729584.039000] scsi13 : SCSI emulation for USB Mass Storage devices
Oct 22 22:16:03 localhost usb.agent[16262]:      usb-storage: already loaded
Oct 22 22:16:07 localhost kernel: [4729589.044000]   Vendor: BENQ      Model: DVD DD DW1620     Rev: B7P9Oct 22 22:16:07 localhost kernel: [4729589.044000]   Type:   CD-ROM                             ANSI SCSI revision: 00
Oct 22 22:16:08 localhost kernel: [4729589.224000] sr1: scsi3-mmc drive: 62x/62x writer cd/rw xa/form2 cdda tray
Oct 22 22:16:08 localhost kernel: [4729589.229000] Attached scsi generic sg0 at scsi13, channel 0, id 0, lun 0,  type 5
Oct 22 22:16:08 localhost scsi.agent[16314]:      sr_mod: loaded sucessfully (for cdrom)
Oct 22 22:16:08 localhost scsi.agent[16314]:      sg: loaded sucessfully (for cdrom)


Thanks for any ideas.

[SOLVED]

This drive has suddenly become /dev/sr1 instead of /dev/scd0 like it used to be.
No idea why but that was the issue and is now resolved.
(except for totem, it still thinks the drive is at /dev/scd0 so until that's fixed I'll just use VLC).

---

