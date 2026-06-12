---
title: "AUDIO CD, MP3, DVD read error."
date: 2007-09-06
forum: Multimedia &amp; Video
---

### Post by skdd on 2007-09-06
SO LATELY I'VE BEEN HAVEN TROUBLES WITH MY DRIVE READING SOME DISKS THAT I POP INTO IT.  IT READS THE DISK AND GIVES THIS MESSAGE TELLING ME THAT THE DISK DOES NOT HAVE ANYTHING INSIDE AND TREATS IT LIKE IS IS A BLANK DISK THAT I JUST INSERTED.  I DUNNO IF IT'S MY CD DRIVE OR JUST THE SOFTWARE'S FAULT... HOW CAN I CHECK THAT???  BUT THIS HAVE BEEN HAPENING FOR NOT VERY LONG TIME BECASUE I EVEN GOT TO PLAY DVDS AND AUDIO CDS (THAT I USUALLY  BURN). 

this is my dmesg when i inser a new disk... i hope the info helps...

dmesg |tail
[17184387.284000] hdc: error code: 0x70  sense_key: 0x04  asc: 0x09  ascq: 0x90
[17184387.304000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[17184387.304000] hdc: packet command error: error=0x40 { LastFailedSense=0x04 }[17184387.304000] ide: failed opcode was: unknown
[17184387.304000] hdc: error code: 0x70  sense_key: 0x04  asc: 0x09  ascq: 0x90
[17184387.308000] cdrom: This disc doesn't have any tracks I recognize!
[17184387.316000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[17184387.316000] hdc: packet command error: error=0x40 { LastFailedSense=0x04 }[17184387.316000] ide: failed opcode was: unknown
[17184387.320000] hdc: error code: 0x70  sense_key: 0x04  asc: 0x09  ascq: 0x90

PS: I already downloaded the gstreamer packages... and it worked fine... as i said this problem has happened lately... and i really dunno waht to do...

---

