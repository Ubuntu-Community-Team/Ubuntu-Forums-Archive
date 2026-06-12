---
title: "trying to convert DVD to mpeg, lsdvd fails?"
date: 2010-01-08
forum: Multimedia Software
---

### Post by fINTiP on 2010-01-08
downloaded dvdrip from synaptic, got all dependencies, got the css library... now I've hit a problem I can't seem to solve. When I click the button to collect the table of contents (DVD's info from the DVD, it seems), it just flat out fails.

I get a warning dialog with this message:

"Job 'Read TOC (lsdvd)' failed with error message:
Error reading table of contents. Please check your DVD device settings in the Preferences and don't forget to put a DVD in the drive.
--------------------------------------------------------------------------------
"

The log looks like this:

Fri Jan  8 13:13:34 2010 Detected transcode version: 10104
Fri Jan  8 13:14:00 2010 Project file saved to '/home/kajo/dvdrip-data/unnamed.rip'
Fri Jan  8 13:14:00 2010 Project temporary dir '/home/kajo/dvdrip-data/unnamed/tmp' created
Fri Jan  8 13:14:00 2010 Project unnamed created
Fri Jan  8 13:14:06 2010 Start job 'Read TOC (lsdvd|tcprobe)'
Fri Jan  8 13:14:06 2010 Start job 'Read TOC (lsdvd)'
Fri Jan  8 13:14:06 2010 Executing command: execflow lsdvd -a -n -c -s -v -Op \/dev\/sr0 2>/dev/null && echo EXECFLOW_OK
Fri Jan  8 13:14:06 2010 Job 'Read TOC (lsdvd|tcprobe)' finished
Fri Jan  8 13:14:06 2010 Job 'Read TOC (lsdvd|tcprobe)' exited with error: Job 'Read TOC (lsdvd)' failed with error message:
Error reading table of contents. Please check your DVD device settings in the Preferences and don't forget to put a DVD in the drive.
--------------------------------------------------------------------------------
Fri Jan  8 13:14:06 2010 Job 'Read TOC (lsdvd)' finished

[B]---------------------------------------
-----------------------------------
--------------------------------------
-----------------------------------[/B]

running lsdvd by itself, trying to get a clue for where to go next, I receive this:

me@me-laptop:~$ lsdvd
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Can't seek to block 2581936
libdvdread: Can't seek to block 2581936
libdvdread: Invalid IFO for title 2 (VTS_02_0.IFO).
Can't open ifo 2!

What am I to make of this? Also, I assume I am going in the right direction to put the dvd onto my ipod touch 2G, yes?

A google brings up people with similar errors, and nothing helpful that I could find. :\

Thanks in advance.

K

---

### Post by stinger30au on 2010-01-08
the error says it cant read the disc

have u tried a different disc?

---

