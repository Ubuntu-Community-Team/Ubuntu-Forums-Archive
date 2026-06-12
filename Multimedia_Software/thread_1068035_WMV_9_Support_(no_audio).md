---
title: "WMV 9 Support? (no audio)"
date: 2009-02-12
forum: Multimedia Software
---

### Post by DPic on 2009-02-12
I get no sound in WMV 9 files. Video works find but there is no sounds. I am using 64 bit Ubuntu with the gstreamer codecs installed. 

What's the best way to get this working?

---

### Post by cotcot on 2009-02-12
All other apps using sound closed ? If you have some apps using sound open it could happen that other apps do not get access to the sound server anymore.

---

### Post by ouija on 2009-02-12
I've been trying to figure this out myself.

From what I've read, there are no native 64bit codecs that work with Ubuntu AMD64.  I've seen articles stating that using a 32-bit version of Mplayer and the w32codecs will allow for WMV9 playback, but after many attempts I have failed in getting that to work.

I actually think the problem is that I am trying to playback a WMV10 file, which is basically a High Definition WMV file that uses the VC-1 video codec and WMV10 for the audio.  It is not DRM, just a bluray rip that I have for playback on my XBOX 360.

I managed to get video playback using mplayer 64-bit, but received the following error: cannot find codec for audio format 0x162.

Totem doesn't play the file period.

So my understanding is that there is no WMV10 audio codec support for Ubuntu amd64 versions.

However, I did stumble across Fluendo's site in my searches: [http://www.fluendo.com/shop/product/complete-set-of-playback-plugins/](http://www.fluendo.com/shop/product/complete-set-of-playback-plugins/)

Apparently they are offering a codec pack for Ubuntu which will provide support for WMV10 and VC-1.   Unfortunately, this comes at a price -- and I am too cheap and stubborn to purchase it myself (thus far, anyways)

If you're really wanting to get playback working, I'd suggest purchasing that codec pack (and posting your results in this forum if and when you do!)

---

### Post by Debuggern on 2009-03-12
Maybe my post has the solution for your wmv with no sound problem. Give it a try! Good luck!

[http://ubuntuforums.org/showpost.php?p=6880834&postcount=9](http://ubuntuforums.org/showpost.php?p=6880834&postcount=9)

---

### Post by DPic on 2009-03-30
Even VLC doesn't work. I don't understand that since VLC doesn't depend on gstreamer. Actually, i don't even understand why this is only a problem for 64-bit, or is it a problem for 32-bit as well?

---

### Post by peepingtom on 2009-03-30
Install w32codecs or w64codecs and try to play it in mplayer. VLC doesn't interface with win32 codecs and gstreamer uses a different method for loading only specific win32 codecs. If it won't play in mplayer with windows binary codecs, it won't play on Linux.

---

### Post by mc4man on 2009-03-30
> i don't even understand why this is only a problem for 64-bit, or is it a problem for 32-bit as well? 

It's only a problem on 32 bit to the extent of using vlc, there are some wma files it can't play (wmal, most wmap

The difference is other players can, notably mplayer and amarok (based on having w32codecs or win32codecs installed.

Also on a 32 bit install wmal and wmap can be converted to wma2 or otherwise which most players can handle (32 or 64 bit

The easiest way to playback wmap or wmal on a 64 bit install is to install wine and run the windows mplayer from it (note run, not install, also does fairly decent job on playback of wmv with wmap or wmal audio (wmv3

see here (# 15
[http://ubuntuforums.org/showthread.php?t=911880&page=2](http://ubuntuforums.org/showthread.php?t=911880&page=2)

---

### Post by DPic on 2009-03-30
> **peepingtom said:**
> Install w32codecs or w64codecs and try to play it in mplayer. VLC doesn't interface with win32 codecs and gstreamer uses a different method for loading only specific win32 codecs. If it won't play in mplayer with windows binary codecs, it won't play on Linux.

Tried it, no dice =[

---

### Post by DPic on 2009-03-30
Windows Media Player 10 works in wine. I've successfully got it installed and running using the how-to on this page: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3212](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3212)

But, when i try to play the file, it says that a codec is needed and i should click "web help" to download it, but clicking that does nothing and i don't know where to go for the codecs. Does anyone think they can figure out how to get this working from here?

---

### Post by mc4man on 2009-03-30
You may try this, noting that I run 32 bit.
Using either foobar 2000 or the portable vlc player for win.(portable apps) I was unable to playback wma lossless or pro 

I installed this version of windows media runtime files and now can play wma lossless (16 and 24 bit) and the couple of wma3 (pro) audio samples I have in both players thru wine.

[http://downloads.phpnuke.org/lv/software/download/kl77.htm?lang=en](http://downloads.phpnuke.org/lv/software/download/kl77.htm?lang=en)

When installing uncheck those 'php' checkboxes.

Whether this will help Windows Media Player 10 I don't know, but certainly enabled the capability for the players I could test with.


Edit; 
For wmv i'd go with the mplayer option if wmp doesn't work. Though I was able to play a high def wmv3 with the portable vlc it's not to be recommended (though a 0.8.6 version, if found, may work better than a .0.9.x ver.

---

### Post by DPic on 2009-03-30
> **mc4man said:**
> You may try this, noting that I run 32 bit.
Using either foobar 2000 or the portable vlc player for win.(portable apps) I was unable to playback wma lossless or pro 

I installed this version of windows media runtime files and now can play wma lossless (16 and 24 bit) and the couple of wma3 (pro) audio samples I have in both players thru wine.

[http://downloads.phpnuke.org/lv/software/download/kl77.htm?lang=en](http://downloads.phpnuke.org/lv/software/download/kl77.htm?lang=en)

When installing uncheck those 'php' checkboxes.

Whether this will help Windows Media Player 10 I don't know, but certainly enabled the capability for the players I could test with.


Edit; 
For wmv i'd go with the mplayer option if wmp doesn't work. Though I was able to play a high def wmv3 with the portable vlc it's not to be recommended (though a 0.8.6 version, if found, may work better than a .0.9.x ver.

I downloaded that codec pack and it installed but i was still unable to play the file (same results). Is there a newer one available directly from microsoft?

---

### Post by mc4man on 2009-03-30
Possibly wmp 10 can't use the '9 series' of runtime files. 
There is this but I'm not sure it'll install into wine (won't here but I don't have wmp

[http://www.softpedia.com/progDownload/Windows-Media-Format-Runtime-11-Download-40238.html](http://www.softpedia.com/progDownload/Windows-Media-Format-Runtime-11-Download-40238.html)

If you wished to test the ones you did install (see screen to ck. in system32, highlighted are the runtime .dll's) maybe install foobar2000 and load a track
The basic operation of foobar2000 is quite simple, to get fuller use there are many threads elsewhere. (drag and drop doesn't work, use file -> add file

Screen 2 shows foobar playing a particularly 'tough' wma (24 bit, 88200 hz, 2359 kbps ( the pink floyd is a lossless wma, the beethoven is wma pro - all play

[http://www.foobar2000.org/](http://www.foobar2000.org/)


I have another idea, will take a little work later on a tester. (find all the .dll's on my vista box, transfer to wine's system32, register, install wmp10 and see.
Did you use winetricks to install wmp10?

---

### Post by DPic on 2009-03-30
> **mc4man said:**
> Possibly wmp 10 can't use the '9 series' of runtime files. 
There is this but I'm not sure it'll install into wine (won't here but I don't have wmp

[http://www.softpedia.com/progDownload/Windows-Media-Format-Runtime-11-Download-40238.html](http://www.softpedia.com/progDownload/Windows-Media-Format-Runtime-11-Download-40238.html)

If you wished to test the ones you did install (see screen to ck. in system32, highlighted are the runtime .dll's) maybe install foobar2000 and load a track
The basic operation of foobar2000 is quite simple, to get fuller use there are many threads elsewhere. (drag and drop doesn't work, use file -> add file

Screen 2 shows foobar playing a particularly 'tough' wma (24 bit, 88200 hz, 2359 kbps ( the pink floyd is a lossless wma, the beethoven is wma pro - all play

[http://www.foobar2000.org/](http://www.foobar2000.org/)


I have another idea, will take a little work later on a tester. (find all the .dll's on my vista box, transfer to wine's system32, register, install wmp10 and see.
Did you use winetricks to install wmp10?

After installing those runtime files, the clip doesn't ask for a codec, but it says it's playing (but i see no picture and hear no sound), and after about 7 seconds i got an error (which i can't reproduce, so i don't know what it said). Either way, when i try to play the file WMP starts to eat my memory, shows no picture, has no sound, and doesn't play steadily (the seconds don't go up steadily). Foobar is just for audio, but i'm trying to play a video clip

Yes, winetricks was necessary to install wmp10

---

### Post by mc4man on 2009-03-31
Installed wmp10 on an old tester and while it's underpowered (p4 2.4) there was no real problem with wmv3.
The audio played back right away, initially tried some hd nasa clips and there was no video. Added ffdshow and directx and the video played, though poorly. 
Using some less demanding wmv3 from mplayerhq, they played fine, though the cpu usage was high (60 -70 %

wma lossless audio files played fine also (high cpu - 40+%

In comparison the win gmplayer played all the clips fine with lower cpu (35 - 50% for wmv3., 10 - 15% for lossless and wma3 audio. 

All of the needed wma .dll's installed with wmp10

some samples used (r.click, save link as

[http://www.nasa.gov/multimedia/hd/index.html](http://www.nasa.gov/multimedia/hd/index.html)
(480p, 720p

[http://samples.mplayerhq.hu/V-codecs/WMV9/](http://samples.mplayerhq.hu/V-codecs/WMV9/)
(halo

[http://samples.mplayerhq.hu/A-codecs/WMA9/wmapro/](http://samples.mplayerhq.hu/A-codecs/WMA9/wmapro/)
(wmvhdsplash

[http://www.linnrecords.com/linn-downloads-testfiles.aspx](http://www.linnrecords.com/linn-downloads-testfiles.aspx)

(when i put together a new box i'm definitely going to have a dual boot 64/32

---

### Post by northwestuntu on 2009-03-31
is there any ideas as to when we will get 64bit support on this? i am having the same problem not being able to get audio.

---

### Post by mc4man on 2009-04-01
Another option for 64 bit for wmv9 with wmal, wmap audio may be to use 'realplayer'

---

### Post by mc4man on 2009-04-08
Actually there is now a patch for the 64 bit mplayer to allow playback of wma3 (pro) and wmv3  (will not play wma lossless

Hopefully someone like rvm (smplayer) will provide a patched mplayer build.

Tested by building mplayer off of a live cd (amd_64), works fine
Tested on the WMVHCsplash.wmv and a wma3 audio file (the wmv played great even though no video drivers installed because of being on live cd

The patch details are here (post of nullack
[http://ubuntuforums.org/showthread.php?t=1081070&page=10](http://ubuntuforums.org/showthread.php?t=1081070&page=10)

Ex.

> MPlayer SVN-r29151-4.3.2 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing test4.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV3]  1280x720  24bpp  1000.000 fps  6500.0 kbps (793.5 kbyte/s)

==========================================================================
Requested video codec family [wmv9dmo] (vfm=dmo) not available.
Enable it at compilation.
Requested video codec family [wmvdmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg WMV3/WMV9)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
[wmapro @ 0xd73d00][18] [0] [3f] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [e0] [0] [0] [0] 
[wmapro @ 0xd73d00] ed sample bit depth = 16
[wmapro @ 0xd73d00] ed decode flags = e0
[wmapro @ 0xd73d00] samples per frame = 2048
[wmapro @ 0xd73d00] log2 frame size = 17
[wmapro @ 0xd73d00] max num subframes = 16
[wmapro @ 0xd73d00] len prefix = 1
[wmapro @ 0xd73d00] num channels = 6
[wmapro @ 0xd73d00] lossless = 0
AUDIO: 48000 Hz, 6 ch, s16le, 384.0 kbit/8.33% (ratio: 48000->576000)
[COLOR="Red"]Selected audio codec: [ffwmapro] afm: ffmpeg (FFmpeg WMA Pro audio)[/COLOR]
==========================================================================
AO: [alsa] 48000Hz 6ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 1280 x 720 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [x11] 1280x720 => 1280x720 Planar YV12 
[swscaler @ 0xe28680]using unscaled yuv420p -> rgb32 special converter
A:  18.3 V:  18.3 A-V:  0.000 ct:  0.114 369/369 15% 72%  1.2% 18 0 
Exiting... (Quit)


While on the live cd did build a proper though vanilla Intrepid amd_64 mplayer .deb set that should work with any intrepid install (with a min. of libx264-65), available to test,  (pm if wanting link, inadvertently left internal libdvdcss2 enabled, won't post publicly
Also avail. a package set for hardy amd_64 (mplayer, mplayer docs, mencoder

---

### Post by DPic on 2009-05-17
Seems like the easiest thing is to get the Fluendo codec pack which you can get legally (for $40) or illegally (for free):

[http://shop.canonical.com/product_info.php?products_id=244](http://shop.canonical.com/product_info.php?products_id=244)
[http://thepiratebay.org/torrent/4900791](http://thepiratebay.org/torrent/4900791)

---

### Post by logos34 on 2009-05-26
> **mc4man said:**
> Possibly wmp 10 can't use the '9 series' of runtime files. 
There is this but I'm not sure it'll install into wine (won't here but I don't have wmp

[http://www.softpedia.com/progDownload/Windows-Media-Format-Runtime-11-Download-40238.html](http://www.softpedia.com/progDownload/Windows-Media-Format-Runtime-11-Download-40238.html)


that worked for me (wmapro and wma lossless, 16- and 24-bit, playback in foobar)

---

### Post by logos34 on 2009-05-26
> **mc4man said:**
> Another option for 64 bit for wmv9 with wmal, wmap audio may be to use 'realplayer'

that too works for me...audio only, that is...but it chokes on wmv3 video with wmapro soundtrack (green screen, stuttering)

---

### Post by logos34 on 2009-05-26
> **mc4man said:**
> Actually there is now a patch for the 64 bit mplayer to allow playback of wma3 (pro) and wmv3  (will not play wma lossless

...

Tested by building mplayer off of a live cd (amd_64), works fine
Tested on the WMVHCsplash.wmv and a wma3 audio file (the wmv played great even though no video drivers installed because of being on live cd

The patch details are here (post of nullack
[http://ubuntuforums.org/showthread.php?t=1081070&page=10](http://ubuntuforums.org/showthread.php?t=1081070&page=10)

...

Also avail. a package set for hardy amd_64 (mplayer, mplayer docs, mencoder

This is exactly what I need for my x64 8.04 Heron...Not clear, though, on steps to patch in nullack's post...can I apply it to the repo version of mplayer i have?

---

### Post by mc4man on 2009-05-26
> can I apply it to the repo version of mplayer i have? 

No, your going to have to patch, then build mplayer. If you've read back a bit in this post it's a bit of hit or miss thing, more hit than miss.

I just quickly built a patched svn a few moments ago to test, no issues.

MPlayer SVN-r29324, wmapro revision 4315

If you wanted to quickly grab the sources and patch, then create a folder and cd to it

```

svn checkout svn://svn.mplayerhq.hu/mplayer/trunk svn
```
```
cd svn && svn checkout svn://svn.ffmpeg.org/soc/wmapro wmapro
```
```
 cp wmapro/wma* libavcodec
```
```
patch -p0 <wmapro/audioframesize.patch && patch -p0 <wmapro/mplayer.patch && patch -p0 <wmapro/wmapro_ffmpeg.patch
```

Then you could decide how you want to build and what you want to enable, ect. at your leisure.

It's doubtful any hardy repo source will patch (normal or medibuntu), if you were using the smplayer repo than probably will. (if not inclined to use latest svn.


Edit:
andrews guide will work good, or you coild try dbuild using the debian folder that comes in the svn or I could point you to another easy way to do individual packages. (split off mencoder

---

### Post by andrew.46 on 2009-05-26
Hi mc4man,

> **mc4man said:**
> No, your going to have to patch, then build mplayer. If you've read back a bit in this post it's a bit of hit or miss thing, more hit than miss.

I just quickly built a patched svn a few moments ago to test, no issues

Certainly since I started using it a little over a week ago I have experienced clean builds with the 32bit svn MPlayer and the SOC wmapro code. faust 3 is still beavering away at the task too:

```

andrew@skamandros~/source/mplayer/mplayer/wmapro$ svn log -l 6
------------------------------------------------------------------------
r4313 | faust3 | 2009-05-26 06:34:38 +1000 (Tue, 26 May 2009) | 1 line

use get_bits1 instead of get_bits( , 1) 
------------------------------------------------------------------------
r4312 | faust3 | 2009-05-26 06:24:50 +1000 (Tue, 26 May 2009) | 1 line

removed unused negative_quantstep context variable
------------------------------------------------------------------------
r4311 | faust3 | 2009-05-26 06:21:27 +1000 (Tue, 26 May 2009) | 1 line

calculate sf_offsets index only once when assigning the resampled scale factors
------------------------------------------------------------------------
r4310 | faust3 | 2009-05-26 06:13:59 +1000 (Tue, 26 May 2009) | 1 line

avoid divison and modulo operations in wma_inverse_channel_transform
------------------------------------------------------------------------
r4306 | faust3 | 2009-05-25 00:49:10 +1000 (Mon, 25 May 2009) | 1 line

do the runlength switch in the inner most vector decoding loop without an extra condition
------------------------------------------------------------------------
r4304 | faust3 | 2009-05-24 04:04:58 +1000 (Sun, 24 May 2009) | 1 line

get rid of a branch in the run length decoding loop
------------------------------------------------------------------------

```

Andrew

---

### Post by mc4man on 2009-05-26
It certainly seems to be much more reliable atm. The biggest issue was wma3dec.c had #include "bitstream.h", which libavcodec didn't.

Now it seems they're (the patch and ffmpeg)  keeping on same page in that regard.(tonights is #include "get_bits.h", which is in libavcodec

---

### Post by logos34 on 2009-05-27
> **mc4man said:**
> No, your going to have to patch, then build mplayer. If you've read back a bit in this post it's a bit of hit or miss thing, more hit than miss.

I just quickly built a patched svn a few moments ago to test, no issues.

MPlayer SVN-r29324, wmapro revision 4315

If you wanted to quickly grab the sources and patch, then create a folder and cd to it

```

svn checkout svn://svn.mplayerhq.hu/mplayer/trunk svn
```
```
cd svn && svn checkout svn://svn.ffmpeg.org/soc/wmapro wmapro
```
```
 cp wmapro/wma* libavcodec
```
```
patch -p0 <wmapro/audioframesize.patch && patch -p0 <wmapro/mplayer.patch && patch -p0 <wmapro/wmapro_ffmpeg.patch
```

Then you could decide how you want to build and what you want to enable, ect. at your leisure.

It's doubtful any hardy repo source will patch (normal or medibuntu), if you were using the smplayer repo than probably will. (if not inclined to use latest svn.


Edit:
andrews guide will work good,


ok, did all that.  Here's what ./config (bottom)... returns:

> Config files successfully generated by ./configure --codecsdir=/usr/lib/codecs --confdir=/etc/mplayer !

  Install prefix: /usr/local
  Data directory: /usr/local/share/mplayer
  Config direct.: /etc/mplayer

  Byte order: little-endian
  Optimizing for: 

  Languages:
    Messages/GUI: en
    Manual pages: en

  Enabled optional drivers:
    Input: dvdnav(internal) ftp pvr tv-teletext tv-v4l2 tv-v4l tv [COLOR="Red"]live555[/COLOR] cddb cdda libdvdcss(internal) dvdread(internal) vcd dvb smb network 
    Codecs: libschroedinger libdirac [COLOR="Red"]x264[/COLOR] xvid libdv libamr_wb libamr_nb [COLOR="Red"]libavcodec(internal)[/COLOR] real xanim faad2(internal) faac musepack libdca libmpeg2(internal) liba52(internal) mp3lib(internal) libtheora speex tremor(internal) twolame libmad liblzo gif 
    Audio output: alsa openal jack pulse nas esd arts oss v4l2 sdl mpegpes(dvb) 
    Video output: v4l2 dxr3 sdl gif89a pnm jpeg png mpegpes(dvb) fbdev svga caca aa ggi xvidix cvidix dga xv x11 xover dfbmga directfb yuv4mpeg md5sum tga 

  Disabled optional drivers:
    Input: vstream radio tv-dshow nemesi 
    Codecs: qtx [COLOR="Red"]win32[/COLOR] toolame 
    Audio output: sun ivtv dxr2 
    Video output: zr zr2 ivtv dxr2 vesa xmga mga winvidix opengl 3dfx vdpau xvmc bl xvr100 tdfx_vid wii s3fb tdfxfb 

'config.h' and 'config.mak' contain your configuration options.
Note: If you alter theses files (for instance CFLAGS) MPlayer may no longer
      compile *** DO NOT REPORT BUGS if you tweak these files ***

'make' will now compile MPlayer and 'make install' will install it.
Note: On non-Linux systems you might need to use 'gmake' instead of 'make'.

Please check mtrr settings at /proc/mtrr (see DOCS/HTML/en/video.html#mtrr)

[COLOR="Red"]NOTE: Win32 codec DLLs are not supported on your CPU (x86_64) or your
operating system (Linux). You may encounter a few files that cannot
be played due to missing open source video/audio codec support.[/COLOR]

Check configure.log if you wonder why an autodetection failed (make sure
development headers/packages are installed).

NOTE: The --enable-* parameters unconditionally force options on, completely
skipping autodetection. This behavior is unlike what you may be used to from
autoconf-based configure scripts that can decide to override you. This greater
level of control comes at a price. You may have to provide the correct compiler
and linker flags yourself.
If you used one of these options (except --enable-gui and similar ones that
turn on internal features) and experience a compilation or linking failure,
make sure you have passed the necessary compiler/linker flags to configure.

If you suspect a bug, please read DOCS/HTML/en/bugreports.html.

So is that what it should look like?  Is 'libavcodec (internal)' going to pick up the wma*(pro) stuff I copied? 

EDIT: nm, i see it:
> 
[COLOR="Blue"]Checking for RealPlayer codecs ... yes (using /usr/lib/codecs)[/COLOR]
Checking for QuickTime codecs ... auto 
Checking for Nemesi Streaming Media libraries ... no 
[COLOR="Blue"]Checking for LIVE555 Streaming Media libraries ... yes (using /usr/lib/live)[/COLOR]
Checking for FFmpeg libavutil ... yes (static)
[COLOR="Blue"]Checking for FFmpeg libavcodec ... yes (static)[/COLOR]
Checking for FFmpeg libavformat ... yes (static)
Checking for FFmpeg libpostproc ... yes (static)
Checking for FFmpeg libswscale ... yes (static)
Checking for libamr narrowband ... yes 
Checking for libamr wideband ... yes 
Checking for libdv-0.9.5+ ... yes 
Checking for Xvid ... yes 
Checking for Xvid two pass plugin ... yes 
[COLOR="Blue"]Checking for x264 ... yes (in libavcodec: yes)[/COLOR]

I went through ./configure --help options and it appears there's not much to change--practically everything is set for [autodetect]

Oh, and is mplayerplug-in going to be a problem?

thanks again

---

### Post by mc4man on 2009-05-27
The configure looks fine, go ahead and build and see what you get.

The only thing to consider is if you use (s)mplayer for dvd playback and if so do want a dvdnav enabled mplayer (at present config not enabled.

Dvdnav in mplayer works ok, has some possible issues if you have a surround sound set up.
Even if you don't use mplayer with dvdnav there is some small advantage to having it enabled in the build.
Some structured protected titles are unplayable in a mplayer build without dvdnav (fairly rare)

If you wanted it enabled in the build you'd need to add libdvdread4, libdvdread-dev (the 4.1.3-2 version), and upgrade your libdvdnav4 and libdvdnav-dev to 4.1.3-2

Available from here 
[https://launchpad.net/~rvm/+archive/libs](https://launchpad.net/~rvm/+archive/libs)

Install libdvdread4 first, then the other 3, libdvdread3 is unaffected (leave


As far as the plugin best to ask Andrew (I don't stream too much, I don't see any issue though

---

### Post by andrew.46 on 2009-05-27
Hi mc4man,

> **mc4man said:**
> The only thing to consider is if you use (s)mplayer for dvd playback and if so do want a dvdnav enabled mplayer (at present config not enabled.[...] If you wanted it enabled in the build you'd need to add libdvdread4, libdvdread-dev (the 4.1.3-2 version), and upgrade your libdvdnav4 and libdvdnav-dev to 4.1.3-2

Available from here 
[https://launchpad.net/~rvm/+archive/libs](https://launchpad.net/~rvm/+archive/libs)

Install libdvdread4 first, then the other 3, libdvdread3 is unaffected 

I will have to admit that I only use the internal dvdnav, libdvdcss and dvdread and I have had no trouble with dvd menus and playback. So in this respect my ./configure mirrors logos':

```

Enabled optional drivers:
Input: **[COLOR="Purple"]dvdnav(internal)[/COLOR]** ftp pvr tv-teletext tv-v4l2 tv-v4l tv live555 cddb cdda
 **[COLOR="Purple"]libdvdcss(internal)[/COLOR]** **[COLOR="Purple"]dvdread(internal)[/COLOR]** vcd dvb smb network 

```

> As far as the plugin best to ask Andrew (I don't stream too much, I don't see any issue though

I have run this plugin with the svn mplayer for some time with no problems whatsoever.

All the best,

Andrew

---

### Post by logos34 on 2009-05-27
To compile the mplayerplugin I'm using the suggestion here:

> $ ./whatoptions.sh
Run configure with the following options

./configure --prefix=/usr --with-mozilla-home=/usr/lib/iceweasel

except I changed it to the browser I'm using (don't know why it chose iceweasel, which isn't installed, though the folder and mplayerplug-in is there).

But I'm running into this problem:

>  logos34@ubuntu:~/downloads/mplayerplug-in-3.55$./configure --prefix=/usr --with-mozilla-home=/usr/local/swiftweasel

...

configure: Determining mozilla/firefox packages to build against
checking for pkg-config... /usr/bin/pkg-config
checking for mozilla-plugin mozilla-xpcom... configure: WARNING: mozilla-plugin not found
checking for firefox-plugin firefox-xpcom... configure: WARNING: firefox-plugin not found
checking for seamonkey-plugin seamonkey-xpcom... configure: WARNING: seamonkey-plugin not found
checking for xulrunner-plugin xulrunner-xpcom... yes
checking MOZPLUG_CFLAGS... -I/usr/include/xulrunner/java -I/usr/include/xulrunner/plugin -I/usr/include/nspr -I/usr/include/xulrunner -I/usr/include/xulrunner/xpcom -I/usr/include/xulrunner/string  
checking MOZPLUG_LIBS... -L/usr/lib/xulrunner -lxpcom -lplds4 -lplc4 -lnspr4 -lpthread -ldl  
[COLOR="Red"]checking for xpidl... no
configure: error: xpidl compiler not found[/COLOR]

the only thing a search of apt-cache showed up was libmozillainterfaces-java, but it didn't help.

Other x64 Hardy users have had [same issue]("http://groups.google.com/group/gecko-mediaplayer/browse_thread/thread/a52f7cf4bb00de45").

Edit: do I need any gecko-related stuff?  [From this]("http://mplayerplug-in.sourceforge.net/install.php#plugin") I thought it only applied to older versions

I just knew the plugin would cause trouble

---

### Post by logos34 on 2009-05-27
AND I can't even launch mplayer.  Seemed to compile ok:
> 
checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@ubuntu ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ mplayer ]
3 -  Version: [ 3:1.0~svn-r29324 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ svn ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
install -d /usr/local/bin /etc/mplayer /usr/local/lib
install -m 755 -s mencoder /usr/local/bin
install -d /usr/local/share/man/man1
install -m 644 DOCS/man/en/mplayer.1 /usr/local/share/man/man1/
cd /usr/local/share/man/man1 && ln -sf mplayer.1 mencoder.1
install -m 755 -s mplayer /usr/local/bin

======================== Installation successful ==========================

Copying documentation directory...
./
./LICENSE
./Changelog
./README
./AUTHORS
grep: /var/tmp/TiaCnGkSRIRYbLbjfnWUP/newfile: No such file or directory

Copying files to the temporary directory...OK

Stripping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...OK

Transferring package to /home/logos34/Desktop...OK

Erasing temporary files...OK

Deleting doc-pak directory...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /home/logos34/Desktop/mplayer_3:1.0~svn-r29324-1_amd64.deb

 You can remove it from your system anytime using: 

      dpkg -r mplayer

**********************************************************************


---

### Post by andrew.46 on 2009-05-27
Hi logos,

> **logos34 said:**
> AND I can't even launch mplayer.  Seemed to compile ok

Looks like a perfect installation.... is there an error message when you launch it from the commandline?

All the best,

Andrew

---

### Post by mc4man on 2009-05-27
I would defer in terms of the plugin though I'm wondering why your trying to build it. Is there some functionality not in the repo version? (hardy-backports

As far as the mplayer build I'm assuming you followed Andrew's guide which builds a non gui version.
In other words test it from the cli or install smplayer as a gui frontend. The old default gmplayer wasn't/isn't much good anyway

---

### Post by logos34 on 2009-05-27
> **andrew.46 said:**
> Looks like a perfect installation.... is there an error message when you launch it from the commandline?

no, nothing...some hdd light flicker, that's it...htop shows no mplayer process...tried /usr/local/bin/mplayer, terminal and run application box

compiled it a second time...no change

Note: mozilla-plugin works with SVN mplayer installed...so maybe I'll just use that IF I can get mplayer to launch

---

### Post by mc4man on 2009-05-27
If you still have your build folder intact from last build, cd to it and run ./mplayer
Anything show up in the terminal?

---

### Post by logos34 on 2009-05-27
too late, already did distclean

this is a major bummer

---

### Post by mc4man on 2009-05-27
Well if you've a little time on your hands run a ./configure, make and then test with ./mplayer.

or maybe try ./configure --prefix=/usr

---

### Post by logos34 on 2009-05-27
ok, will do

I can't even get it to respond to

mplayer --help

mplayer --version

---

### Post by logos34 on 2009-05-27
ok, I reinstalled the deb and I can play a file directly (wmv3+wmapro yeah! finally)...but just the screen comes up, no gui controls.  

mplayer WMVHDsplash.wmv

with sound now

mplayer New\ Stories\ \(Highway\ Blues\)-1_48kH_288k.wma

thanks for that, mc4man

Why won't it launch?

Great build, andrew46, can't find anything wrong, I mean unless there's errors buried in the make output and not reported at the end.  Hmm.  Even the repo version of mozilla-mplayer works.  Capturing mp3 radio streams works. 

results of 'locate mplayer':

> $ locate mplayer
/etc/mplayer
/etc/mplayerplug-in.conf
/etc/mplayerplug-in.types
/etc/mplayer/input.conf
/etc/mplayer/menu.conf
/etc/mplayer/mplayer.conf
/home/logos34/.mplayer
/home/logos34/m4a2wav-mplayer.sh
/home/logos34/.local/share/applications/mplayer-usercustom-usercustom-usercustom-usercustom-1.desktop
/home/logos34/.local/share/applications/mplayer-usercustom-usercustom-usercustom-usercustom.desktop
/home/logos34/.local/share/applications/mplayer-usercustom-usercustom-usercustom.desktop
/home/logos34/.local/share/applications/mplayer-usercustom-usercustom.desktop
/home/logos34/.local/share/applications/mplayer-usercustom.desktop
/home/logos34/.local/share/applications/mplayer.desktop
/home/logos34/.macromedia/Flash_Player/#SharedObjects/HQ2ZAHAE/www.dailymotion.com/flash/dmplayer
/home/logos34/.macromedia/Flash_Player/#SharedObjects/HQ2ZAHAE/www.dailymotion.com/flash/dmplayer/dmplayer.swf
/home/logos34/.macromedia/Flash_Player/#SharedObjects/HQ2ZAHAE/www.dailymotion.com/flash/dmplayer/dmplayer.swf/dmplayer.sol
/home/logos34/.mplayer/config
/home/logos34/.mplayer/config~
/home/logos34/.mplayer/gui.conf
/home/logos34/.mplayer/gui.history
/home/logos34/.mplayer/gui.pl
/home/logos34/.mplayer/gui.url
/home/logos34/.mplayer/mplayerplug-in.conf
/home/logos34/downloads/mplayer-pulse.patch
/home/logos34/downloads/mplayer-snapshot-0.3
/home/logos34/multimedia/Video/Mplayer/firefox mplayer plugin
/home/logos34/multimedia/Video/Mplayer/mplayer -vc help
/home/logos34/multimedia/Video/Mplayer/mplayer-gui-install.html
/home/logos34/multimedia/Video/Mplayer/mplayer-gui-install_files
/home/logos34/multimedia/Video/Mplayer/mplayer.1.html
/home/logos34/multimedia/Video/Mplayer/mplayer_errors
/home/logos34/multimedia/Video/Mplayer/replace totem w mplayer plugins
/home/logos34/multimedia/Video/Mplayer/mplayer-gui-install_files/default.css
/home/logos34/multimedia/audio/Mplayer/mplayer man page.html
/home/logos34/multimedia/audio/Ripping streams/mplayer - save streams
/home/logos34/pictures/screenshots/mplayer signal13 error.png
/home/logos34/pictures/screenshots/mplayer_inet6.png
/home/logos34/pictures/screenshots/mplayer_mp3codec.png
/usr/bin/gmplayer
/usr/bin/mplayer
/usr/lib/libogmrip-mplayer.so.0
/usr/lib/libogmrip-mplayer.so.0.0.0
/usr/lib/firefox/plugins/mplayerplug-in-dvx.so
/usr/lib/firefox/plugins/mplayerplug-in-dvx.xpt
/usr/lib/firefox/plugins/mplayerplug-in-qt.so
/usr/lib/firefox/plugins/mplayerplug-in-qt.xpt
/usr/lib/firefox/plugins/mplayerplug-in-rm.so
/usr/lib/firefox/plugins/mplayerplug-in-rm.xpt
/usr/lib/firefox/plugins/mplayerplug-in-wmp.so
/usr/lib/firefox/plugins/mplayerplug-in-wmp.xpt
/usr/lib/firefox/plugins/mplayerplug-in.so
/usr/lib/firefox/plugins/mplayerplug-in.xpt
/usr/lib/iceape/plugins/mplayerplug-in-dvx.so
/usr/lib/iceape/plugins/mplayerplug-in-dvx.xpt
/usr/lib/iceape/plugins/mplayerplug-in-qt.so
/usr/lib/iceape/plugins/mplayerplug-in-qt.xpt
/usr/lib/iceape/plugins/mplayerplug-in-rm.so
/usr/lib/iceape/plugins/mplayerplug-in-rm.xpt
/usr/lib/iceape/plugins/mplayerplug-in-wmp.so
/usr/lib/iceape/plugins/mplayerplug-in-wmp.xpt
/usr/lib/iceape/plugins/mplayerplug-in.so
/usr/lib/iceape/plugins/mplayerplug-in.xpt
/usr/lib/iceweasel/plugins/mplayerplug-in-dvx.so
/usr/lib/iceweasel/plugins/mplayerplug-in-dvx.xpt
/usr/lib/iceweasel/plugins/mplayerplug-in-qt.so
/usr/lib/iceweasel/plugins/mplayerplug-in-qt.xpt
/usr/lib/iceweasel/plugins/mplayerplug-in-rm.so
/usr/lib/iceweasel/plugins/mplayerplug-in-rm.xpt
/usr/lib/iceweasel/plugins/mplayerplug-in-wmp.so
/usr/lib/iceweasel/plugins/mplayerplug-in-wmp.xpt
/usr/lib/iceweasel/plugins/mplayerplug-in.so
/usr/lib/iceweasel/plugins/mplayerplug-in.xpt
/usr/lib/mime/packages/mplayer
/usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
/usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
/usr/lib/mozilla/plugins/mplayerplug-in-qt.so
/usr/lib/mozilla/plugins/mplayerplug-in-qt.xpt
/usr/lib/mozilla/plugins/mplayerplug-in-rm.so
/usr/lib/mozilla/plugins/mplayerplug-in-rm.xpt
/usr/lib/mozilla/plugins/mplayerplug-in-wmp.so
/usr/lib/mozilla/plugins/mplayerplug-in-wmp.xpt
/usr/lib/mozilla/plugins/mplayerplug-in.so
/usr/lib/mozilla/plugins/mplayerplug-in.xpt
/usr/lib/transcode/import_mplayer.so
/usr/lib/xulrunner-addons/plugins/mplayerplug-in-dvx.so
/usr/lib/xulrunner-addons/plugins/mplayerplug-in-dvx.xpt
/usr/lib/xulrunner-addons/plugins/mplayerplug-in-qt.so
/usr/lib/xulrunner-addons/plugins/mplayerplug-in-qt.xpt
/usr/lib/xulrunner-addons/plugins/mplayerplug-in-rm.so
/usr/lib/xulrunner-addons/plugins/mplayerplug-in-rm.xpt
/usr/lib/xulrunner-addons/plugins/mplayerplug-in-wmp.so
/usr/lib/xulrunner-addons/plugins/mplayerplug-in-wmp.xpt
/usr/lib/xulrunner-addons/plugins/mplayerplug-in.so
/usr/lib/xulrunner-addons/plugins/mplayerplug-in.xpt
/usr/share/mplayer
/usr/share/app-install/desktop/gnome-mplayer.desktop
/usr/share/app-install/desktop/kmplayer.desktop
/usr/share/app-install/desktop/mozilla-mplayer.desktop
/usr/share/app-install/desktop/mplayer.desktop
/usr/share/app-install/desktop/smplayer.desktop
/usr/share/app-install/icons/gnome-mplayer.png
/usr/share/app-install/icons/mplayer.xpm
/usr/share/app-install/icons/smplayer.png
/usr/share/applications/mplayer.desktop
/usr/share/apps/k9copy/icons/hicolor/48x48/actions/mplayer.png
/usr/share/doc/mozilla-mplayer
/usr/share/doc/mplayer
/usr/share/doc/mplayer-skins
/usr/share/doc/mozilla-mplayer/README
/usr/share/doc/mozilla-mplayer/TODO
/usr/share/doc/mozilla-mplayer/changelog.Debian.gz
/usr/share/doc/mozilla-mplayer/copyright
/usr/share/doc/mplayer/Copyright.gz
/usr/share/doc/mplayer/changelog.Debian.gz
/usr/share/doc/mplayer/changelog.gz
/usr/share/doc/mplayer/copyright
/usr/share/doc/mplayer/examples
/usr/share/doc/mplayer-skins/changelog.Debian.gz
/usr/share/doc/mplayer-skins/copyright
/usr/share/locale/cs/LC_MESSAGES/mplayerplug-in.mo
/usr/share/locale/da/LC_MESSAGES/mplayerplug-in.mo
/usr/share/locale/de/LC_MESSAGES/mplayerplug-in.mo
/usr/share/locale/en_US/LC_MESSAGES/mplayerplug-in.mo
/usr/share/locale/es/LC_MESSAGES/mplayerplug-in.mo
/usr/share/locale/fr/LC_MESSAGES/mplayerplug-in.mo
/usr/share/locale/hu/LC_MESSAGES/mplayerplug-in.mo
/usr/share/locale/it/LC_MESSAGES/mplayerplug-in.mo
/usr/share/locale/ja/LC_MESSAGES/mplayerplug-in.mo
/usr/share/locale/ko/LC_MESSAGES/mplayerplug-in.mo
/usr/share/locale/nl/LC_MESSAGES/mplayerplug-in.mo
/usr/share/locale/pl/LC_MESSAGES/mplayerplug-in.mo
/usr/share/locale/pt_BR/LC_MESSAGES/mplayerplug-in.mo
/usr/share/locale/ru/LC_MESSAGES/mplayerplug-in.mo
/usr/share/locale/se/LC_MESSAGES/mplayerplug-in.mo
/usr/share/locale/sk/LC_MESSAGES/mplayerplug-in.mo
/usr/share/locale/tr/LC_MESSAGES/mplayerplug-in.mo
/usr/share/locale/wa/LC_MESSAGES/mplayerplug-in.mo
/usr/share/locale/zh_CN/LC_MESSAGES/mplayerplug-in.mo
/usr/share/man/man1/gmplayer.1.gz
/usr/share/man/man1/mplayer.1.gz
/usr/share/mimelnk/application/x-mplayer2.desktop
/usr/share/mplayer/skins
/usr/share/mplayer/subfont.ttf
/usr/share/mplayer/skins/Ater
/usr/share/mplayer/skins/clearplayer
/usr/share/mplayer/skins/default
/usr/share/mplayer/skins/mini
/usr/share/mplayer/skins/Ater/README
/usr/share/mplayer/skins/Ater/VERSION
/usr/share/mplayer/skins/Ater/about.png
/usr/share/mplayer/skins/Ater/barfwd.png
/usr/share/mplayer/skins/Ater/barnext.png
/usr/share/mplayer/skins/Ater/barpause.png
/usr/share/mplayer/skins/Ater/barplay.png
/usr/share/mplayer/skins/Ater/barprev.png
/usr/share/mplayer/skins/Ater/barrev.png
/usr/share/mplayer/skins/Ater/barstop.png
/usr/share/mplayer/skins/Ater/eqb.png
/usr/share/mplayer/skins/Ater/exit.png
/usr/share/mplayer/skins/Ater/font-pl.png
/usr/share/mplayer/skins/Ater/font.fnt
/usr/share/mplayer/skins/Ater/forward.png
/usr/share/mplayer/skins/Ater/icons
/usr/share/mplayer/skins/Ater/load.png
/usr/share/mplayer/skins/Ater/main.png
/usr/share/mplayer/skins/Ater/maximize.png
/usr/share/mplayer/skins/Ater/menu.png
/usr/share/mplayer/skins/Ater/menus.png
/usr/share/mplayer/skins/Ater/minimize.png
/usr/share/mplayer/skins/Ater/mute.png
/usr/share/mplayer/skins/Ater/next.png
/usr/share/mplayer/skins/Ater/pause.png
/usr/share/mplayer/skins/Ater/play.png
/usr/share/mplayer/skins/Ater/playbar.png
/usr/share/mplayer/skins/Ater/playlist.png
/usr/share/mplayer/skins/Ater/pos.png
/usr/share/mplayer/skins/Ater/prefs.png
/usr/share/mplayer/skins/Ater/prev.png
/usr/share/mplayer/skins/Ater/progres.png
/usr/share/mplayer/skins/Ater/rev.png
/usr/share/mplayer/skins/Ater/skin
/usr/share/mplayer/skins/Ater/stop.png
/usr/share/mplayer/skins/Ater/subload.png
/usr/share/mplayer/skins/Ater/subpic.png
/usr/share/mplayer/skins/Ater/subvol.png
/usr/share/mplayer/skins/Ater/symbols.fnt
/usr/share/mplayer/skins/Ater/symbols2.png
/usr/share/mplayer/skins/Ater/symbolsg.fnt
/usr/share/mplayer/skins/Ater/volume.png
/usr/share/mplayer/skins/Ater/icons/icon192x192.png
/usr/share/mplayer/skins/Ater/icons/icon32x32.png
/usr/share/mplayer/skins/Ater/icons/icon48x48.png
/usr/share/mplayer/skins/Ater/icons/icon64x64.png
/usr/share/mplayer/skins/Ater/icons/icon96x96.png
/usr/share/mplayer/skins/clearplayer/README
/usr/share/mplayer/skins/clearplayer/VERSION
/usr/share/mplayer/skins/clearplayer/button.png
/usr/share/mplayer/skins/clearplayer/button_forward.png
/usr/share/mplayer/skins/clearplayer/button_load.png
/usr/share/mplayer/skins/clearplayer/button_next.png
/usr/share/mplayer/skins/clearplayer/button_pause.png
/usr/share/mplayer/skins/clearplayer/button_play.png
/usr/share/mplayer/skins/clearplayer/button_prev.png
/usr/share/mplayer/skins/clearplayer/button_rewind.png
/usr/share/mplayer/skins/clearplayer/button_stop.png
/usr/share/mplayer/skins/clearplayer/font.fnt
/usr/share/mplayer/skins/clearplayer/font.png
/usr/share/mplayer/skins/clearplayer/main.png
/usr/share/mplayer/skins/clearplayer/mute.png
/usr/share/mplayer/skins/clearplayer/pos.png
/usr/share/mplayer/skins/clearplayer/skin
/usr/share/mplayer/skins/clearplayer/sub.png
/usr/share/mplayer/skins/clearplayer/vol.png
/usr/share/mplayer/skins/clearplayer/waves.png
/usr/share/mplayer/skins/mini/README
/usr/share/mplayer/skins/mini/VERSION
/usr/share/mplayer/skins/mini/main.png
/usr/share/mplayer/skins/mini/pause.png
/usr/share/mplayer/skins/mini/play.png
/usr/share/mplayer/skins/mini/pos.png
/usr/share/mplayer/skins/mini/skin
/usr/share/mplayer/skins/mini/stop.png
/usr/share/pixmaps/mplayer.xpm
/var/lib/dpkg/info/mozilla-mplayer.conffiles
/var/lib/dpkg/info/mozilla-mplayer.list
/var/lib/dpkg/info/mozilla-mplayer.md5sums
/var/lib/dpkg/info/mplayer-skins.list
/var/lib/dpkg/info/mplayer-skins.md5sums
/var/lib/dpkg/info/mplayer-skins.preinst
/var/lib/dpkg/info/mplayer.conffiles
/var/lib/dpkg/info/mplayer.list
/var/lib/dpkg/info/mplayer.md5sums
/var/lib/dpkg/info/mplayer.postinst
/var/lib/dpkg/info/mplayer.postrm
/var/lib/dpkg/info/mplayer.preinst




---

### Post by mc4man on 2009-05-27
...........................................................................

Edit : removed, missed your post

If you wish a gui get smplayer

---

### Post by logos34 on 2009-05-27
I wasn't using a gui before, just controls with Ater skin. I was happy with that when I used mplayer.  I'm not crazy about smplayer

point is where;s the control display/console thingy and what;s preventing it launching.  I removed mplayer-skins and mencoder, to no avail.

---

### Post by logos34 on 2009-05-27
another oddity: if I use smplayer, I can playback some wmv3+smapro (the nasa clips), but not WMVHDsplash.wmv 

hmm..

When I first call mplayer from cli, as I said the hdd flickers, so it's like it's having trouble finding the libs or soemthing...mc4man, you think just this

./configure --prefix=/usr

might fix it?

---

### Post by mc4man on 2009-05-27
> ....might fix it?
No


Is this screen what you mean by > I wasn't using a gui before, just controls with Ater skin

---

### Post by logos34 on 2009-05-27
> **mc4man said:**
> No


Is this screen what you mean by

exactly,  that's it.


Tried this:

> ./configure [COLOR="Red"]--prefix=/usr[/COLOR] --codecsdir=/usr/lib/codecs --confdir=/etc/mplayer


dpkg -i but fails checkinstall:

> 
logos34@ubuntu:~/svn$ sudo dpkg -i mplayer_3\:1.0~svn-r29324-1_amd64.deb 
(Reading database ... 218236 files and directories currently installed.)
Unpacking mplayer (from mplayer_3:1.0~svn-r29324-1_amd64.deb) ...
dpkg: error processing mplayer_3:1.0~svn-r29324-1_amd64.deb (--install):
 trying to overwrite `/usr/bin/mencoder', which is also in package mencoder
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 mplayer_3:1.0~svn-r29324-1_amd64.deb

Just running the executable from the svn folder:

logos34@ubuntu:~/svn$ ./mplayer

doesn't work either...same thing, a little flicker, then nothing

even removed leftover /usr/bin/mencoder, but same error again when try 

sudo dpkg -i mplayer_3:1.0~svn-r29324-1_amd64.deb

No sense in wasting any more effort on this...it's one problem or another on x64...might go back to 32-bit one of these days).  Guess I'll just go back to repo version of mplayer and use ffplay in the meantime...If I start running into a lot of wmv3+wma3 audio, then I'll come back and troubleshoot (or maybe I'll have found the answer by then).

thanks again

---

### Post by mc4man on 2009-05-27
A couple of 'closing'..? points.

that skin requires a gui enabled mplayer which by default isn't enabled.
(./configure --enable-gui

the flicker I'm not sure, if it's only on a hd video like that sample maybe cpu, video adapter, display driver.

The mencoder thing is a slight issue, either --disable-mencoder in the configure or remove the standalone mencoder first. (see you tried

I get around that by building mplayer as a debian package **set** (separate mplayer, mencoder, doc packages - post 22 screen


> might go back to 32-bit one of these days


I finally relented and installed jaunty on my m1330 laptop (core2duo, 4 gb ram, nividia

After several days of testing I'm dumping jaunty due to what **I** see as a rather poor combo of the kernel, xorg, compiz, as implemented in  jaunty.
I'm gonna start with 8.04 and if no hardware issues go with that . Maybe I'll try the 64 bit version though for A/V 32 bit seems better suited

---

### Post by logos34 on 2009-05-28
> **mc4man said:**
> A couple of 'closing'..? points.

that skin requires a gui enabled mplayer which by default isn't enabled.
(./configure --enable-gui

you're kidding?  it's not?  What do want to bet that's it.  (I hope)
> 
the flicker I'm not sure, if it's only on a hd video like that sample maybe cpu, video adapter, display driver.

I meant hard drive *light* flicker

> The mencoder thing is a slight issue, either --disable-mencoder in the configure or remove the standalone mencoder first. (see you tried 

ok, I'll try it first with default, then disable it and reinstall the repo standalone

wish me luck...

---

### Post by logos34 on 2009-05-28
SUCCESS!  You da man, mc4man! I own you a beer dude

Wow, for a second there I was back in noob-land, groping around...But this is the TICKET:
> 
./configure **--enable-gui** --codecsdir=/usr/lib/codecs --confdir=/etc/mplayer

EXCEPT there's one more step: you have to copy your skins over because it doesn't even include the default clearplayer--just makes an empty folder.  So unless you're going to use smplayer or gmplayer:

> cp /usr/share/mplayer/skins/* /usr/local/share/mplayer/skins

I use Ater (totally cool, I think):

[ATTACH]115423[/ATTACH]
[ATTACH]115425[/ATTACH]
[ATTACH]115424[/ATTACH]

Still can't believe I overlooked the gui option the first time--I was focusing on codecs and A/V output

The first wmv3 video I tried was one of the nasa clips of shuttle launch, and wth these immortal words after liftoff:

"--Roger, roll, Endeavor"

I had image *and* wmap sound. Rock and roll.  Now mplayer works like it should. 

I opted to use the svn mencoder.  Now to reinstall mozilla-mplayer and verify it can play wmap files in the FF browser, like it did when I tested it earlier.

Thanks again, andrew.46!  It works on x64 Hardy.

---

### Post by andrew.46 on 2009-05-28
Hi logos34,

> **logos34 said:**
> Thanks again, andrew.46!  It works on x64 Hardy. 

Glad to hear it is all working. I will admit I don't have the knowledge or the patience that mc4man has with the package management system of Ubuntu :-).

Andrew

---

### Post by logos34 on 2009-05-28
just one final wrinkle:

k9copy, ogmrip, devede and acidrip all have mencoder as dep...They want to install the repo version.  So I thought I'd just build all of them from source (or at least the first two)...Not so easy...some complain about not finding mplayer in path (?), or something else, no matter if I use checkinstall or debuild...argh, getting sick of this...I think I'll compile mplayer ONCE more, this time with --disable-mencoder and go back to medibuntu version.

But doesn't that mean mencoder won't support decoding wmap?  If that's the only diff I can live with it...Had enough fun for one day...

---

### Post by rvm4000 on 2009-05-28
I've just compiled mplayer r29325 with wmapro (r4319). I've tested it with WMVHDsplash.wmv.

Question: isn't the sound a little bit distorted?

And sometimes I've got this error:
> 
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 6 ch, s16le, 384.0 kbit/8.33% (ratio: 48000->576000)
Selected audio codec: [ffwmapro] afm: ffmpeg (FFmpeg WMA Pro audio)
==========================================================================
[AO_ALSA] alsa-lib: pcm_hw.c:1099:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
[AO_ALSA] Playback open error: Device or resource busy
Failed to initialize audio driver 'alsa'


---

### Post by andrew.46 on 2009-05-28
Hi rvm,

> **rvm4000 said:**
> I've just compiled mplayer r29325 with wmapro (r4319). I've tested it with WMVHDsplash.wmv.

Question: isn't the sound a little bit distorted?

Sound is ok here with same revisions but my audio / video setup is pretty minimalist so it would need to be quite a degree of distortion for me to hear :-).

> And sometimes I've got this error:
```

[AO_ALSA] alsa-lib: pcm_hw.c:1099:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
[AO_ALSA] Playback open error: Device or resource busy
Failed to initialize audio driver 'alsa' 

```


Are you running Ubuntu as guest in a virtual machine? In absence of other reasons I sometimes get a similar error if the host is using sound.

Andrew

---

### Post by rvm4000 on 2009-05-28
> **andrew.46 said:**
> Are you running Ubuntu as guest in a virtual machine? In absence of other reasons I sometimes get a similar error if the host is using sound

No, this is a real machine. I don't know why it happens but I've got that problem very often when I try to play a file with wmapro audio, and I lose the sound. Maybe it's a bug in that codec...

BTW, I've just uploaded mplayer svn r29325 with support for wmapro to [https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing) (it's compiling right now).

---

### Post by rvm4000 on 2009-05-28
I've just compiled on another computer (with a 32 bit distro) mplayer r29328 with the wmapro patch.

This time I have no problem at all with the sound, so I guess the "Device or resource busy" problem I had on my laptop must be a driver issue or something.

---

### Post by andrew.46 on 2009-05-28
Hi rvm,

> **rvm4000 said:**
> No, this is a real machine. I don't know why it happens but I've got that problem very often when I try to play a file with wmapro audio, and I lose the sound. Maybe it's a bug in that codec...

I guess since playback is also possible from the MPlayer codecs you could test for ffwmapro problems by running a comparison with:

```
mplayer -ac wma9dmo WMVHDsplash.wmv
```

Although I see that in a later post you suspect your machine itself. Even so it produces an interesting comparison...

Andrew

---

### Post by rvm4000 on 2009-05-28
I'm using a 64bit distro in the machine I have problems, so wma9dmo is not available there.

(Well, unless I compile mplayer in 32bit mode, which is something I have never done)

**Edit:** 
I'm running ubuntu 9.04 (i386) in virtualbox in this machine. Installed mplayer with the wmapro patch.

Well, when using the ffwmapro codec I have the same problem ([AO_ALSA] alsa-lib: pcm_hw.c:1321:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy). If I use instead -ac wma9dmo then the sound plays!

So I thing it's actually a bug in the ffwmapro codec.

---

### Post by andrew.46 on 2009-05-29
Hi mc4man,

> **mc4man said:**
> andrews guide will work good, or you coild try dbuild using the debian folder that comes in the svn or I could point you to another easy way to do individual packages. (split off mencoder

Well actually *I* would appreciate a few pointers on how to accomplish this  as I am after a newer approach for an svn MPlayer guide for Karmic and despite my misgivings about splitting MPlayer up in this way I guess it is the Ubuntu / Debian way. Any guidance you can give would be highly appreciated.

Andrew

---

### Post by mc4man on 2009-05-30
> Well actually I would appreciate a few pointers on how to accomplish this 

In this case (mplayer) rvm4000 would be the one to talk to. What I was going to suggest to logos if the checkinstall way didn't work for some mysterious reason was to use rvm's ./create_deb.sh instead. Only requires a few commands and 30 sec.'s editing

(i see now he's added a wmapro patch, so it may even be easier than several days ago.)

 The only possible issue there would be if a change in libavcodec wasn't reflected in the patch if need be. (if I'm understanding how his patch works
Similar to the bitstream.h to get_bits.h thing.

Anyway (and subject to correction from rvm4000) it would go something like this

Create a working folder (mplayer, mplayer1, whatever) and cd to it

```
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk svn
```

```
wget http://smplayer.svn.sourceforge.net/viewvc/smplayer/mplayer-builds/patches-ubuntu/debian.diff && cd svn


```
```
patch -p0 -E -i ../debian.diff
```

At this point browse to svn/debian-rvm/rules and edit as one see's fit. (very little actually, mplayer for the most part is still  configured from auto-detect and default-enabled
(also would be the time to manually patch if desired, like the wmapro in lieu of the included patch

I just disable cpu runtime detection and then this is the default options as set by the rules
> configuration: --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --disable-libdvdcss-internal --enable-menu --enable-gui --enable-mencoder


If you don't want a dvdnav enabled build then you'd remove what's in red

> #CONFIGURE_INPUT :=  [COLOR="Red"]--disable-dvdread-internal[/COLOR] 
CONFIGURE_INPUT :=  [COLOR="Red"]--disable-libdvdcss-internal[/COLOR]

If you didn't want a gui then rvm will have to chime in, his rules have changed a bit from the last time i saw them, I remember it took a few tries to find the right lines to comment and the ones to uncomment. (or just let it build a gui - in logos case that's what he wanted.

The only other 2 things are the patches and the --enable-xvmc
The enable-xvmc isn't an issue if libxvmc-dev isn't installed, if it is then it may present a problem on hardy. I'd just remove the entry unless one really needed/used it

The patches can be left as is or be disabled individually by removing the entry in 00list. 

If there is a problem with a patch you'll know immediately when starting the build, if so edit out the line in 00list and run ./create_deb.sh again

I'm sure there are 2-3 build packages you need to install, just don't recollect. again the terminal output will tell you right away in clear terms. (look in control file
quilt, dpatch, xsltproc, libxml2-utils, docbook-xml, docbook-xsl ..??

Then simply (still at the svn prompt

```
chmod 755 create_deb.sh && ./create_deb.sh
```

Actually very easy and quick unlike something like vlc which is a bit of a pita to build in package form, particularly on hardy ( but very 'educational' to do so, though a make and make install is still my preferred way.

Edit: I think I remember you mentioning you didn't realize vlc was broken up in debian, screen shows a 0.9.9a package build using  debuild.
The number of packages is somewhat absurd, 5 are needed for the minimum install

---

### Post by andrew.46 on 2009-05-30
Hi mc4man,

Thanks for that. I have again had a look at debian packaging and in particular rvm's work with MPlayer/MEncoder/docs and I will have to admit I cannot warm to this system. But thanks for pointing me in the right direction :-).

Andrew

---

### Post by fillintheblanks on 2009-05-30
can anybody playback this address in mplayer? I can't figure out why it connects in totem-xine but not in mplayer

> mplayer -playlist "http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC1154.wmv&.wvxgg"

Resolving demand.global-mix.net for AF_INET...
Connecting to server demand.global-mix.net[91.193.244.62]: 80...
Cache size set to 320 KBytes
MPlayer SVN-r29328-4.3.3 (C) 2000-2009 MPlayer Team
137 audio & 297 video codecs

Playing [http://o-lon-01.global-mix.net/gmuk-...est=1243614814](http://o-lon-01.global-mix.net/gmuk-...est=1243614814).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-...4&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...

---

### Post by krisku on 2010-05-01
> **Debuggern said:**
> Maybe my post has the solution for your wmv with no sound problem. Give it a try! Good luck!

[http://ubuntuforums.org/showpost.php?p=6880834&postcount=9](http://ubuntuforums.org/showpost.php?p=6880834&postcount=9)

Thanks, this worked nicely for me! However I had installed MPlayer from the svn version with a lot of codecs and development libraries as well. [http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

---

