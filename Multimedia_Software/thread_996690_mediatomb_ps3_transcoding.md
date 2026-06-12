---
title: "mediatomb ps3 transcoding"
date: 2008-11-29
forum: Multimedia Software
---

### Post by huongalt on 2008-11-29
HI all

I am trying to get the video transcoding part of media tomb working. 
i think the structure of the xml file is correct as i can see by the terminal that it actually makes it as far as trying to envole the decoder, however I get the following error

[00000498] avcodec encoder error: cannot find encoder MPEG-2 Video
[00000415] stream_out_transcode stream out error: cannot find video encoder (module:ffmpeg fourcc:mp2v)
[00000415] stream_out_transcode stream out error: cannot create video chain
[00000435] main packetizer error: cannot create packetizer output (mp4v)
[00000498] avcodec encoder error: cannot find encoder MPEG-2 Video
[00000415] stream_out_transcode stream out error: cannot find video encoder (module:ffmpeg fourcc:mp2v)
[00000415] stream_out_transcode stream out error: cannot create video chain
[00000435] main packetizer error: cannot create packetizer output (mp4v)
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
[00000402] signals interface error: Caught Terminated signal, exiting...
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
[00000402] signals interface error: Caught Terminated signal, exiting...

This i assume means that the ffmpeg mpeg-2 decoder is not installed or not reachable,, 
can any one help or at least point me in the right direction

---

