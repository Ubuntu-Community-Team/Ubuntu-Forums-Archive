---
title: "QDVDuthor error"
date: 2006-10-26
forum: Multimedia &amp; Video
---

### Post by mibadt on 2006-10-26
Hi,
I try to make an ISO file (for DVD burning) from an MPG file using QDVDAuthor.
The script (created by DVDAuthor) fails in its first line with an error message.

PLease advise !

TIA

Michael Badt
--------copy of script line+ its outcome-------------
/usr/bin/jpegtopnm "/home/miki/DVD_tmp/Bled/Main Menu VMGM/background.jpg" |/usr/bin/ppmtoy4m -n 1 -F25:1 -A59:54 -I t -L |/usr/bin/mpeg2enc -f 8 -n p -o "/home/miki/DVD_tmp/Bled/Main Menu VMGM/menu.m2v"
   INFO: [ppmtoy4m] Command-line Parameters:
   INFO: [ppmtoy4m]              framerate:  25:1
   INFO: [ppmtoy4m]     pixel aspect ratio:  59:54
   INFO: [ppmtoy4m]          pixel packing:  RGB
   INFO: [ppmtoy4m]              interlace:  top-field-first (interleaved PPM input)
   INFO: [ppmtoy4m]         starting frame:  0
   INFO: [ppmtoy4m]            # of frames:  1, or until input exhausted
   INFO: [ppmtoy4m]     chroma subsampling:  4:4:4 (no subsampling)
   INFO: [mpeg2enc] SETTING EXTENDED MMX for MOTION!
   INFO: [mpeg2enc] SETTING SSE and MMX for TRANSFORM!
   INFO: [mpeg2enc] SETTING EXTENDED MMX for PREDICTION!
jpegtopnm: WRITING PPM FILE
   INFO: [ppmtoy4m] Output Stream parameters:
   INFO: [ppmtoy4m]     frame size:  720x576 pixels (1244160 bytes)
   INFO: [ppmtoy4m]         chroma:  4:4:4 (no subsampling)
   INFO: [ppmtoy4m]     frame rate:  25/1 fps (~25.000000)
   INFO: [ppmtoy4m]      interlace:  top-field-first
   INFO: [ppmtoy4m]   sample aspect ratio:  59:54
**ERROR: [mpeg2enc] Could not read YUV4MPEG2 header: stream requires unsupported features!

---

