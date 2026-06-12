---
title: "Mythtv - wake sleeping drives?"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by tommyp on 2007-06-29
I have been having some problems lately using Mythtv.  My recordings directory is on a separate drive which is  asleep when not in use (I seem to remember setting this in the BIOS).  

When starting to watch live TV, sometimes the command will seem to timeout after maybe 5 seconds, after which I try again and it works.  Also, several scheduled recordings have not happened lately.  Here has been the output of the backend logs:

> 2007-06-29 17:30:04.634 scheduler: Started recording: Ask This Old House "Replacing Shrubs; Attic Ventilation": channel 1014 on cardid 1, sourceid 1
2007-06-29 17:31:58.418 MPEGRec(/dev/video0) Error: error reading from: /dev/video0
			eno: Input/output error (5)
2007-06-29 17:33:42.955 MPEGRec(/dev/video0) Error: error reading from: /dev/video0
			eno: Input/output error (5)
2007-06-29 17:35:27.343 MPEGRec(/dev/video0) Error: error reading from: /dev/video0
			eno: Input/output error (5)
2007-06-29 17:37:12.194 MPEGRec(/dev/video0) Error: error reading from: /dev/video0
			eno: Input/output error (5)
and on. You get the idea.

I think this means that the drive is asleep when Mythtv tries to record.  Is there anyway to have Myth wake up the recordings directory prior to a scheduled recorded or maybe give the drive more time to get up to speed before myth timesout?

Thanks!

---

### Post by tommyp on 2007-06-30
bump

---

### Post by superm1 on 2007-07-01
Can you check dmesg?  Are there also errors there regarding this?  I'm reluctant to think its the drive wake up times, but more likely errors on the PCI bus (which would be seen by dmesg)

---

