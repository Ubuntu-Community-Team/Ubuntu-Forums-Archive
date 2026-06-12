---
title: "Using FFMpeg SVN or Source + Mplayer"
date: 2008-03-09
forum: Multimedia &amp; Video
---

### Post by SoulSmasher on 2008-03-09
hi, i want to play x264 mkv HD movies in mplayer (which i compiled from a guide [here]("http://ubuntuforums.org/showthread.php?t=558538")) with ffmpeg
i compiled ffmpeg using [this guide]("https://wiki.ubuntu.com/ffmpeg") , but no use. i can't see ffmpeg in mplayer (i'm using smplayer as gui, but neither i can see it, there are standart xv, gl, gl2 etc. xv's resizing sucks, gl is ok but its performance sucks)

i used to use ffdshow in windows for HD movies, it just used to work ok :(

it's not a must to use mplayer, i just wonder how i can use (ffdshow) ffmpeg ?

thanks for any further advices,
Cheers
Arda

---

### Post by xc3RnbFO8P on 2008-03-09
try this:

> wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb)
sudo dpkg -i w32codecs_20071007-0medibuntu1_i386.deb

---

### Post by SoulSmasher on 2008-03-09
> **Ringi said:**
> try this:


ok, i seen a file given [here]("http://www.debian-multimedia.org/dists/stable/main/binary-i386/package/w32codecs.php")

> ATI VCR-2 video codec.
Cinepak video codec
DivX ;-) video codec, ver. 3.11
DivX ;-) video codec, ver. 4.x
Indeo Video 3.2/4.1/5.0/4.1 quick/5.0 quick codecs.
Intel 263 video codec.
Microsoft MPEG-4 video codec, beta version 3.0.0.2700
Morgan Multimedia Motion JPEG video codec.
QuickTime
RealAudio
RealVideo 8
RealVideo 9
Windows Media Video 9

do those have the same contents? because ffdshow (ffmpeg) isn't there :(

---

### Post by xc3RnbFO8P on 2008-03-09
First install it and try if it works.

---

### Post by xc3RnbFO8P on 2008-03-09
If it dont work try this:

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

And in Synaptic Package Manager  search: ffmpeg.

---

### Post by rvm4000 on 2008-03-09
> **SoulSmasher said:**
> hi, i want to play x264 mkv HD movies in mplayer (which i compiled from a guide [here]("http://ubuntuforums.org/showthread.php?t=558538")) with ffmpeg
i compiled ffmpeg using [this guide]("https://wiki.ubuntu.com/ffmpeg") , but no use. i can't see ffmpeg in mplayer (i'm using smplayer as gui, but neither i can see it, there are standart xv, gl, gl2 etc. xv's resizing sucks, gl is ok but its performance sucks)

As far as I know, ffmpeg is already included in the sources of mplayer. xv, gl and so on are output drivers, nothing to do with ffmpeg.

You also won't find a codec named "ffmpeg", but there are a lot of video and audio codecs which start with "ff". Those are the codecs from ffmpeg.

For example a list of video codecs:
> 
> mplayer -vc help | grep "^ff*"

ffkmvc      ffmpeg    problems  ffkmvc  [kmvc]
ffzmbv      ffmpeg    working   FFmpeg Zip Motion-Block Video  [zmbv]
ffmpeg1     ffmpeg    working   FFmpeg MPEG-1  [mpeg1video]
ffmpeg2     ffmpeg    working   FFmpeg MPEG-2  [mpeg2video]
ffmpeg12    ffmpeg    working   FFmpeg MPEG-1/2  [mpegvideo]
ffmpeg12mc  ffmpeg    problems  FFmpeg MPEG-1/2 (XvMC)  [mpegvideo_xvmc]
ffnuv       ffmpeg    working   NuppelVideo  [nuv]
ffbmp       ffmpeg    working   FFmpeg BMP decoder  [bmp]
ffgif       ffmpeg    working   FFmpeg GIF decoder  [gif]
fftiff      ffmpeg    working   FFmpeg TIFF decoder  [tiff]
ffpcx       ffmpeg    working   FFmpeg PCX decoder  [pcx]
ffpng       ffmpeg    working   FFmpeg PNG decoder  [png]
fftga       ffmpeg    untested  FFmpeg TGA decoder  [targa]
ffsunras    ffmpeg    working   FFmpeg SUN Rasterfile decoder  [sunrast]
ffindeo3    ffmpeg    working   FFmpeg Intel Indeo 3.1/3.2  [indeo3]
fffli       ffmpeg    working   Autodesk FLI/FLC Animation  [flic]
ffaasc      ffmpeg    working   Autodesk RLE decoder  [aasc]
ffloco      ffmpeg    working   LOCO video decoder  [loco]
ffqtrle     ffmpeg    working   QuickTime Animation (RLE)  [qtrle]
ffrpza      ffmpeg    working   QuickTime Apple Video  [rpza]
ffsmc       ffmpeg    working   Apple Graphics (SMC) codec  [smc]
ff8bps      ffmpeg    working   Planar RGB (Photoshop)  [8bps]
ffcyuv      ffmpeg    working   Creative YUV (libavcodec)  [cyuv]
ffmsrle     ffmpeg    working   Microsoft RLE  [msrle]
ffroqvideo  ffmpeg    working   Id RoQ File Video Decoder  [roqvideo]
ffcvid      ffmpeg    working   Cinepak Video (native codec)  [cinepak]
ffvideo1    ffmpeg    working   Microsoft Video 1 (native codec)  [msvideo1]
ffmszh      ffmpeg    working   AVImszh (native codec)  [mszh]
ffzlib      ffmpeg    working   AVIzlib (native codec)  [zlib]
ffhuffyuv   ffmpeg    working   FFmpeg HuffYUV  [huffyuv]
ffv1        ffmpeg    working   FFV1 (lossless codec)  [ffv1]
ffsnow      ffmpeg    working   FFSNOW (Michael's wavelet codec)  [snow]
ffasv1      ffmpeg    working   FFmpeg ASUS V1  [asv1]
ffasv2      ffmpeg    working   FFmpeg ASUS V2  [asv2]
ffvcr1      ffmpeg    working   FFmpeg ATI VCR1  [vcr1]
ffcljr      ffmpeg    working   FFmpeg Cirrus Logic AccuPak (CLJR)  [cljr]
ffsvq1      ffmpeg    working   FFmpeg Sorenson Video v1 (SVQ1)  [svq1]
ff4xm       ffmpeg    working   FFmpeg 4XM video  [4xm]
ffvixl      ffmpeg    working   Miro/Pinnacle VideoXL codec  [xl]
ffqtdrw     ffmpeg    working   QuickDraw native decoder  [qdraw]
ffindeo2    ffmpeg    working   Indeo 2 native decoder  [indeo2]
ffflv       ffmpeg    working   FFmpeg Flash video  [flv]
fffsv       ffmpeg    working   FFmpeg Flash Screen video  [flashsv]
ffdivx      ffmpeg    working   FFmpeg DivX ;-) (MSMPEG-4 v3)  [msmpeg4]
ffmp42      ffmpeg    working   FFmpeg MSMPEG-4 v2  [msmpeg4v2]
ffmp41      ffmpeg    working   FFmpeg MSMPEG-4 v1  [msmpeg4v1]
ffwmv1      ffmpeg    working   FFmpeg WMV1/WMV7  [wmv1]
ffwmv2      ffmpeg    working   FFmpeg WMV2/WMV8  [wmv2]
ffwmv3      ffmpeg    problems  FFmpeg WMV3/WMV9  [wmv3]
ffvc1       ffmpeg    problems  FFmpeg WVC1  [vc1]
ffh264      ffmpeg    working   FFmpeg H.264  [h264]
ffsvq3      ffmpeg    working   FFmpeg Sorenson Video v3 (SVQ3)  [svq3]
ffodivx     ffmpeg    working   FFmpeg MPEG-4  [mpeg4]
ffwv1f      ffmpeg    working   WV1F MPEG-4  [mpeg4]
ffmjpeg     ffmpeg    working   FFmpeg MJPEG decoder  [mjpeg]
ffmjpegb    ffmpeg    working   FFmpeg MJPEG-B decoder  [mjpegb]
ffi263      ffmpeg    working   FFmpeg I263 decoder  [h263i]
ffh263      ffmpeg    working   FFmpeg H.263+ decoder  [h263]
ffzygo      ffmpeg    untested  FFmpeg ZyGo  [h263]
ffh261      ffmpeg    working   CCITT H.261  [h261]
ffdv        ffmpeg    working   FFmpeg DV decoder  [dvvideo]
ffrv20      ffmpeg    working   FFmpeg RV20 decoder  [rv20]
ffrv10      ffmpeg    working   FFmpeg RV10 decoder  [rv10]
ffvp3       ffmpeg    untested  FFmpeg VP3  [vp3]
fftheora    ffmpeg    untested  FFmpeg Theora  [theora]
ffvp5       ffmpeg    working   FFmpeg VP5 decoder  [vp5]
ffvp6       ffmpeg    working   FFmpeg VP6 decoder  [vp6]
ffvp6f      ffmpeg    working   FFmpeg VP6 Flash decoder  [vp6f]
ffultimotion ffmpeg    working   IBM Ultimotion native decoder  [ultimotion]
ffduck      ffmpeg    working   Duck Truemotion1  [truemotion1]
fftm20      ffmpeg    working   FFmpeg Duck/On2 TrueMotion 2.0  [truemotion2]
ffamv       ffmpeg    working   Modified MJPEG, used in AMV files  [amv]
ffsp5x      ffmpeg    working   SP5x codec - used by Aiptek MegaCam  [sp5x]
ffwnv1      ffmpeg    working   FFmpeg wnv1 native codec  [wnv1]
ffvmnc      ffmpeg    working   FFmpeg VMware video  [VMware video]
ffsmkvid    ffmpeg    working   FFmpeg Smacker Video  [smackvid]
ffcavs      ffmpeg    working   Chinese AVS Video  [cavs]
ffcamtasia  ffmpeg    working   TechSmith Camtasia Screen Codec (native)  [camtasia]
ffcamstudio ffmpeg    working   CamStudio Screen Codec  [camstudio]
fraps       vfw       working   FRAPS: Realtime Video Capture  [frapsvid.dll]
fffraps     ffmpeg    working   FFmpeg Fraps  [fraps]
fftiertexseq ffmpeg    working   FFmpeg Tiertex SEQ  [tiertexseqvideo]
ffvmd       ffmpeg    working   FFmpeg Sierra VMD video  [vmdvideo]
ffdxa       ffmpeg    working   FFmpeg Feeble Files DXA video  [dxa]
ffdsicinvideo ffmpeg    working   FFmpeg Delphine CIN video  [dsicinvideo]
ffthp       ffmpeg    working   FFmpeg THP video  [thp]
ffbethsoftvid ffmpeg    problems  FFmpeg Bethesda Software VID  [bethsoftvid]
fftxd       ffmpeg    working   FFmpeg Renderware TeXture Dictionary decoder  [txd]
ffwc3       ffmpeg    problems  FFmpeg XAN wc3  [xan_wc3]
ffidcin     ffmpeg    problems  FFmpeg Id CIN video  [idcinvideo]
ffinterplay ffmpeg    problems  FFmpeg Interplay Video  [interplayvideo]
ffvqa       ffmpeg    problems  FFmpeg VQA Video  [vqavideo]
ffc93       ffmpeg    problems  FFmpeg C93 Video  [c93]


But you usually won't need to select a codec manually, mplayer will always try to use the fastest one.

---

### Post by SoulSmasher on 2008-03-09
> **rvm4000 said:**
> As far as I know, ffmpeg is already included in the sources of mplayer. xv, gl and so on are output drivers, nothing to do with ffmpeg.

You also won't find a codec named "ffmpeg", but there are a lot of video and audio codecs which start with "ff". Those are the codecs from ffmpeg.

For example a list of video codecs:


But you usually won't need to select a codec manually, mplayer will always try to use the fastest one.

ok then let me change the question a bit:) . why i can't get a smooth resizing with good performance like windows does? *is there another output module which does this job (i mean, smooth resizing with good performance?)*

thanks for your replies :)

---

### Post by andrew.46 on 2008-03-09
Hi,

 I see some of the confusion has been cleared a little, although I am a little puzzled as to why you are having performance issues with mplayer. As has been pointed out mplayer incorporates and uses the ffmpeg libraries.

 I do have 2 suggestions for you though that might perhaps help:

1. Try downloading and installing the subversion x264 as follows:

```
$ svn co svn://svn.videolan.org/x264/trunk x264
$ cd x264
$ ./configure --enable-shared
$ make
$ sudo make install
```

And then compile the svn mplayer *again* as per the excellent guide that you mentioned (yes it is my guide!). mplayer wil thenl pick up the new libraries and use them. I would be surprised if this did not lift the performance expotentially.

2. A lesser choice that I do not have such confidence in is if you have ffmpeg installed it has a little viewer called ffplay that you could perhaps try. This runs from the command line and is not the flashest bit of software ever seen :-)

 Please let me know if either of these choices is of any assistance.

                    Andrew

---

### Post by janfsd on 2008-03-09
I think that x264 is just the encoder, the decoder is already in ffmpeg.

---

### Post by rvm4000 on 2008-03-09
> **SoulSmasher said:**
> ok then let me change the question a bit:) . why i can't get a smooth resizing with good performance like windows does? *is there another output module which does this job (i mean, smooth resizing with good performance?)*

xv produces the best performance. x11, gl, gl2... are slower.

But why is so important a smooth resizing? How many times do you resize a video?
Anyway I think resizing (using xv) is a little better in smplayer than in mplayer itself, at least there's no flickering.

---

### Post by SoulSmasher on 2008-03-10
@andrew.46 - it's the same :(

> **rvm4000 said:**
> xv produces the best performance. x11, gl, gl2... are slower.

But why is so important a smooth resizing? How many times do you resize a video?
Anyway I think resizing (using xv) is a little better in smplayer than in mplayer itself, at least there's no flickering.

well, if you're having a 1080p movie that cannot fit on your screen, you've to resize :) and it looks so bad :(, for divx stuff gl gl2 handles the job excellently, but for 1080p movies, it's such a cancer :(

are there any handy output modules for smoth resizing with good performance?

---

### Post by eye208 on 2008-03-10
> **SoulSmasher said:**
> it looks so bad :(
What does "bad" mean? Pixelated? No anti-aliasing?

The only output module giving pixelated results on resizing is X11 software rendering. Maybe that's what you see because your Xv overlay doesn't work at all and MPlayer uses X11 as a fallback option. Do you have an ATI card? Did you run "sudo aticonfig --ovt Xv"? Are you running Compiz (i.e. desktop effects)?

---

### Post by SoulSmasher on 2008-03-10
ive an ati card (mobility radeon x1300, which uses latest drivers with envy) and my resolution is 1280*800

compiz is deactivated, and using metacity while doing those stuff :)

when i try to play a video with xv , which's resolution is lower than my resolution, it becomes blocky (it's ok with gl , gl2 for standart divx videos with good performance btw), but when i play a 1080p movie (usually 1920*800, or 1920*1080 resolution), it (also vlc) does not make a smooth resize to my resolution (it looks like i's not anti-aliased yes)..

---

### Post by eye208 on 2008-03-10
Last time I used the ATI driver (fglrx), it would support either Xv or GL overlay, with GL being the default. Since GL overlay seems to work fine for you, I'd suppose Xv is disabled and MPlayer uses X11 instead. You can confirm this by running MPlayer from the command line and watching its console output.

To enable Xv (and disable GL overlay), run "sudo aticonfig --ovt Xv" once. The new setting will be written to the xorg.conf file. You need to restart X to apply it.

---

### Post by andrew.46 on 2008-03-10
Hi,

My apologies:

> **SoulSmasher said:**
> @andrew.46 - it's the same :(

Looks like janfsd is correct and the updated x264 is good for *encoding* but not *decoding.* In which case I am a little stumped as to your problem.

  Andrew

---

### Post by SoulSmasher on 2008-03-10
i think it is normal by the way, thank you all guys, so i just will watch 1080p stuff on my other pc which windows is installed.

**thank you all for your efforts on help :)**

---

### Post by janfsd on 2008-03-10
What are your pc specs?

---

### Post by rvm4000 on 2008-03-10
> **SoulSmasher said:**
> well, if you're having a 1080p movie that cannot fit on your screen, you've to resize :) and it looks so bad :(, for divx stuff gl gl2 handles the job excellently, but for 1080p movies, it's such a cancer :(

Ah, I thought you meant flickering problems while resizing the window. For me, what you explain is "scaling".

I have a nvidia card and xv gives a very good quality even in fullscreen (also x11 gives good quality, but it's slow). In fact I only have seen a very bad quality using directx:noaccel in windows.

If xv gives bad results for you, you can try soft scaling (of course that will use a lot of CPU). smplayer already has an option for that in the video filters menu.
In mplayer it can be done with something like:
```

mplayer video.avi -vf scale=1280:-2 -sws 9

```
(change the 1280 with the width of your screen)

---

