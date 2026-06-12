---
title: "Error when converting fbs file to mpg file"
date: 2009-09-11
forum: Multimedia Software
---

### Post by nagalenoj on 2009-09-11
Dear friends,
   I've recorded some remote desktop by using Ultravnc as server and RFBproxy as client. RFBproxy has given me a fbs file for each session. 
   When I searched about converting this to movie format, I've found the following command and I installed it.

      [I]./rfbproxy --export ~/Desktop/q3.fbs | ppmtoy4m | yuvscaler -n ntsc -O DVD | mpeg2enc -f 8 -o video_test.mpg

   [/I]I'm getting this following error when executing this command.

   INFO: [ppmtoy4m] Command-line Parameters:
   INFO: [ppmtoy4m]              framerate:  30000:1001
   INFO: [ppmtoy4m]     pixel aspect ratio:  1:1
   INFO: [ppmtoy4m]          pixel packing:  RGB
   INFO: [ppmtoy4m]              interlace:  none/progressive
   INFO: [ppmtoy4m]         starting frame:  0
   INFO: [ppmtoy4m]            # of frames:  all, until input exhausted
   INFO: [ppmtoy4m]     chroma subsampling:  4:4:4 (no subsampling)
   INFO: [yuvscaler] yuvscaler 1.8.0 (15-02-2004) is a general scaling utility for yuv frames
   INFO: [yuvscaler] (C) 2001-2004 Xavier Biquard <xbiquard@free.fr>, yuvscaler -h for help, or man yuvscaler
   INFO: [mpeg2enc] SETTING EXTENDED MMX for MOTION!
   INFO: [mpeg2enc] SETTING SSE and MMX for TRANSFORM!
   INFO: [mpeg2enc] SETTING EXTENDED MMX for PREDICTION!
   INFO: [ppmtoy4m] Output Stream parameters:
**ERROR: [yuvscaler] Could'nt read YUV4MPEG header!
**ERROR: [mpeg2enc] Could not read YUV4MPEG2 header: system error (failed read/write)!
   INFO: [ppmtoy4m]     frame size:  1024x768 pixels (2359296 bytes)
   INFO: [ppmtoy4m]         chroma:  4:4:4 (no subsampling)
   INFO: [ppmtoy4m]     frame rate:  30000/1001 fps (~29.970030)
   INFO: [ppmtoy4m]      interlace:  none/progressive
   INFO: [ppmtoy4m]   sample aspect ratio:  1:1

I don't what is the problem and where is the mistake. _Help me to solve this error._ 

Whether the above command will solve my requirement. I've found it in this site, [http://wiki.debconf.org/wiki/DebConf5VideoVNC](http://wiki.debconf.org/wiki/DebConf5VideoVNC)

_Is there any other way?_

---

