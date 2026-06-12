---
title: "Installing Moonlight (Silverlight) from SVN on Intrepid"
date: 2008-11-24
forum: Multimedia Software
---

### Post by Filmorependrgn on 2008-11-24
NOTE: WORK IN PROGRESS
Here's a quick recap of my experiences with getting Moonlight to install from their SVN repository. this is only for Moonlight supporting Silverlight 1.0. For Silverlight 2.0 support, Mono libraries version 2.0 or greater are required, which are included in Jaunty. But since I don't have a computer to use as a development computer at the moment, I'll wait until Jaunty is released to update with Silverlight 2.0 instructions.

1) Download the code for Moonlight
```
svn co svn://anonsvn.mono-project.com/source/trunk/moon
```
This code will create a directory called "moon" where the source is stored.
```
cd moon
```

2) Get FFMPEG configured.
2a) Download the FFMPEG source
```
sudo aptitude build-dep ffmpeg
apt-get source ffmpeg
cd ffmpeg-debian*

```
2b) Configure ffmpeg.
The Moonlight compile directions recommend the following:
```
 ./configure --disable-static --enable-shared --disable-ffmpeg --disable-ffserver --disable-ffplay --disable-zlib --disable-network --disable-vhook --disable-debug --disable-muxers --disable-encoders --disable-demuxers --disable-bsfs --disable-protocols
```
But I used the Ubuntu config flags which can be seen if you type `ffmpeg -v' Which, ironically enough, gives an error about `Unknown option -v' but hey... we got what we needed. For this release of ffmpeg, the config flags are as follows:
```
./configure  --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
```

2d) Build ffmpeg. This step was a pain in the *** as it took a lot of manual coding on my part to get it to work. I have submitted a [bug report]("https://bugs.launchpad.net/ubuntu/+source/ffmpeg-debian/+bug/302049"). The hot-fix below assumes that you know the basics of coding (sorry for the lack of detail, but I assume this step will be much easier in the future).
Modify libavcodec/h263.h to look more like this
```

#if defined(ENABLE_H263_DECODER) || \
                                 defined(ENABLE_H263I_DECODER)   || \
                                 defined(ENABLE_FLV_DECODER)     || \
                                 defined(ENABLE_RV10_DECODER)    || \
                                 defined(ENABLE_RV20_DECODER)    || \
                                 defined(ENABLE_MPEG4_DECODER)   || \
                                 defined(ENABLE_MSMPEG4_DECODER) || \
                                 defined(ENABLE_WMV_DECODER)
#define ENABLE_ANY_H263_DECODER 1
#else
#define ENABLE_ANY_H263_DECODER 0
#endif

#if defined(ENABLE_H263_ENCODER)    || \
                                 defined(ENABLE_H263P_ENCODER)   || \
                                 defined(ENABLE_FLV_ENCODER)     || \
                                 defined(ENABLE_RV10_ENCODER)    || \
                                 defined(ENABLE_RV20_ENCODER)    || \
                                 defined(ENABLE_MPEG4_ENCODER)   || \
                                 defined(ENABLE_MSMPEG4_ENCODER) || \
                                 defined(ENABLE_WMV_ENCODER)
#define ENABLE_ANY_H263_ENCODER 1
#else
#define ENABLE_ANY_H263_ENCODER 0
#endif

```
Also add all those pesky ENABLE_((SOMETHING))_ENCODER defines anywhere into config.h
For me it was
```

#define ENABLE_H261_ENCODER 0
#define ENABLE_MPEG4_ENCODER 0
#define ENABLE_MSMPEG4V1_ENCODER 0
#define ENABLE_MSMPEG4V2_ENCODER 0
#define ENABLE_MSMPEG4V3_ENCODER 0
#define ENABLE_MPEG2VIDEO_ENCODER 0
#define ENABLE_H263_ENCODER 0
#define ENABLE_H263P_ENCODER 0

```

3) Configure Moonlight.

```
 PKG_CONFIG_PATH=$PATH_TO_FFMPEG_SOURCE ./autogen.sh --enable-directfb --enable-ps --enable-pdf --enable-svg --enable-xcb --enable-glitz --enable-user-plugin  --with-ffmpeg=yes --with-alsa=yes --with-pulse-audio=no --with-managed=no --with-ff3=yes
```
Where $PATH_TO_FFMPEG_SOURCE is the *absolute* path to your ffmpeg source from step 2.

3b) If you try to build Moonlight at this point, you'll probably get a lot of errors due to missing components. You'll want to find each component and install the associated "library-dev" package. The only non-obvious one is that, to build a Firefox plugin, you need the xulrunner package.
```
sudo aptitude install xulrunner-1.9-dev
```
If you feel lucky, and wanna try the same one's I did, try this code:
```
sudo aptitude install libxtst-dev libmagick++9-dev libasound2-dev xulrunner-1.9-dev libdbus-glib-1-dev librsvg2-2 librsvg2-dev libpoppler-glib-dev libdirectfb-dev libglitz-glx1-dev libglitz1-dev xcb xcb-proto ggcov libgtk2.0-dev  libglibmm-2.4-dev  libglibmm-utils-dev libglib2.0-dev 
```

4) Build Moonlight. If you're lucky, it'll compile without any more errors. The final plugin will be located at ```
moon/plugin/install/novell-moonlight.xpi
```

---

### Post by directhex on 2008-11-25
Why bother compiling your own FFmpeg? The existing lib in Intrepid is fine with 8/9 of the SL1.0 codecs, and the last one is rarely used

---

### Post by Filmorependrgn on 2008-11-25
> **directhex said:**
> Why bother compiling your own FFmpeg? The existing lib in Intrepid is fine with 8/9 of the SL1.0 codecs, and the last one is rarely used

Mostly because I wanted to follow the install guide as closely as possible while trying to retain as much of Ubuntu's source as possible. Also, I couldn't quite figure out the proper procedure for using the existing libs.

---

### Post by tharsan on 2008-11-26
I was able to get Moonlight up and running in Firefox 3 in my Intrepid installation by compiling Moonlight from source, using the Ubuntu-recommended configure line you posted.

I just installed the libavcodec-dev and libavutil-dev packages along with the existing ubuntu ffmpeg package, instead of compiling ffmpeg from source.

Many sites don't seem to detect the presence of Moonlight, however (despite the plugin showing up in my Firefox Add-Ons list) and insist that I install Silverlight.

---

### Post by directhex on 2008-11-26
> **tharsan said:**
> I was able to get Moonlight up and running in Firefox 3 in my Intrepid installation by compiling Moonlight from source, using the Ubuntu-recommended configure line you posted.

I just installed the libavcodec-dev and libavutil-dev packages along with the existing ubuntu ffmpeg package, instead of compiling ffmpeg from source.

Many sites don't seem to detect the presence of Moonlight, however (despite the plugin showing up in my Firefox Add-Ons list) and insist that I install Silverlight.

Right now, you're compiling a SL 1.0-only package (--with-managed=no). If a site has been moved to SL 2.0, you're not gonna get much joy from it - hence the "install silverlight" button

SL 2.0 support only just had developers start work on it, SL 1.0 support is complete but being bugfixed

---

### Post by Obnesence on 2008-11-26
Thank you for the post.  I was able to build and install Silverlight 1.9 with some modifications of your instructions.  I set me user agent up to report me as Firefox 3.0 on Windows Vista and went to Netflix.  Signed up for their Silverlight Beta program and attempted to watch a video.  Got a blank white screen surrounded by black.

It didn't work, but I am excited.  Another few months of development and I will be able to watch Netflix on Linux!

---

### Post by directhex on 2008-11-26
> **Obnesence said:**
> Thank you for the post.  I was able to build and install Silverlight 1.9 with some modifications of your instructions.  I set me user agent up to report me as Firefox 3.0 on Windows Vista and went to Netflix.  Signed up for their Silverlight Beta program and attempted to watch a video.  Got a blank white screen surrounded by black.

It didn't work, but I am excited.  Another few months of development and I will be able to watch Netflix on Linux!

Very possibly, but I doubt you will with FFmpeg - NetFlix use the DRM functionality in SL 2.0. Moonlight will offer support for the DRM, but only via the closed-source Microsoft Media Pack codec addon. Which may offend on moral grounds (more than Moon does already)

---

### Post by Obnesence on 2008-11-26
> **directhex said:**
> Very possibly, but I doubt you will with FFmpeg - NetFlix use the DRM functionality in SL 2.0. Moonlight will offer support for the DRM, but only via the closed-source Microsoft Media Pack codec addon. Which may offend on moral grounds (more than Moon does already)

Yes, distasteful, I agree.  I visited MS's Silverlight site and it prompted me to install their codecs.  I did so.  Some sites actually worked after I did that.  Not Netflix though.  All I got was a white rectangle surrounded by black.

---

