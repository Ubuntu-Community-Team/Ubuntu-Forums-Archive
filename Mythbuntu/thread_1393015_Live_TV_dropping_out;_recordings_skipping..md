---
title: "Live TV dropping out; recordings skipping."
date: 2010-01-28
forum: Mythbuntu
---

### Post by sceo on 2010-01-28
Here's what I'm seeing:

**Seeing this in mythbackend log:**
TFW, Error: Write() -- IOBOUND begin remaining(6633) free(0) size(2097152) cnt(1)
TFW, Error: Write() -- IOBOUND end

**Seeing this in console messages:**
pegasus kernel: [ 2407.965324] ivtv0: All encoder MPG stream buffers are full. Dropping data.
pegasus kernel: [ 2407.965332] ivtv0: Cause: the application is not reading fast enough.

**Seeing this in the frontend log:**
NVP(0): prebuffering pause
WriteAudio: buffer underrun
RingBuf(/recordings/1054_20100128204228.mpg): Waited 1.0 seconds for data to become available...
Checking to see if there's a new livetv program to switch to..
NVP(0): Prebuffer wait timed out 10 times.


...so I must have some kind of performance problem?  Everything was working fine until I moved the mythbox upstairs.  The box itself is laying on it's side, and it's contained - so it might be overall hotter than normal.  I also needed to do wireless instead of wired network connection; but that's all that's changed.

I also had some MySQL tables that needed to be repaired, so I repaired and optimized all my tables (particularly "credits" had a problem).  It seems to help, but I'm still seeing these kinds of errors.  What might they indicate - bad disk?

---

