---
title: "Mplayer Firefox Plugin Stopped Working Unexpectedly"
date: 2008-09-04
forum: Multimedia Software
---

### Post by gollybegully on 2008-09-04
Im running Hardy and Mplayer Plugin worked perfectly until today.  It just says download complete and doesn't play the video.  Uninstalled and reinstalled Firefox and the plugin to no avail.

I don't even know where to start now.  It makes no sense because it was working earlier today and I haven't changed anything.  I've been running ubuntu exclusively for a couple years now but im seriously thinking of giving it up. This kind of instability is absurd.

---

### Post by gandaran on 2008-09-04
mplayer plugin is not very good for online streaming, sometimes works sometimes not, I suggest you find another player and plugin that you like in synaptic, there are many much better than mplayer, remove mplayer plugin (you can keep only the player if you prefer) before installing other player plugin.

---

### Post by gollybegully on 2008-09-04
Really?  I heard that Mplayer was really your only choice at this point.  VLC and some other one were pretty much useless at this point in development.  Which one do you use?

Can somebody point me in the right direction?  Is there maybe some configuration file i can look at on mplayerplugin?

As far as codecs, this is where I stand: (mplayer -vc help)

```
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (Family: 15, Model: 43, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Available video codecs:
vc:         vfm:      status:   info:  [lib/dll]
ffkmvc      ffmpeg    problems  ffkmvc  [kmvc]
ffzmbv      ffmpeg    working   FFmpeg Zip Motion-Block Video  [zmbv]
zmbv        vfw       working   Zip Motion-Block Video  [zmbv.dll]
mpegpes     mpegpes   working   MPEG-PES output (.mpg or DXR3/IVTV/DVB/V4L2 card)
mpeg12      libmpeg2  working   MPEG-1 or 2 (libmpeg2)
ffmpeg1     ffmpeg    working   FFmpeg MPEG-1  [mpeg1video]
ffmpeg2     ffmpeg    working   FFmpeg MPEG-2  [mpeg2video]
ffmpeg12    ffmpeg    working   FFmpeg MPEG-1/2  [mpegvideo]
ffmpeg12mc  ffmpeg    problems  FFmpeg MPEG-1/2 (XvMC)  [mpegvideo_xvmc]
ffnuv       ffmpeg    working   NuppelVideo  [nuv]
nuv         nuv       working   NuppelVideo
ffbmp       ffmpeg    working   FFmpeg BMP decoder  [bmp]
ffgif       ffmpeg    working   FFmpeg GIF decoder  [gif]
fftiff      ffmpeg    untested  FFmpeg TIFF decoder  [tiff]
ffpng       ffmpeg    working   FFmpeg PNG decoder  [png]
mpng        mpng      working   PNG image decoder  [libpng]
fftga       ffmpeg    untested  FFmpeg TGA decoder  [targa]
mtga        mtga      working   TGA image decoder
sgi         sgi       working   SGI image decoder
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
lzo         lzo       working   LZO compressed  [liblzo]
theora      theora    working   Theora (free, reworked VP3)  [libtheora]
cram        vfw       problems  Microsoft Video 1  [msvidc32.dll]
ffcvid      ffmpeg    working   Cinepak Video (native codec)  [cinepak]
cvidvfw     vfw       working   Cinepak Video  [iccvid.dll]
huffyuv     vfw       problems  HuffYUV  [huffyuv.dll]
ffvideo1    ffmpeg    working   Microsoft Video 1 (native codec)  [msvideo1]
ffmszh      ffmpeg    working   AVImszh (native codec)  [mszh]
ffzlib      ffmpeg    working   AVIzlib (native codec)  [zlib]
cvidxa      xanim     problems  XAnim's Radius Cinepak Video  [vid_cvid.xa]
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
ffdivx      ffmpeg    working   FFmpeg DivX ;-) (MS MPEG-4 v3)  [msmpeg4]
ffmp42      ffmpeg    working   FFmpeg M$ MPEG-4 v2  [msmpeg4v2]
ffmp41      ffmpeg    working   FFmpeg M$ MPEG-4 v1  [msmpeg4v1]
ffwmv1      ffmpeg    working   FFmpeg M$ WMV1/WMV7  [wmv1]
ffwmv2      ffmpeg    problems  FFmpeg M$ WMV2/WMV8  [wmv2]
ffwmv3      ffmpeg    problems  FFmpeg M$ WMV3/WMV9  [wmv3]
ffvc1       ffmpeg    problems  FFmpeg M$ WVC1  [vc1]
ffh264      ffmpeg    working   FFmpeg H.264  [h264]
ffsvq3      ffmpeg    working   FFmpeg Sorenson Video v3 (SVQ3)  [svq3]
ffodivx     ffmpeg    working   FFmpeg MPEG-4  [mpeg4]
ffwv1f      ffmpeg    working   WV1F MPEG-4  [mpeg4]
xvid        xvid      working   XviD (MPEG-4)  [libxvidcore.a]
divx4vfw    vfw       problems  DivX4Windows-VFW  [divx.dll]
divxds      dshow     working   DivX ;-) (MS MPEG-4 v3)  [divx_c32.ax]
divx        vfw       working   DivX ;-) (MS MPEG-4 v3)  [divxc32.dll]
mpeg4ds     dshow     working   Microsoft MPEG-4 v1/v2  [mpg4ds32.ax]
mpeg4       vfw       working   Microsoft MPEG-4 v1/v2  [mpg4c32.dll]
wmv8        dshow     working   Windows Media Video 8  [wmv8ds32.ax]
wmv7        dshow     working   Windows Media Video 7  [wmvds32.ax]
wmv9dmo     dmo       working   Windows Media Video 9 DMO  [wmv9dmod.dll]
wmvdmo      dmo       working   Windows Media Video DMO  [wmvdmod.dll]
wmvadmo     dmo       working   Windows Media Video Adv DMO  [wmvadvd.dll]
wmvvc1dmo   dmo       working   Windows Media Video (VC-1) Advanced Profile Decoder  [wvc1dmod.dll]
wmsdmod     dmo       working   Windows Media Screen Codec 2  [wmsdmod.dll]
ubmp4       vfw       problems  UB Video MPEG-4  [ubvmp4d.dll]
zrmjpeg     zrmjpeg   problems  Zoran MJPEG passthrough
ffmjpeg     ffmpeg    working   FFmpeg MJPEG decoder  [mjpeg]
ffmjpegb    ffmpeg    working   FFmpeg MJPEG-B decoder  [mjpegb]
ijpg        ijpg      working   Independent JPEG Group's codec  [libjpeg]
m3jpeg      vfw       working   Morgan Motion JPEG Codec  [m3jpeg32.dll]
mjpeg       vfw       working   MainConcept Motion JPEG  [mcmjpg32.dll]
avid        vfw       working   AVID Motion JPEG  [AvidAVICodec.dll]
LEAD        vfw       working   LEAD (M)JPEG  [LCodcCMP.dll]
imagepower  vfw       problems  ImagePower MJPEG2000  [jp2avi.dll]
m3jpeg2k    vfw       working   Morgan MJPEG2000  [m3jp2k32.dll]
m3jpegds    dshow     crashing  Morgan MJPEG  [m3jpegdec.ax]
pegasusm    vfw       crashing  Pegasus Motion JPEG  [pvmjpg21.dll]
pegasusl    vfw       crashing  Pegasus lossless JPEG  [pvljpg20.dll]
pegasusmwv  vfw       crashing  Pegasus Motion Wavelet 2000  [pvwv220.dll]
vivo        vfw       working   Vivo H.263  [ivvideo.dll]
u263        dshow     working   UB Video H.263/H.263+/H.263++ Decoder  [ubv263d+.ax]
i263        vfw       working   I263  [i263_32.drv]
ffi263      ffmpeg    working   FFmpeg I263 decoder  [h263i]
ffh263      ffmpeg    working   FFmpeg H.263+ decoder  [h263]
ffzygo      ffmpeg    untested  FFmpeg ZyGo  [h263]
h263xa      xanim     crashing  XAnim's CCITT H.263  [vid_h263.xa]
ffh261      ffmpeg    working   CCITT H.261  [h261]
qt261       qtvideo   working   QuickTime H.261 video decoder  [QuickTime.qts]
h261xa      xanim     problems  XAnim's CCITT H.261  [vid_h261.xa]
m261        vfw       untested  M261  [msh261.drv]
indeo5ds    dshow     working   Intel Indeo 5  [ir50_32.dll]
indeo5      vfwex     working   Intel Indeo 5  [ir50_32.dll]
indeo4      vfw       working   Intel Indeo 4.1  [ir41_32.dll]
indeo3      vfwex     working   Intel Indeo 3.1/3.2  [ir32_32.dll]
indeo5xa    xanim     working   XAnim's Intel Indeo 5  [vid_iv50.xa]
indeo4xa    xanim     working   XAnim's Intel Indeo 4.1  [vid_iv41.xa]
indeo3xa    xanim     working   XAnim's Intel Indeo 3.1/3.2  [vid_iv32.xa]
qdv         dshow     working   Sony Digital Video (DV)  [qdv.dll]
ffdv        ffmpeg    working   FFmpeg DV decoder  [dvvideo]
libdv       libdv     working   Raw DV decoder (libdv)  [libdv.so.2]
mcdv        vfw       working   MainConcept DV Codec  [mcdvd_32.dll]
3ivXxa      xanim     working   XAnim's 3ivx Delta 3.5 plugin  [vid_3ivX.xa]
3ivX        dshow     working   3ivx Delta 4.5  [3ivxDSDecoder.ax]
rv3040      realvid   working   Linux RealPlayer 10 RV30/40 decoder  [drvc.so]
rv3040win   realvid   working   Win32 RealPlayer 10 RV30/40 decoder  [drvc.dll]
rv40        realvid   working   Linux RealPlayer 9 RV40 decoder  [drv4.so.6.0]
rv40win     realvid   working   Win32 RealPlayer 9 RV40 decoder  [drv43260.dll]
rv40mac     realvid   working   Mac OS X RealPlayer 9 RV40 decoder  [drvc.bundle/Contents/MacOS/drvc]
rv30        realvid   working   Linux RealPlayer 8 RV30 decoder  [drv3.so.6.0]
rv30win     realvid   working   Win32 RealPlayer 8 RV30 decoder  [drv33260.dll]
rv30mac     realvid   working   Mac OS X RealPlayer 9 RV30 decoder  [drvc.bundle/Contents/MacOS/drvc]
ffrv20      ffmpeg    working   FFmpeg RV20 decoder  [rv20]
rv20        realvid   working   Linux RealPlayer 8 RV20 decoder  [drv2.so.6.0]
rv20winrp10 realvid   working   Win32 RealPlayer 10 RV20 decoder  [drv2.dll]
rv20win     realvid   working   Win32 RealPlayer 8 RV20 decoder  [drv23260.dll]
rv20mac     realvid   working   Mac OS X RealPlayer 9 RV20 decoder  [drv2.bundle/Contents/MacOS/drv2]
ffrv10      ffmpeg    working   FFmpeg RV10 decoder  [rv10]
alpary      dshow     working   Alparysoft lossless codec dshow  [aslcodec_dshow.dll]
alpary2     vfw       working   Alparysoft lossless codec vfw  [aslcodec_vfw.dll]
LEADMW20    dshow     working   Lead CMW wavelet 2.0  [LCODCCMW2E.dll]
ffvp3       ffmpeg    untested  FFmpeg VP3  [vp3]
fftheora    ffmpeg    untested  FFmpeg Theora  [theora]
vp3         vfwex     working   On2 Open Source VP3 Codec  [vp31vfw.dll]
vp4         vfwex     working   On2 VP4 Personal Codec  [vp4vfw.dll]
ffvp5       ffmpeg    working   FFmpeg VP5 decoder  [vp5]
vp5         vfwex     working   On2 VP5 Personal Codec  [vp5vfw.dll]
ffvp6       ffmpeg    working   FFmpeg VP6 decoder  [vp6]
ffvp6f      ffmpeg    working   FFmpeg VP6 Flash decoder  [vp6f]
vp6         vfwex     working   On2 VP6 Personal Codec  [vp6vfw.dll]
vp7         vfwex     working   On2 VP7 Personal Codec  [vp7vfw.dll]
mwv1        vfw       working   Motion Wavelets  [icmw_32.dll]
asv2        vfw       working   ASUS V2  [asusasv2.dll]
asv1        vfw       working   ASUS V1  [asusasvd.dll]
ffultimotion ffmpeg    working   IBM Ultimotion native decoder  [ultimotion]
ultimotion  vfw       working   IBM Ultimotion  [ultimo.dll]
mss1        dshow     working   Windows Screen Video  [msscds32.ax]
ucod        vfw       working   UCOD-ClearVideo  [clrviddd.dll]
vcr2        vfw       working   ATI VCR-2  [ativcr2.dll]
CJPG        vfw       working   CJPG  [CtWbJpg.DLL]
ffduck      ffmpeg    working   Duck Truemotion1  [truemotion1]
fftm20      ffmpeg    working   FFmpeg Duck/On2 TrueMotion 2.0  [truemotion2]
tm20        dshow     working   TrueMotion 2.0  [tm20dec.ax]
ffamv       ffmpeg    working   Modified MJPEG, used in AMV files  [amv]
ffsp5x      ffmpeg    working   SP5x codec - used by Aiptek MegaCam  [sp5x]
sp5x        vfw       working   SP5x codec - used by Aiptek MegaCam  [sp5x_32.dll]
vivd2       vfw       working   SoftMedia ViVD V2 codec VfW  [ViVD2.dll]
winx        vfwex     working   Winnov Videum winx codec  [wnvwinx.dll]
ffwnv1      ffmpeg    working   FFmpeg wnv1 native codec  [wnv1]
wnv1        vfwex     working   Winnov Videum wnv1 codec  [wnvplay1.dll]
vdom        vfw       working   VDOWave codec  [vdowave.drv]
lsv         vfw       working   Vianet Lsvx Video Decoder  [lsvxdec.dll]
ffvmnc      ffmpeg    working   FFmpeg VMware video  [VMware video]
vmnc        vfw       working   VMware video  [vmnc.dll]
ffsmkvid    ffmpeg    working   FFmpeg Smacker Video  [smackvid]
ffcavs      ffmpeg    working   Chinese AVS Video  [cavs]
qt3ivx      qtvideo   working   win32/quicktime 3IV1 (3ivx) decoder  [3ivx Delta 3.5.qtx]
qtavui      qtvideo   working   Win32/QuickTime Avid Meridien Uncompressed  [AvidQTAVUICodec.qtx]
qth263      qtvideo   crashing  Win32/QuickTime H.263 decoder  [QuickTime.qts]
qtrlerpza   qtvideo   crashing  Win32/Quicktime RLE/RPZA decoder  [QuickTime.qts]
qtvp3       qtvideo   crashing  Win32/QuickTime VP3 decoder  [On2_VP3.qtx]
qtzygo      qtvideo   problems  win32/quicktime ZyGo decoder  [ZyGoVideo.qtx]
qtbhiv      qtvideo   untested  Win32/QuickTime BeHereiVideo decoder  [BeHereiVideo.qtx]
qtcvid      qtvideo   working   Win32/QuickTime Cinepak decoder  [QuickTime.qts]
qtindeo     qtvideo   crashing  Win32/QuickTime Indeo decoder  [QuickTime.qts]
qtmjpeg     qtvideo   crashing  Win32/QuickTime MJPEG decoder  [QuickTime.qts]
qtmpeg4     qtvideo   crashing  Win32/QuickTime MPEG-4 decoder  [QuickTime.qts]
qtsvq3      qtvideo   working   Win32/QuickTime SVQ3 decoder  [QuickTimeEssentials.qtx]
qtsvq1      qtvideo   problems  Win32/QuickTime SVQ1 decoder  [QuickTime.qts]
vsslight    vfw       working   VSS Codec Light  [vsslight.dll]
vssh264     dshow     working   VSS H.264 New  [vsshdsd.dll]
vssh264old  vfw       working   VSS H.264 Old  [vssh264.dll]
vsswlt      vfw       working   VSS Wavelet Video Codec  [vsswlt.dll]
zlib        vfw       working   AVIzlib  [avizlib.dll]
mszh        vfw       working   AVImszh  [avimszh.dll]
alaris      vfwex     crashing  Alaris VideoGramPiX  [vgpix32d.dll]
vcr1        vfw       crashing  ATI VCR-1  [ativcr1.dll]
pim1        vfw       crashing  Pinnacle Hardware MPEG-1  [pclepim1.dll]
qpeg        vfw       working   Q-Team's QPEG (www.q-team.de)  [qpeg32.dll]
rricm       vfw       crashing  rricm  [rricm.dll]
ffcamtasia  ffmpeg    working   TechSmith Camtasia Screen Codec (native)  [camtasia]
camtasia    vfw       working   TechSmith Camtasia Screen Codec  [tsccvid.dll]
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
xan         vfw       working   XAN Video  [xanlib.dll]
ffwc3       ffmpeg    problems  FFmpeg XAN wc3  [xan_wc3]
ffidcin     ffmpeg    problems  FFmpeg Id CIN video  [idcinvideo]
ffinterplay ffmpeg    problems  FFmpeg Interplay Video  [interplayvideo]
ffvqa       ffmpeg    problems  FFmpeg VQA Video  [vqavideo]
ffc93       ffmpeg    problems  FFmpeg C93 Video  [c93]
rawrgb32    raw       working   RAW RGB32
rawrgb24    raw       working   RAW RGB24
rawrgb16    raw       working   RAW RGB16
rawbgr32flip raw       working   RAW BGR32
rawbgr32    raw       working   RAW BGR32
rawbgr24flip raw       working   RAW BGR24
rawbgr24    raw       working   RAW BGR24
rawbgr16flip raw       working   RAW BGR15
rawbgr16    raw       working   RAW BGR15
rawbgr15flip raw       working   RAW BGR15
rawbgr15    raw       working   RAW BGR15
rawbgr8flip raw       working   RAW BGR8
rawbgr8     raw       working   RAW BGR8
rawbgr1     raw       working   RAW BGR1
rawyuy2     raw       working   RAW YUY2
rawuyvy     raw       working   RAW UYVY
raw444P     raw       working   RAW 444P
raw422P     raw       working   RAW 422P
rawyv12     raw       working   RAW YV12
rawnv21     hmblck    working   RAW NV21
rawnv12     hmblck    working   RAW NV12
rawhm12     hmblck    working   RAW HM12
rawi420     raw       working   RAW I420
rawyvu9     raw       working   RAW YVU9
rawy800     raw       working   RAW Y8/Y800
null        null      crashing  NULL codec (no decoding!)

```

---

### Post by wolfen69 on 2008-09-04
> **gandaran said:**
> mplayer plugin is not very good for online streaming, sometimes works sometimes not, I suggest you find another player and plugin that you like in synaptic, there are many much better than mplayer, remove mplayer plugin (you can keep only the player if you prefer) before installing other player plugin.

why are you spreading FUD? i've installed mplayer plugin on every ubuntu install i've done,(many) and it works great. many people use it with great success.

---

### Post by wolfen69 on 2008-09-04
go to synaptic and completely remove mozilla-mplayer and mplayer. then open a terminal and:```
sudo apt-get clean
```then ```
sudo apt-get autoremove
``` then ```
sudo apt-get install mozilla-mplayer
``` make sure firefox is closed during this process.

---

### Post by gandaran on 2008-09-04
> **wolfen69 said:**
> why are you spreading FUD? i've installed mplayer plugin on every ubuntu install i've done,(many) and it works great. many people use it with great success.

then why I and many users have problems with mplayer?
look I don't want to enter into a player plugin war, but I just want to say that any player plugin based on xine engine is a lot superior to mplayer, vlc or mplayer clones for online embedded streaming.

---

### Post by gollybegully on 2008-09-04
> **wolfen69 said:**
> go to synaptic and completely remove mozilla-mplayer and mplayer. then open a terminal and:```
sudo apt-get clean
```then ```
sudo apt-get autoremove
``` then ```
sudo apt-get install mozilla-mplayer
``` make sure firefox is closed during this process.

Hey, it worked!  there's an odd 10sec delay that wasnt there before but cant complain. Not quite sure it's better than sex, but at least i can watch porn now. haha!

---

