---
title: "VLC and huffyuv Videos - Green Screen"
date: 2012-05-04
forum: Multimedia Software
---

### Post by dodle on 2012-05-04
I have a huffyuv encoded video file:

```
deluge@debian:~/Desktop$ mediainfo test.avi
General
Complete name                    : test.avi
Format                           : AVI
Format/Info                      : Audio Video Interleave
File size                        : 372 MiB
Duration                         : 10s 33ms
Overall bit rate                 : 311 Mbps
Writing application              : Lavf52.111.0

Video
ID                               : 0
Format                           : Huffman
Codec ID                         : HFYU
Duration                         : 10s 33ms
Bit rate                         : 311 Mbps
Width                            : 1 280 pixels
Height                           : 800 pixels
Display aspect ratio             : 1.600
Frame rate                       : 30.000 fps
Color space                      : RGB
Bit depth                        : 8 bits
Bits/(Pixel*Frame)               : 10.111
Stream size                      : 372 MiB (100%)
```

But VLC only displays a green screen when I play it. Any ideas? Is there a decoder that I need to get? MPlayer plays the video just fine and on Windows VLC has no problem with huffyuv.


**----- EDIT -----**

I've figured out that this is a problem with the builds of libav in the debian-multimedia repository. I'm in the process of working it out now.


**----- SOLVED -----**

I removed vlc and ffmpeg and created a file called /etc/apt/preferences and placed in it:

```
Package: *
Pin: origin ftp.debian-multimedia.org
Pin-Priority: 1
```

I cleared the apt cache and updated, then reinstalled vlc and ffmpeg. All seems well.

---

