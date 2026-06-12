---
title: "AMR-WB Codec"
date: 2009-11-16
forum: Multimedia Software
---

### Post by yester64 on 2009-11-16
Hi,
i am trying to change a codec on a movie, but appearently i am missing a codec to the movie.
Its a amr-wb codec. How do i get this codec so i can work on the movie?
I tried already to follow a guide ([HOWTO: Install and use the latest FFmpeg and x264 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=786095&highlight=amr-wb") ) and to recompile ffmpeg, but i still don't have the codec.
also i am missing AC3. what a bummer.
Using Karmic 64bit.

I forgot to mention that i am using Avidemux. Its only in that program, in the player they work but i need to convert them so i can play them on the xbox.

---

### Post by andrew.46 on 2009-11-17
Hi yester,

> **yester64 said:**
> i am trying to change a codec on a movie, but appearently i am missing a codec to the movie. Its a amr-wb codec. How do i get this codec so i can work on the movie? I tried already to follow a guide ([HOWTO: Install and use the latest FFmpeg and x264 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=786095&highlight=amr-wb") ) and to recompile ffmpeg, but i still don't have the codec.

I believe that FakeOutdoorsman is working on an update that will include the *libopencore-amr* libraries so perhaps a post to his guide might give you an advance preview of the upcoming work?

All the best,

Andrew

---

### Post by yester64 on 2009-11-17
I just have to clarify that it appears to be a avidemux problem. At least so i am guessing.
In a videoplayer the files play, but once you want to load it into avidemux it says that it does not have the codec, or more precise that 'a' codec is missing.

So strange. The only reason why i mentioned the codec amr-wb is that it shows up under properties in avidemux.

I will keep an eye on that.

---

### Post by mc4man on 2009-11-17
I believe avidemux uses it's own ffmpeg libraries, if so, then amr support probably isn't enabled in them.

---

### Post by andrew.46 on 2009-11-17
Hi yester64,

> **yester64 said:**
> I just have to clarify that it appears to be a avidemux problem. [...] The only reason why i mentioned the codec amr-wb is that it shows up under properties in avidemux.

Oops, my apologies for misunderstanding your question :oops:.

Andrew

---

### Post by yester64 on 2009-11-17
:)
no problem. Since i can't figure out what the error really is i try a different program out.
I am trying it now with Live.

btw. i checked the forum and it says something about using older versions. mmm..
if it does use its own libraries than that is kinda bad. I checked that as well, but haven't gotten positiv results. Such a shame, since its a nice program.

---

### Post by andrew.46 on 2009-11-17
Hi yester64,

> **yester64 said:**
> btw. i checked the forum and it says something about using older versions. mmm..

Looks like the newest version 2.5.1 supports amr *decoding*:

[http://fixounet.free.fr/avidemux/news.html#2009-08-16](http://fixounet.free.fr/avidemux/news.html#2009-08-16)

> 
* AMR-WB audio decoding support using opencore-amrwb


Might be worth a look?

Andrew

---

### Post by yester64 on 2009-11-17
> **andrew.46 said:**
> Hi yester64,



Looks like the newest version 2.5.1 supports amr *decoding*:

[http://fixounet.free.fr/avidemux/news.html#2009-08-16](http://fixounet.free.fr/avidemux/news.html#2009-08-16)



Might be worth a look?

Andrew


Mm.. i checked my version (karmic) and its 2.5.1. So in theory it should have it. then i checked in the plugins and it is not present.
under Audio: LibMad, LibAC3, Faad2 & libVorbis
and under Audio Decoder: MP2 LavCodec, Faac AAC, Lame MP3, Vorbis, PCM, AC3, TwoLame MP2

Mm.. i am just getting into all that. I have to check their forum again. Perhaps i have to download it from their website.

Thx for the tip :)

---

### Post by andrew.46 on 2009-11-17
Hi yester64,

> **yester64 said:**
> Mm.. i checked my version (karmic) and its 2.5.1. So in theory it should have it. then i checked in the plugins and it is not present.

Looks like [the packagers]("http://changelogs.ubuntu.com/changelogs/pool/multiverse/a/avidemux/avidemux_2.5.1+repack-0ubuntu2/changelog") have removed it:

```
avidemux (1:2.5.0-0.0ubuntu1) karmic; urgency=low

  * Merge with debian-multimedia, Ubuntu remaining changes:
    - debian/{control,rules}:
      + Drop ccache support.
  **[COLOR="Red"]* Remove libopencore-amrnb-dev build-dependency.[/COLOR]**
  * Refresh avidemux-compile.patch.
```

Well, that solves the mystery, the solution would be to repackage the program and restore the libopencore-amrnb-dev build dependency. Do you have any experience with this?

Andrew

---

### Post by yester64 on 2009-11-17
> **andrew.46 said:**
> Hi yester64,



Looks like [the packagers]("http://changelogs.ubuntu.com/changelogs/pool/multiverse/a/avidemux/avidemux_2.5.1+repack-0ubuntu2/changelog") have removed it:
[snip]Andrew

Not really, but i have to get into it anyway. So i rather learn it now.
btw. is there any lecture you can recommend for deeper linux know how. I got me awhile back 'Beginnig Linux' which was ok but did not deep enough.
I like to learn more do all these things. My plan was to master linux :rolleyes:

---

### Post by andrew.46 on 2009-11-17
Hi yester64,

> **yester64 said:**
> Not really, but i have to get into it anyway. So i rather learn it now.

Hmmm... I have had a look at this package and I cannot see clearly how they have excluded ac3 and amr, both of which appear to ship in the original tarball. mc4man might be our guide here perhaps?

> btw. is there any lecture you can recommend for deeper linux know how. I got me awhile back 'Beginnig Linux' which was ok but did not deep enough.
I like to learn more do all these things. My plan was to master linux :rolleyes:

For the most part my 2 best friends have been Trial and Error :).

Andrew

---

### Post by mc4man on 2009-11-17
It appears, from a quick build, that you can restore the codecs. Something along the lines of an apt-get build-dep and apt-get source avidemux, fill in your missing -dev's and build. ( I used the debian/rules, can't comment on a straight build. ( though there may be issues with gcc-4.4 without using the rules, can't say

If you have the -dev libraries installed then they will be detected and support enabled.

Small example from build log ( a fairly long build and large log
```

- Checking for FAAD
-- *****************
-- Found faad.h
-- Found faad library
-- Could not find faacDecInit in /usr/lib/libfaad.so
-- Found NeAACDecInit in /usr/lib/libfaad.so
-- Found FAAD

-- Checking for LIBVORBIS
-- *******************
-- Found vorbis/codec.h
-- Found vorbis library
-- Found vorbis_synthesis_init in /usr/lib/libvorbis.so
-- Found LIBVORBIS

-- Checking for opencore-amrnb
-- ***************************
-- Found opencore-amrnb/interf_dec.h
-- Found opencore-amrnb library
-- Found Decoder_Interface_init in /usr/lib/libopencore-amrnb.so
-- Found opencore-amrnb

-- Checking for opencore-amrwb
-- ***************************
-- Found opencore-amrwb/dec_if.h
-- Found opencore-amrwb library
-- Found D_IF_init in /usr/lib/libopencore-amrwb.so
-- Found opencore-amrwb

```

What will come up is you'll need to match your libx264 headers with the avidemux source.
I have atm headers from libx264-76 installed on this box and support was not built. I'd assume for the karmic repo source that the karmic repo libx264-dev should work ( though there is never 'for sure' in terms of x264. I'd think you'd definitely  need a 67 version 

> ***    SUMMARY    ***
*********************
   GTK+        Yes
   Qt 4        Yes
*** Miscellaneous ***
   gettext     Yes
   SDL         Yes
   XVideo      Yes
*********************
*** Release Build ***
*********************
***  Audio Codec  ***
  [COLOR="Blue"] Aften       No[/COLOR]
   LAME        Yes
   FAAC        Yes
   Vorbis      Yes
***  /Audio Codec  ***
*************************
***      SUMMARY      ***
*************************
***    Video Codec    ***
   [COLOR="Blue"]x264            No[/COLOR]
   Xvid            Yes
***    Audio Codec    ***
   FAAD            Yes
   opencore-amrnb  Yes
   opencore-amrwb  Yes
***   Miscellaneous   ***
   FontConfig      Yes
   FreeType2       Yes
   gettext         Yes



While there is no specific entry for ac3/a52, there were enough entries to assume support is enabled

The bigger question would be I guess,  does then build work? I haven't installed, nor have ever used. The large number of "dpkg-shlibdeps: warning:" would be of some concern, though a good chance they don't affect the app or install.

Edit : the repo libx264-dev works fine, aften doesn't seem to be recognized, ..?

> -- Found x264
--   core version: 67 

> -- Found Aften
-- Warning: Unable to determine Aften version - support for Aften will be turned off

---

### Post by FakeOutdoorsman on 2009-11-18
> **andrew.46 said:**
> Hi yester,



I believe that FakeOutdoorsman is working on an update that will include the *libopencore-amr* libraries so perhaps a post to his guide might give you an advance preview of the upcoming work?

All the best,

Andrew

I started working on this yesterday.  It shouldn't be taking me this long to get it done since all I have to do is copy and paste from Andrew's guide.  Just kidding, but it's not far from the truth.  I've just been debating with myself how to present the guide without it getting too cluttery.  I was also going back and forth with the idea of splitting Karmic from Intrepid and Jaunty.  Yes, I think I will do that now that *libopencore-amr*b-dev* is in the repo.  I just have to do some re-organization, a few test runs, and then it should be ready for an update.

---

### Post by yester64 on 2009-11-18
> **andrew.46 said:**
> Hi yester64,

Hmmm... I have had a look at this package and I cannot see clearly how they have excluded ac3 and amr, both of which appear to ship in the original tarball. mc4man might be our guide here perhaps?

For the most part my 2 best friends have been Trial and Error :).
Andrew

lol... but i still get me some additional lecture.

---

### Post by yester64 on 2009-11-18
> **mc4man said:**
> 

Edit : the repo libx264-dev works fine, aften doesn't seem to be recognized, ..?

Let me check if i have it on.
I will post soon.

---

### Post by yester64 on 2009-11-18
> **FakeOutdoorsman said:**
> I started working on this yesterday.  It shouldn't be taking me this long to get it done since all I have to do is copy and paste from Andrew's guide.  Just kidding, but it's not far from the truth.  I've just been debating with myself how to present the guide without it getting too cluttery.  I was also going back and forth with the idea of splitting Karmic from Intrepid and Jaunty.  Yes, I think I will do that now that *libopencore-amr*b-dev* is in the repo.  I just have to do some re-organization, a few test runs, and then it should be ready for an update.

Nice, i am looking forward to it. :)

---

### Post by yester64 on 2009-11-18
> **mc4man said:**
> It appears, from a quick build, that you can restore the codecs. Something along the lines of an apt-get build-dep and apt-get source avidemux, fill in your missing -dev's and build. ( I used the debian/rules, can't comment on a straight build. ( though there may be issues with gcc-4.4 without using the rules, can't say


Here is what Avidemux tells me

```
joerg@joerg-desktop:~$ avidemux
*************************
  Avidemux v2.5.1
*************************
 http://www.avidemux.org
 Code      : Mean, JSC, Gruntster 
 GFX       : Nestor Di , nestordi@augcyl.org
 Design    : Jakub Misak
 FreeBSD   : Anish Mistry, amistry@am-productions.biz
 Audio     : Mihail Zenkov
 MacOsX    : Kuisathaverat
 Win32     : Gruntster

Compiler: GCC 4.4.1
Build Target: Linux (x86-64)
User Interface: GTK+ (2.18.3)

Large file available: 1 offset

Initialising prefs
Directory /home/joerg/.avidemux exists.Good.
Using /home/joerg/.avidemux as base directory for prefs/jobs/...
Preferences found and loaded
[cpuCaps]Checking CPU capabilities
        MMX detected 
        MMXEXT detected 
        SSE detected 
        SSE2 detected 
        SSE3 detected 
        SSSE3 detected 
[cpuCaps]End of CPU capabilities check (cpuMask :ffffffff)

 Registering Encoders
*********************
MJPEG encoder registered
FFmpeg encoder registered

2 encoder(s) registered

[SDL] Version: 1.2.13
[SDL] Initialisation succeeded
[SDL] Video Driver: x11


[Locale] setlocale de_DE.UTF-8
[Locale] Textdomain was messages
[Locale] Textdomain is now avidemux
[Locale] Files for avidemux appear to be in /usr/share/locale
[Locale] Test: _Datei

Initializing Dithering tables
[COREUI] Compiled with 01.00.01
[COREUI] Linked with   01.00.01
[CoreUI] Compiled with patch version 1, using 1
Initializing postproc
Deleting post proc
updating post proc
Enabled type:3 strength:3

 Registering Internal Filters
******************************

[ADM_ad_plugin] Scanning directory /usr/lib/ADM_plugins/audioDecoder/
[ADM_ad_plugin] Plugin loaded version 0.0.1, name libADM_ad_Mad.so, desc: LibMad decoder plugin for avidemux (c) Mean

[ADM_ad_plugin] Plugin loaded version 0.0.1, name libADM_ad_a52.so, desc: LibAC3 decoder plugin for avidemux (c) Mean

[ADM_ad_plugin] Plugin loaded version 0.0.1, name libADM_ad_faad.so, desc: Faad2 decoder plugin for avidemux (c) Mean

[ADM_ad_plugin] Plugin loaded version 0.0.1, name libADM_ad_vorbis.so, desc: libVorbis decoder plugin for avidemux (c) Mean

[ADM_ad_plugin] Scanning done, found 4 codec
[ADM_vf_plugin] Scanning directory /usr/lib/ADM_plugins/videoFilter/
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_lavDeinterlace.so as  libavcodec deinterlacer
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_FluxSmooth.so as  FluxSmooth
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vidChromaV.so as  Chroma V
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_addborders.so as  Add black borders
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_dropOut.so as  Drop
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_blendRemoval.so as  Blend Removal
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_fastconvolutionmedian.so as  Median
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Mosaic.so as  mosaic
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_keepEvenField.so as  Keep even fields
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Crop_gtk.so as  Crop
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_forcedPP.so as  Forced postprocessing
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Whirl.so as  Whirl
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_telecide.so as  Decomb Telecide
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Stabilize.so as  Light denoiser.
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_blendDgBob.so as  DG Bob
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_hue_gtk.so as  MPlayer hue
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_eq2_gtk.so as  MPlayer eq2
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_cnr2_gtk.so as  Cnr2
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_separateField.so as  Fade
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Tisophote.so as  TIsophote
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_unstackField.so as  Unstack fields
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_contrast_qt4.so]: libADM_UIQT4.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_contrast_qt4.so:nogetdesc
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_crop_qt4.so]: libADM_UIQT4.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_crop_qt4.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_mpdelogo_gtk.so as  MPlayer delogo
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Pulldown.so as  Pulldown
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_blackenBorders.so as  Blacken borders
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_eq2_qt4.so]: libADM_UIQT4.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_eq2_qt4.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_tdeint.so as  TDeint
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Denoise.so as  Denoise
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_mplayerResize_gtk.so as  MPlayer resize
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_stackField.so as  Stack fields
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_chromaShift_gtk.so as  Chroma shift
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_fade.so as  Fade
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_fastconvolutiongauss.so as  Gauss smooth
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_equalizer_qt4.so]: libADM_UIQT4.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_equalizer_qt4.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_decimate.so as  Decomb Decimate
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_chromaShift_qt4.so]: libADM_UIQT4.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_chromaShift_qt4.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_kernelDeint.so as  KernelDeint
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_mSmooth.so as  MSmooth by Donald Graft
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_ssa.so as  ***
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_smartPalShift.so as  PAL smart
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_sub_gtk.so as  Subtitler
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_contrast_gtk.so as  Contrast
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Deinterlace.so as  Deinterlace
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_avisynthResize_qt4.so]: libADM_UIQT4.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_avisynthResize_qt4.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_equalizer_gtk.so as  Luma equalizer
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_mcdeint.so as  mcDeinterlace
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_denoise3d.so as  MPlayer denoise3d
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_lumaonly.so as  Luma only
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_avisynthResize_gtk.so as  Resize
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_fastconvolutionmean.so as  Mean
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vidChromaU.so as  Chroma U
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_hue_qt4.so]: libADM_UIQT4.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_hue_qt4.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_denoise3dhq.so as  MPlayer hqdn3d
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_soften.so as  Soften
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_fastconvolutionsharpen.so as  Sharpen
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_mSharpen.so as  MSharpen
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_colorYUV_gtk.so as  Avisynth ColorYUV
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_palShift.so as  PAL field shift
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_rotate.so as  Rotate
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_largemedian.so as  Median (5x5)
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_reverse.so as  Reverse
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_resampleFps.so as  Resample fps
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_smartSwapField.so as  Smart swap fields
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_vflip.so as  Vertical flip
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_cnr2_qt4.so]: libADM_UIQT4.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_cnr2_qt4.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_keepOddField.so as  Keep odd fields
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_asharp_gtk.so as  asharp
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_hzStackField.so as  separatefields
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_yadif.so as  yadif
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_swapuv.so as  Swap U and V
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_mergeField.so as  Merge fields
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_mplayerResize_qt4.so]: libADM_UIQT4.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_mplayerResize_qt4.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Delta.so as  Luma delta
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_mpdelogo_qt4.so]: libADM_UIQT4.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_mpdelogo_qt4.so:nogetdesc
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_sub_qt4.so]: libADM_UIQT4.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_sub_qt4.so:nogetdesc
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_colorYUV_qt4.so]: libADM_UIQT4.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_colorYUV_qt4.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_vlad.so as  Temporal Cleaner
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_swapField.so as  Swap fields
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_asharp_qt4.so]: libADM_UIQT4.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_asharp_qt4.so:nogetdesc
[ADM_vf_plugin] Scanning done
[ADM_av_plugin] Scanning directory /usr/lib/ADM_plugins/audioDevices/
Name :Oss ApiVersion :1
[Filters] Registered filter /usr/lib/ADM_plugins/audioDevices//libADM_av_oss.so as  Oss audio device (c) mean
Name :Alsa ApiVersion :1
[Filters] Registered filter /usr/lib/ADM_plugins/audioDevices//libADM_av_alsa.so as  Alsa audio device (c) mean
Name :Sdl ApiVersion :1
[Filters] Registered filter /usr/lib/ADM_plugins/audioDevices//libADM_av_sdl.so as  Sdl audio device (c) mean
Symbol loading failed for /usr/lib/ADM_plugins/audioDevices//libADM_av_jack.so
/usr/lib/ADM_plugins/audioDevices//libADM_av_jack.so:CannotLoad
[ADM_av_plugin] Scanning done
[ADM_ae_plugin] Scanning directory /usr/lib/ADM_plugins/audioEncoders/
[AudioEncoder] Loaded LavMP2 version 01.00.00 wavTag :0x50
[AudioEncoder] Registered filter /usr/lib/ADM_plugins/audioEncoders//libADM_ae_lav_mp2.so as  MP2 LavCodec encoder plugin Mean 2008
[AudioEncoder] Loaded Faac version 01.00.00 wavTag :0xff
[AudioEncoder] Registered filter /usr/lib/ADM_plugins/audioEncoders//libADM_ae_faac.so as  Faac AAC encoder plugin Mean 2008
[AudioEncoder] Loaded Lame version 01.00.00 wavTag :0x55
[AudioEncoder] Registered filter /usr/lib/ADM_plugins/audioEncoders//libADM_ae_lame.so as  Lame MP3 encoder plugin Mean 2008
[AudioEncoder] Loaded Vorbis version 01.00.00 wavTag :0x676f
[AudioEncoder] Registered filter /usr/lib/ADM_plugins/audioEncoders//libADM_ae_vorbis.so as  Vorbis encoder plugin Mean 2008
[AudioEncoder] Loaded PCM version 01.00.00 wavTag :0x1
[AudioEncoder] Registered filter /usr/lib/ADM_plugins/audioEncoders//libADM_ae_pcm.so as  PCM encoder plugin Mean 2008
[AudioEncoder] Loaded LavAC3 version 01.00.00 wavTag :0x2000
[AudioEncoder] Registered filter /usr/lib/ADM_plugins/audioEncoders//libADM_ae_lav_ac3.so as  AC3 LavEncoder encoder plugin Mean 2008
[AudioEncoder] Loaded TwoLame version 01.00.00 wavTag :0x50
[AudioEncoder] Registered filter /usr/lib/ADM_plugins/audioEncoders//libADM_ae_twolame.so as  TwoLame MP2 encoder plugin Mean 2008
[ADM_ae_plugin] Scanning done
[ADM_ad_plugin] Scanning directory /home/joerg/.avidemux/plugins/audioDecoder/
[ADM_ad_plugin] Cannot parse plugin
[ADM_vf_plugin] Scanning directory /home/joerg/.avidemux/plugins/videoFilter/
[ADM_vf_plugin] Cannot parse plugin
[ADM_vidEnc_plugin] Scanning directory /usr/lib/ADM_plugins/videoEncoder/
ignored: avcodec
ignored: xvid
ignored: x264
[ADM_vidEnc_plugin] Plugin loaded version 1.0.0, filename libADM_vidEnc_avcodec.so, desc: DV video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Plugin loaded version 1.0.0, filename libADM_vidEnc_avcodec.so, desc: FFV1 video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Plugin loaded version 1.0.0, filename libADM_vidEnc_avcodec.so, desc: FFVHuff video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Plugin loaded version 1.0.0, filename libADM_vidEnc_avcodec.so, desc: Huffyuv video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Plugin loaded version 1.0.1, filename libADM_vidEnc_x264.so, desc: x264 video encoder plugin for Avidemux (c) Mean/Gruntster
[Xvid] Initialising Xvid
[Xvid] Build: xvid-1.1.2
[Xvid] SIMD supported: (cf)
        MMX
        MMXEXT
        SSE
        SSE2
        ALTIVEC
[ADM_vidEnc_plugin] Plugin loaded version 1.0.1, filename libADM_vidEnc_xvid.so, desc: Xvid video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Scanning done, found 6 codec
Found 19 video encoder
Found 8 audio encoder
Found 0 Copy audio encoder
Found 1 MP2 (lav) audio encoder
Found 2 AAC (Faac) audio encoder
Found 3 MP3 (lame) audio encoder
Found 4 Vorbis audio encoder
Found 5 PCM audio encoder
Found 6 AC3 (lav) audio encoder
Found 7 MP2 (Twolame) audio encoder
[AudioEncoder] Selected copy for index 0, tag 0x6ff0530 
Found 13 Format 
Directory /home/joerg/.avidemux/custom/ exists.Good.
No custom script
Found 0 custom scripts, adding them
Menu built
The screen seems to be 1440 x 900 px
/dev/input/event0: Permission denied
/dev/input/event1: Permission denied
/dev/input/event2: Permission denied
/dev/input/event3: Permission denied
/dev/input/event4: Permission denied
/dev/input/event5: Permission denied
/dev/input/event6: Permission denied
No physical Jog/Shuttle device found.
Spidermonkey initialized.
No crash file (/home/joerg/.avidemux/crash.js)


```

---

### Post by FakeOutdoorsman on 2009-11-18
> **yester64 said:**
> Nice, i am looking forward to it. :)

Updated with the **libopencore-amr** stuff:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

It was a rush job, so it may not be perfect.  Too many distractions, not enough Ubuntu.

**Update:** It appears this only allows amr-nb decoding/encoding and amr-wb decoding.  No encoding for amr-wb?  Or is it the other way around?  I already shut down the virtual machine.  I'll have to take a look at this later in the week.

---

### Post by yester64 on 2009-11-18
> **FakeOutdoorsman said:**
> Updated with the **libopencore-amr** stuff:

[HOWTO: Install and use the latest FFmpeg and x264]("http://ubuntuforums.org/showthread.php?t=786095")

It was a rush job, so it may not be perfect.  Too many distractions, not enough Ubuntu.

**Update:** It appears this only allows amr-nb decoding/encoding and amr-wb decoding.  No encoding for amr-wb?  Or is it the other way around?  I already shut down the virtual machine.  I'll have to take a look at this later in the week.

I thank you very much :)
I have to learn that too.

---

### Post by yester64 on 2009-11-18
> **FakeOutdoorsman said:**
> Updated with the **libopencore-amr** stuff:

[HOWTO: Install and use the latest FFmpeg and x264]("http://ubuntuforums.org/showthread.php?t=786095")

It was a rush job, so it may not be perfect.  Too many distractions, not enough Ubuntu.

**Update:** It appears this only allows amr-nb decoding/encoding and amr-wb decoding.  No encoding for amr-wb?  Or is it the other way around?  I already shut down the virtual machine.  I'll have to take a look at this later in the week.

Just to let you know. I think it did not work.
avidemux still has problems with the codec. I will try it again tomorrow, perhaps i did a mistake. So i want to clarify that before i commit.

---

### Post by mc4man on 2009-11-18
Avidemux doesn't use your ffmpeg/ffmpeg libs, *it uses it's own internal one.* The only significant difference from what you posted and from a self built avidemux is this

> Registering Internal Filters
******************************

[ADM_ad_plugin] Scanning directory /usr/lib/ADM_plugins/audioDecoder/
[ADM_ad_plugin] Plugin loaded version 0.0.1, name libADM_ad_Mad.so, desc: LibMad decoder plugin for avidemux (c) Mean

[ADM_ad_plugin] Plugin loaded version 0.0.1, name libADM_ad_vorbis.so, desc: libVorbis decoder plugin for avidemux (c) Mean

[ADM_ad_plugin] Plugin loaded version 0.0.1, name libADM_ad_faad.so, desc: Faad2 decoder plugin for avidemux (c) Mean

[ADM_ad_plugin] Plugin loaded version 1.0.0, name libADM_ad_opencore_amrnb.so, desc: opencore-amrnb decoder plugin for Avidemux (c) Mean/Gruntster

[ADM_ad_plugin] Plugin loaded version 1.0.0, name libADM_ad_opencore_amrwb.so, desc: opencore-amrwb decoder plugin for Avidemux (c) Mean/Gruntster

[ADM_ad_plugin] Plugin loaded version 0.0.1, name libADM_ad_a52.so, desc: LibAC3 decoder plugin for avidemux (c) Mean

[ADM_ad_plugin] Scanning done, found [COLOR="Blue"]6 codec[/COLOR]

Note that the extent of amr support is to decode, which it will do fine, there is no encoding with amr possible

Edit; the reluctance of ubuntu to include opencore-amr support where possible (ffmpeg, avidemux, players that use libavcodec, ect. is somewhat a mystery here, will be interesting to see if that happens in 10.04

---

### Post by yester64 on 2009-11-18
> **mc4man said:**
> Avidemux doesn't use your ffmpeg/ffmpeg libs, *it uses it's own internal one.* The only significant difference from what you posted and from a self built avidemux is this


Thats a bummer. So essentially i can not use Avidemux to decode it.
I will try it with Live and see how it goes. That program does load audio.

---

