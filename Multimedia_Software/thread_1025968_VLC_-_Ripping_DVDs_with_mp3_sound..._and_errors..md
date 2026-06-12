---
title: "VLC - Ripping DVDs with mp3 sound... and errors."
date: 2008-12-30
forum: Multimedia Software
---

### Post by transmition on 2008-12-30
Hello, I am trying to make a copy of a dvd with vlc using the MPEG-TS container, h264 video codec with a bitrate of 2048 kb/s and an audio codec of mp3 with 2 channels and a 256 kb/s bitrate. However, I get this error when I try and start streaming/saving: 

```

[00000456] a52 packetizer: A/52 channels:6 samplerate:48000 bitrate:384000
[00000464] avcodec encoder error: cannot find encoder MPEG Audio layer 1/2/3
[00000410] stream_out_transcode stream out error: cannot find audio encoder (module:any fourcc:mp3 )
[00000410] stream_out_transcode stream out error: cannot create audio chain
[00000456] main packetizer error: cannot create packetizer output (a52 )
[00000475] a52 packetizer: A/52 channels:6 samplerate:48000 bitrate:384000
[00000477] avcodec encoder error: cannot find encoder MPEG Audio layer 1/2/3
[00000410] stream_out_transcode stream out error: cannot find audio encoder (module:any fourcc:mp3 )
[00000410] stream_out_transcode stream out error: cannot create audio chain
[00000475] main packetizer error: cannot create packetizer output (a52 )

```

When done, I get superb video, but no audio whatsoever. I have also tried this with flac, MPEG audio, and MP4 audio, and get similar errors (with the exception of flac, which still has no sound)

I can play the DVD in VLC, and have installed all the gstreamer codecs, win32codecs(?) from mediabuntu, as well as the lib2dvdcss(?) codec from the mediabuntu page.

Can anyone explain what is going on?

---

### Post by transmition on 2008-12-31
*Bump*

---

