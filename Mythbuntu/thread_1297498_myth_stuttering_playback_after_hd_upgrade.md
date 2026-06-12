---
title: "myth stuttering playback after hd upgrade"
date: 2009-10-21
forum: Mythbuntu
---

### Post by kbrunsting on 2009-10-21
I swapped out a 80gb/500gb pair of hardrives about a month ago for a new WD 1.5TB drive.  I did a bit copy from the old drives to the single new one.  I'm running mythbuntu 8.04, on a m2npv-vm mobo, dual core 2ghz amd, 2gb ram, 8400gs video card and 2 hd-5500 tuner cards.  For the first week or two, no problems... then about 2 weeks ago the playback started stuttering.  It would pause for 1-10 seconds randomly during playback when watching a recording as it was recording or watching a pre-recorded show while another was recording.

I'm getting the IO errors
2009-10-21 20:43:36.057 TFW, Error: Write() -- IOBOUND begin cnt(9400) free(9235)
2009-10-21 20:43:38.420 RingBuf(/var/lib/mythtv/recordings/1031_20091021203000.mpg): Waited 4.0 seconds for data to become available...
2009-10-21 20:43:41.155 TFW, Error: Write() -- IOBOUND end

and I've been seeing these type of errors as well:
2009-10-21 20:45:49.624 [mpeg2video @ 0x7f7f1261a5b0]mb incr damaged
2009-10-21 20:45:49.625 [mpeg2video @ 0x7f7f1261a5b0]mb incr damaged
2009-10-21 20:45:49.625 [mpeg2video @ 0x7f7f1261a5b0]mb incr damaged
2009-10-21 20:45:49.626 [mpeg2video @ 0x7f7f1261a5b0]invalid mb type in B Frame at 0 5
2009-10-21 20:45:49.651 [mpeg2video @ 0x7f7f1261a5b0]slice mismatch
2009-10-21 20:45:49.654 [mpeg2video @ 0x7f7f1261a5b0]ac-tex damaged at 27 46
2009-10-21 20:45:49.655 [mpeg2video @ 0x7f7f1261a5b0]invalid mb type in B Frame at 13 47


2009-10-21 21:09:23.998 AFD Error: Unknown decoding error
2009-10-21 21:09:24.082 [mpeg2video @ 0x7fc5476865b0]warning: first frame is no keyframe
2009-10-21 21:09:24.381 [mpeg2video @ 0x7fc5476865b0]current_picture not initialized

Any ideas?

---

### Post by bsntech on 2009-10-22
Is this one of the WD Green drives?  I've seen problems before where the green drives - in order to be more "green" - will shut down for no apparent reason.

---

### Post by kbrunsting on 2009-10-22
yep, it is.

---

### Post by kbrunsting on 2009-10-22
strange that it would try to do that during recording when the hard drive gets hit pretty good.

---

