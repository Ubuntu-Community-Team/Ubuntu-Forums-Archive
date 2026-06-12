---
title: "CD Player software jam"
date: 2011-01-16
forum: Multimedia Software
---

### Post by owlcroft on 2011-01-16
The title is not very descriptive, but I don't know how else to refer to it.

Ubuntu 10.10, fresh install. LG optical drive, scsi; lsscsi shows:
```
[4:0:0:0]    cd/dvd  HL-DT-ST DVDRAM GSA-4163B A102  /dev/sr0
```
The default action for an audio CD is "Do Nothing."  Normally, everything works fine.

Now: I use the "cdtools" package to open, close, play, and stop some audio CDs.  It works fine, disk after disk, for as many uses as I care to do.  Some time later I go to use the drive again and it will not work.  If, for example, I try the cdtools command "cdclose", I get back:
```
cdclose: unexpected end track 214 in TOC
cdclose: ioctl cdromclose: Input/output error
```  The track number varies from case to case, but otherwise the message is the same.  So far, nothing I have tried helps save a full reboot, which always restores full functionality.

It looks as if something somewhere is "remembering" a disk that is no longer present, and so "jams" the operation; but I am clutching at straws here.

Any ideas?  Reboot gets tedious.

(I am using the cdtools to catalogue my audio-CD collection: the "cdown" command fetches the disk info from freedb and I feed it to a file; so I am loading disk after disk with this sequence: *cdclose; cdstop; cdown; cdeject*.  I can do that for two dozen or more disks in a row with no problem.  It doesn't matter if, when I am through, I close the drive with "cdclose" or by pressing the button on the drive: later on, it is "jammed".)

---

### Post by owlcroft on 2011-01-19
(bump)

The curious thing is that for some while after use of the cdtools software, the drive continues to respond normally.  Then, some hours later, it fails with the error message type as shown earlier.  I am unable to correlate the change with the use of any other software: I certainly have used nothing referencing the drive, except the actual **cdeject** and **cdclose** commands to test if it still works.  It does, it does later, it does later yet, then it doesn't.

What can be clobbering things?

---

### Post by owlcroft on 2011-01-26
(bump again - not getting a lot of help here)

The source code for the cdtools app is here:

[http://cdtool.sourcearchive.com/documentation/2.1.8-release-2/hardware_8c-source.html](http://cdtool.sourcearchive.com/documentation/2.1.8-release-2/hardware_8c-source.html)

Maybe it can help someone who understands these things to figure out what is happening.  The key area seems to be:
```
    /* check bounds of tracks */
    if (hw->tochdr.cdth_trk1 > MAX_TRACKS) {
        errormsg("%P: unexpected end track %d in TOC", hw->tochdr.cdth_trk1);
        hw->tochdr.cdth_trk1 = MAX_TRACKS;
    }
```

---

