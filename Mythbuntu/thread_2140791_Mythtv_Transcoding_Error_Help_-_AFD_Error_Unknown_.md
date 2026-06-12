---
title: "Mythtv Transcoding Error Help - AFD Error: Unknown audio decoding error"
date: 2013-04-30
forum: Mythbuntu
---

### Post by grunge09 on 2013-04-30
I can record and play tv stuff fine, I have trnascoding setup using RTJpeg, so I made a test decoder with MPEG and STILL get the same "AFD Error: Unknown audio decoding error"

what is this and how do I fix this?

---

### Post by klc5555 on 2013-05-02
This type of error often implies that the processing program --probably ffmpeg, possibly mencoder-- lacks access to a codec or library required to process the audio portion of the file. You could try transcoding a test file manually with mythtranscode + ffmpeg/mencoder to see where the process bombs out, as per here:  [http://www.mythtv.org/wiki/MythTV-HOWTO_-_0.26#mythtranscode_example](http://www.mythtv.org/wiki/MythTV-HOWTO_-_0.26#mythtranscode_example) ...and then supply the missing codec (or possibly an updated mencoder/ffmpeg) as necessary.

There is also no shortage of specialized transcoding scripts in existence in the wild, which can be run as user jobs, modified, or automated as necessary. One such, intended for PVR-150 (250, 500) MPEG2 output to H.264 is here: [http://mythtv-scripts.googlecode.com/svn-history/r10/trunk/test/mythtv-transcode-h264.sh](http://mythtv-scripts.googlecode.com/svn-history/r10/trunk/test/mythtv-transcode-h264.sh) (Note that this particular script requires mencoder and ogg-vorbis tools)

---

