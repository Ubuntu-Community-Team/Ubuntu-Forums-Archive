---
title: "Problem transcoding audio in VLC"
date: 2008-09-30
forum: Multimedia Software
---

### Post by insllvn on 2008-09-30
VLC is a veritable Swiss Army Knife of a media program. It is possible to use it to stream or save content off of a DVD (or other video disc). During this process, I am unable to encode in ANY non-free codec. I receive an error about ffmpeg being unable to find an MPEG encoder:

[00000331] a52 packetizer: A/52 channels:1 samplerate:48000 bitrate:96000
[00000348] ffmpeg encoder error: cannot find encoder MPEG AAC Audio
[00000297] stream_out_transcode private error: cannot find encoder ((null))
[00000297] stream_out_transcode private error: cannot create audio chain
[00000331] main packetizer error: cannot create packetizer output (a52 )

I am trying to make back ups of my DVD collection, and I would like the resultant files to play on my PS3. This means I must use MP3, MPEG or AAC codecs in MPEG or MP4 containers, otherwise I would be fine with using ogg vorbis. This issue seems to effect all compatible combinations of container and proprietary audio codec. I really just want to know if I am doing something wrong, or if this is a bug in the current vlc/ffmpeg packages. I would like to use VLC to do this if possible. Any assistance is greatly appreciated.

---

