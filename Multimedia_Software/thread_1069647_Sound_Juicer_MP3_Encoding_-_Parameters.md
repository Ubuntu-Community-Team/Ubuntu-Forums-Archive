---
title: "Sound Juicer MP3 Encoding - Parameters"
date: 2009-02-14
forum: Multimedia Software
---

### Post by kwc01 on 2009-02-14
Hello,

For some reason I can't seem to find any instructions on parameters for GStreamer & lame used by Sound Juicer for encoding MP3s.  I'm wanting to encode VBR from min of 192 to max of 320, with average rates around 225-256.

Can someone point me toward the correct parameters to use?

I using Ubuntu 8.10 and Sound Juicer 2.24.0.

Thanks so much,
kwc

---

### Post by logos34 on 2009-02-14
> audio/x-raw-int,rate=44100,channels=2  !  lame name=enc mode=1 vbr=4 vbr-quality=1 vbr-max-bitrate=320 ! id3v2mux

this will encode @ [vbr-new V1]("http://wiki.hydrogenaudio.org/index.php?title=LAME#VBR_.28variable_bitrate.29_settings") (~225k), joint-stereo (I don't think you even need the 'vbr-max' as 320k ceiling is default)...but you may need 'vbr-min' to bring up the bottom from ~128k or so

or use ABR settings

See:

**gst-inspect lame**

---

