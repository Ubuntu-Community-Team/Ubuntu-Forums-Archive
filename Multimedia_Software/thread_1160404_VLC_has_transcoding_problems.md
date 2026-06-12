---
title: "VLC has transcoding problems"
date: 2009-05-15
forum: Multimedia Software
---

### Post by soltanis on 2009-05-15
VLC works perfectly when outputting video/audio streams of almost any file format. However, its transcoding feature, where it streams a video/audio format into a different format, is broken consistently, and I don't understand why.

The error I get looks like this:

```

[00000552] mux_ogg mux: Open
[00000575] vorbis encoder error: CBR mode initialisation failed
[00000543] stream_out_transcode stream out error: cannot find audio encoder (module:any fourcc:vorb)
[00000543] stream_out_transcode stream out error: cannot create audio chain
[00000573] main packetizer error: cannot create packetizer output (mp3 )
[00000552] main mux error: cannot add this stream
[00000558] main packetizer error: cannot create packetizer output (FLV1)

```

This is with Ogg/Vorbis/Theora.

---

