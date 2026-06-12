---
title: "vlc ffmpeg error during transcoding"
date: 2008-05-30
forum: Multimedia Software
---

### Post by tamray on 2008-05-30
Using Ubuntu Gutsy

I am attempting to use vlc to transcode avi files to wmv. I get video, but no audio on the output file. The logs below show that I am missing necessary libraries. Can I use apt to install what is missing? If so, what packages would I install? 


ffmpeg error: cannot find encoder MPEG Audio layer 1/2/3
stream_out_transcode error: cannot find encoder ((null))
main debug: removing module "mpeg_audio"
stream_out_transcode error: cannot create audio chain
main error: cannot create packetizer output (mpga)

---

### Post by tamray on 2008-05-30
Followed this howto to enable mp3 capabilities, but still get the same error.

([http://symbiotix.net/articles/compiling-ffmpeg-mp3-ubuntu-revised-ubuntu-gutsy-server#comment-543](http://symbiotix.net/articles/compiling-ffmpeg-mp3-ubuntu-revised-ubuntu-gutsy-server#comment-543))

---

