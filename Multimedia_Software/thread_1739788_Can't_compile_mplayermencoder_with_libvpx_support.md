---
title: "Can't compile mplayer/mencoder with libvpx support"
date: 2011-04-26
forum: Multimedia Software
---

### Post by sbrbot on 2011-04-26
I want to encode video content with mencoder and libvpx codec.

--

I have libvpx installed on my machine and I can encode with libvpx using
ffmpeg. My OS is Ubuntu 10.10, 64bit.

--

I downloaded fresh mplayer/mencoder from SVN repository. 

If I configure mplayer/mencoder without any explicit enabled features using:

```
$ ./configure
```

I'm able to compile it but I'm unable to encode video content with it.
For the following command:

```
$ mencoder big_buck_bunny_360p24.y4m -nosound
           -ovc lavc -lavcopts vcodec=libvpx
           -of lavf -lavfopts format=webm
           -o big_buck_bunny.webm

```
I get the following error message:

```
OK, exit.
Cannot find codec 'libvpx' in libavcodec...
Couldn't open video filter 'lavc'.
Failed to open the encoder.

```
--

If I explicitly enable libvpx in lavc with:

```
$ ./configure --enable-libvpx-lavc
```

I cannot compile it any more. I get the following error message:

```
ffmpeg/libavcodec/libavcodec.a(libvpxdec.o): In function `vp8_decode':
libvpxdec.c:(.text+0x49): undefined reference to `vpx_codec_decode'
libvpxdec.c:(.text+0x5e): undefined reference to `vpx_codec_get_frame'
libvpxdec.c:(.text+0x154): undefined reference to `vpx_codec_error'
libvpxdec.c:(.text+0x15f): undefined reference to `vpx_codec_error_detail'
ffmpeg/libavcodec/libavcodec.a(libvpxdec.o): In function `vp8_free':
libvpxdec.c:(.text.unlikely+0xc): undefined reference to `vpx_codec_destroy'
ffmpeg/libavcodec/libavcodec.a(libvpxdec.o): In function `vp8_init':
libvpxdec.c:(.text.unlikely+0x47): undefined reference to `vpx_codec_version_str'
libvpxdec.c:(.text.unlikely+0x63): undefined reference to `vpx_codec_build_config'
libvpxdec.c:(.text.unlikely+0x8a): undefined reference to `vpx_codec_vp8_dx_algo'
libvpxdec.c:(.text.unlikely+0x92): undefined reference to `vpx_codec_dec_init_ver'
libvpxdec.c:(.text.unlikely+0x9e): undefined reference to `vpx_codec_error'
ffmpeg/libavcodec/libavcodec.a(libvpxenc.o): In function `vp8_encode':
libvpxenc.c:(.text+0x7d): undefined reference to `vpx_codec_encode'
libvpxenc.c:(.text+0xd9): undefined reference to `vpx_codec_get_cx_data'
ffmpeg/libavcodec/libavcodec.a(libvpxenc.o): In function `vp8_free':
libvpxenc.c:(.text.unlikely+0x14): undefined reference to `vpx_codec_destroy'
ffmpeg/libavcodec/libavcodec.a(libvpxenc.o): In function `log_encoder_error':
libvpxenc.c:(.text.unlikely+0x409): undefined reference to `vpx_codec_error'
libvpxenc.c:(.text.unlikely+0x414): undefined reference to `vpx_codec_error_detail'
ffmpeg/libavcodec/libavcodec.a(libvpxenc.o): In function `codecctl_int':
libvpxenc.c:(.text.unlikely+0x4e5): undefined reference to `vpx_codec_control_'
ffmpeg/libavcodec/libavcodec.a(libvpxenc.o): In function `vp8_init':
libvpxenc.c:(.text.unlikely+0x55f): undefined reference to `vpx_codec_version_str'
libvpxenc.c:(.text.unlikely+0x57b): undefined reference to `vpx_codec_build_config'
libvpxenc.c:(.text.unlikely+0x59c): undefined reference to `vpx_codec_vp8_cx_algo'
libvpxenc.c:(.text.unlikely+0x5a1): undefined reference to `vpx_codec_enc_config_default'
libvpxenc.c:(.text.unlikely+0x5ac): undefined reference to `vpx_codec_err_to_string'
libvpxenc.c:(.text.unlikely+0x83f): undefined reference to `vpx_codec_vp8_cx_algo'
libvpxenc.c:(.text.unlikely+0x847): undefined reference to `vpx_codec_enc_init_ver'
libvpxenc.c:(.text.unlikely+0x906): undefined reference to `vpx_img_wrap'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```

---

### Post by Yellow Pasque on 2011-04-26
And you have libvpx-dev installed?

---

### Post by sbrbot on 2011-04-26
> **Temüjin said:**
> And you have libvpx-dev installed?
Of course.

---

### Post by andrew.46 on 2011-04-26
I suspect that your version of libvpx might be too old, but I am not entirely sure as I have not used MEncoder for some time :). However on my own system the svn MEncoder encodes to webm with no trouble, using libvpx 0.9.6:

```

andrew@skamandros~/music/YouTube$ mencoder Cold_Chisel_Bow_River.mp4 -nosound -ovc lavc -lavcopts vcodec=libvpx -of lavf -lavfopts format=webm -o test.webm
MEncoder SVN-r33331-4.5.2 (C) 2000-2011 MPlayer Team
success: format: 0  data: 0x0 - 0x12ec31c
libavformat file format detected.
[lavf] stream 0: audio (aac), -aid 0, -alang und
[lavf] stream 1: video (h264), -vid 0
VIDEO:  [H264]  320x240  24bpp  29.917 fps  253.6 kbps (31.0 kbyte/s)
[V] filefmt:44  fourcc:0x34363248  size:320x240  fps:29.917  ftime:=0.0334
** MUXER_LAVF *****************************************************************
REMEMBER: MEncoder's libavformat muxing is presently broken and can generate
INCORRECT files in the presence of B-frames. Moreover, due to bugs MPlayer
will play these INCORRECT files as if nothing were wrong!
*******************************************************************************
OK, exit.
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
videocodec: libavcodec (320x240 fourcc=30385056 [VP80])
**[COLOR="Red"][libvpx @ 0x89965a0]v0.9.6[/COLOR]**
VIDEO CODEC ID: 145
Writing header...
[webm @ 0x8924ca0]Codec for stream 0 does not use global headers but container format requires global headers
Pos: 422.4s  12638f (100%) 38.25fps Trem:   0min  40mb  A-V:0.000 [803:0]

Flushing video frames.
Writing index...

Video stream:  803.652 kbit/s  (100456 B/s)  size: 42436407 bytes  422.435 secs  12638 frames

```

and certainly the resulting file looks ok:

```

andrew@skamandros~/music/YouTube$ mediainfo test.webm 
General
Unique ID                        : 29598461007409727587718975382533857384 (0x164474CBE53015442BDEC17AF1DA6068)
Complete name                    : test.webm
Format                           : WebM
File size                        : 40.6 MiB
Duration                         : 7mn 2s
Overall bit rate                 : 806 Kbps
Writing application              : Lavf53.0.3
Writing library                  : Lavf53.0.3

Video
ID                               : 1
Format                           : VP8
Codec ID                         : V_VP8
Duration                         : 7mn 2s
Bit rate                         : 767 Kbps
Width                            : 320 pixels
Height                           : 240 pixels
Display aspect ratio             : 4:3
Frame rate                       : 29.917 fps
Compression mode                 : Lossy
Bits/(Pixel*Frame)               : 0.334
Stream size                      : 38.6 MiB (95%)
Language                         : English

```

Perhaps try a more recent libvpx and then recompile MPlayer/MEncoder? This will not be necessary on natty as it has the more recent libvpx. Something like the following single command should work:

```

sudo apt-get install build-essential checkinstall && \
sudo apt-get remove libvpx-dev && cd $HOME/Desktop && \
wget http://webm.googlecode.com/files/libvpx-v0.9.6.tar.bz2 && \
tar xjvf libvpx-v0.9.6.tar.bz2 && cd libvpx-v0.9.6 && \
./configure && make && \
sudo checkinstall --pakdir "$HOME/Desktop" --backup=no \
                  --deldoc=yes --pkgname libvpx \
                  --pkgversion "0.9.6" --fstrans=no \
                  --deldesc=yes --delspec=yes --default

```

Hopefully this will get you going :).

---

