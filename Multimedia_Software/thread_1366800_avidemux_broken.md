---
title: "avidemux broken"
date: 2009-12-28
forum: Multimedia Software
---

### Post by jomacintosh on 2009-12-28
Hey.  Can't get avidemux to start.  Doesn't even launch.  I'm pretty sour at this point.  It would be a different story if I could get an error message or some glimmer of hope, but nothing.  Why is something that should be very simple so complicated?

---

### Post by VertexPusher on 2009-12-28
To see the error message, open a terminal and start the program from there.

---

### Post by jomacintosh on 2009-12-28
Here is the last few lines.  I can post the entire output, but that is quite long.

[ADM_vidEnc_plugin] Plugin loaded version 1.0.1, filename libADM_vidEnc_xvid.so, desc: Xvid video encoder plugin for Avidemux (c) Mean/Gruntster

*********** BACKTRACK **************
Frame  0: /usr/lib/libADM_core.so(ADM_backTrack+0x68) [0x7fdba704ff28] 
Frame  1: /lib/libc.so.6 [0x7fdba23e4530] 
Frame  2: /usr/lib/libx264.so.67 [0x7fdb8f858faf] 
*********** BACKTRACK **************
Cleaning up
Deleting post proc
Waiting for Spidermonkey to finish...
Cleaning up Spidermonkey.
Segmentation fault

---

### Post by VertexPusher on 2009-12-29
> **jomacintosh said:**
> Here is the last few lines.  I can post the entire output, but that is quite long.

[ADM_vidEnc_plugin] Plugin loaded version 1.0.1, filename libADM_vidEnc_xvid.so, desc: Xvid video encoder plugin for Avidemux (c) Mean/Gruntster
Here's what should have happened after that line:
```
[ADM_vidEnc_plugin] Plugin loaded version 1.0.1, filename libADM_vidEnc_xvid.so, desc: Xvid video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Plugin loaded version 1.0.1, filename libADM_vidEnc_x264.so, desc: x264 video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Plugin loaded version 1.0.0, filename libADM_vidEnc_avcodec.so, desc: DV video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Plugin loaded version 1.0.0, filename libADM_vidEnc_avcodec.so, desc: FFV1 video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Plugin loaded version 1.0.0, filename libADM_vidEnc_avcodec.so, desc: FFVHuff video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Plugin loaded version 1.0.0, filename libADM_vidEnc_avcodec.so, desc: Huffyuv video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Scanning done, found 6 codec
Found 19 video encoder
Found 8 audio encoder
Found 0 Copy audio encoder
Found 1 MP2 (Twolame) audio encoder
Found 2 PCM audio encoder
Found 3 MP2 (lav) audio encoder
Found 4 MP3 (lame) audio encoder
Found 5 Vorbis audio encoder
Found 6 AC3 (lav) audio encoder
Found 7 AAC (Faac) audio encoder
[AudioEncoder] Selected copy for index 0, tag 0x0 
Found 13 Format
```
Obviously the crash happens during initialisation of the x264 plugin. This is quite strange and probably means that one of those library files is broken. Reinstall the following packages

avidemux
avidemux-plugins
libx264-67

and see if that fixes the problem.

---

### Post by jomacintosh on 2009-12-29
No joy.  Uninstalled the pakages listed via Synaptic.  Reboot. Reinstall using synaptic.  Tried clicking the app in the menu, nothing.  tried running the program in terminal, same last few lines.

---

### Post by VertexPusher on 2009-12-29
One more thing you could try is to delete the (hidden) ".avidemux" folder in your user home directory. This will reset Avidemux to factory default settings. If the program continues to crash, I have no idea what could be wrong, sorry.

---

### Post by papaton on 2010-02-19
Hi, it's been some time since this last post was done, but it seems that I also have the same problem here. Avidemux just won't start. It works fine on my PC, but not on my Laptop. Ubuntu = Karmic. Startup stops after segmentation fault.

Has the issue been solved now, and if so, HOW?
Thanks in advance for any help.

Below the last lines of the terminal output...

Frame 15: /lib/ld-linux.so.2 [0x507200] 
Frame 16: /lib/tls/i686/cmov/libdl.so.2 [0x59cc0b] 
Frame 17: /lib/ld-linux.so.2 [0x5034e6] 
Frame 18: /lib/tls/i686/cmov/libdl.so.2 [0x59d09c] 
Frame 19: /lib/tls/i686/cmov/libdl.so.2(dlopen+0x41) [0x59cb41] 
*********** BACKTRACK **************
Cleaning up
Deleting post proc
Waiting for Spidermonkey to finish...
Cleaning up Spidermonkey.
Segmentation fault

---

### Post by YanH on 2010-02-20
Same problem here. Also running Karmic on a laptop.

Also I've deleted the .avidemux folder and this had no effect.

---

### Post by YanH on 2010-02-24
Are there any 9:10 Laptop users who are succesfully using Avidemux?

---

### Post by linuxmess on 2010-04-22
I'm having the same issue with Avidemux. I can't believe how many packages in karmic 64 fail to function.  Seems I spend more time trouble-shooting than getting work done.  

Sadly, my investment in this new laptop will drive me back to windowz, especially when there is so little attention paid to actually putting an operating system in the 64 bit/linux environment that actually works.

Sad indeed.

---

### Post by papaton on 2010-05-28
Hi,
 
I just upgraded from Ubuntu 9.10 to 10.04 LTS and this seems to work. Now avidemux is operational again. Before upgrading I did a fresh install of 9.10 with my favourite applications and avidemux did not work properly. So somehow the problem seems solved with 10.04.
 
Caution however with upgrading. I first had some issues with the login screen (also described in another post: [http://ubuntuforums.org/showthread.php?t=1465827](http://ubuntuforums.org/showthread.php?t=1465827) ). I think this has to do with the graphics card. I have an ATI Radeon card and I think that if you don't have the proprietary driver installed you can get troubles with it. Some solutions have already been found ( [http://ubuntuforums.org/showthread.php?t=1491345](http://ubuntuforums.org/showthread.php?t=1491345) a.o.), but that discussion is for another thread...
 
Regards,
Ton

---

### Post by eival on 2010-10-30
well to that guy above me, im using 10.4 and its not fixed cause neither the version in the repos or the newer version on their site actually run.

and i just installed this OS about a week ago so i should have all the same updates you guys had when you are saying it now works.

EDIT - i figured it out, you just have to run sudo avidemux in the terminal and it registers a bunch of stuff an the player will then open.

now that i think about it, the installer never asked for sudo password, so maybe they forget to add that part, quiet annoying tho cause NOBODY on google knew of this issue or explained it/figured it out.

---

### Post by Ragnar! on 2010-11-11
Well I just upgraded to 10.10 and now avidemux (either flavor) will not launch. I tried the sudo avidemux and this is what I got:```

*************************
  Avidemux v2.5.2
*************************
 http://www.avidemux.org
 Code      : Mean, JSC, Gruntster 
 GFX       : Nestor Di , nestordi@augcyl.org
 Design    : Jakub Misak
 FreeBSD   : Anish Mistry, amistry@am-productions.biz
 Audio     : Mihail Zenkov
 MacOsX    : Kuisathaverat
 Win32     : Gruntster

Compiler: GCC 4.4.3
Build Target: Linux (x86-64)
User Interface: Qt (4.7.0)

Large file available: 1 offset

Initialising prefs
Directory /home/larry/.avidemux exists.Good.
Using /home/larry/.avidemux as base directory for prefs/jobs/...
Preferences found and loaded
[cpuCaps]Checking CPU capabilities
        MMX detected 
        3DNOW detected 
        MMXEXT detected 
        SSE detected 
        SSE2 detected 
        SSE3 detected 
[cpuCaps]End of CPU capabilities check (cpuMask :ffffffff)

 Registering Encoders
*********************
MJPEG encoder registered
FFmpeg encoder registered

2 encoder(s) registered

[SDL] Version: 1.2.14
[SDL] Initialisation succeeded
[SDL] Video Driver: x11

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
[ADM_ad_plugin] Plugin loaded version 0.0.1, name libADM_ad_a52.so, desc: LibAC3 decoder plugin for avidemux (c) Mean

[ADM_ad_plugin] Plugin loaded version 1.0.0, name libADM_ad_opencore_amrwb.so, desc: opencore-amrwb decoder plugin for Avidemux (c) Mean/Gruntster

[ADM_ad_plugin] Plugin loaded version 1.0.0, name libADM_ad_opencore_amrnb.so, desc: opencore-amrnb decoder plugin for Avidemux (c) Mean/Gruntster

[ADM_ad_plugin] Plugin loaded version 0.0.1, name libADM_ad_vorbis.so, desc: libVorbis decoder plugin for avidemux (c) Mean

[ADM_ad_plugin] Plugin loaded version 0.0.1, name libADM_ad_faad.so, desc: Faad2 decoder plugin for avidemux (c) Mean

[ADM_ad_plugin] Plugin loaded version 0.0.1, name libADM_ad_Mad.so, desc: LibMad decoder plugin for avidemux (c) Mean

[ADM_ad_plugin] Scanning done, found 6 codec
[ADM_vf_plugin] Scanning directory /usr/lib/ADM_plugins/videoFilter/
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_fastconvolutionsharpen.so as Sharpen
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_yadif.so as yadif
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vidChromaU.so as Chroma U
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_resampleFps.so as Resample fps
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_keepEvenField.so as Keep even fields
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_mergeField.so as Merge fields
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_Crop_gtk.so]: libADM_UIGtk.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_Crop_gtk.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_curveEditor_qt4.so as Color Curve Editor
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_colorYUV_gtk.so]: libADM_UIGtk.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_colorYUV_gtk.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_mplayerResize_qt4.so as MPlayer resize
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_fastconvolutionmedian.so as Median
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_addborders.so as Add black borders
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_swapuv.so as Swap U and V
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_equalizer_gtk.so]: libADM_UIGtk.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_equalizer_gtk.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_denoise3d.so as MPlayer denoise3d
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_colorYUV_qt4.so as Avisynth ColorYUV
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_eq2_qt4.so as MPlayer eq2
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_mplayerResize_gtk.so]: libADM_UIGtk.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_mplayerResize_gtk.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_equalizer_qt4.so as Luma equalizer
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_largemedian.so as Median (5x5)
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_dropOut.so as Drop
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_mcdeint.so as mcDeinterlace
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_hzStackField.so as Horizontal Stack Field
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_chromaShift_gtk.so]: libADM_UIGtk.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_chromaShift_gtk.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_fade.so as Fade
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Deinterlace.so as Deinterlace
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_ssa.so as ***
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_palShift.so as PAL field shift
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Tisophote.so as TIsophote
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_kernelDeint.so as KernelDeint
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_asharp_qt4.so as asharp
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Mosaic.so as mosaic
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_vlad.so as Temporal Cleaner
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_asharp_gtk.so]: libADM_UIGtk.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_asharp_gtk.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_lavDeinterlace.so as libavcodec deinterlacer
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_stackField.so as Stack fields
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_sub_gtk.so]: libADM_UIGtk.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_sub_gtk.so:nogetdesc
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_cnr2_gtk.so]: libADM_UIGtk.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_cnr2_gtk.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_soften.so as Soften
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_rotate.so as Rotate
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_lumaonly.so as Luma only
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Denoise.so as Denoise
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_unstackField.so as Unstack fields
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_fastconvolutiongauss.so as Gauss smooth
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Stabilize.so as Light denoiser.
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_mpdelogo_gtk.so]: libADM_UIGtk.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_mpdelogo_gtk.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_contrast_qt4.so as Contrast
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_avisynthResize_gtk.so]: libADM_UIGtk.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_avisynthResize_gtk.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Delta.so as Luma delta
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_contrast_gtk.so]: libADM_UIGtk.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_contrast_gtk.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_crop_qt4.so as Crop
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_mSharpen.so as MSharpen
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_smartSwapField.so as Smart swap fields
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Pulldown.so as Pulldown
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_eq2_gtk.so]: libADM_UIGtk.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_eq2_gtk.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_Whirl.so as Whirl
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_sub_qt4.so as Subtitler
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_smartPalShift.so as PAL smart
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_blackenBorders.so as Blacken borders
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_vflip.so as Vertical flip
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_blendDgBob.so as DG Bob
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_hue_qt4.so as MPlayer hue
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_fastconvolutionmean.so as Mean
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_swapField.so as Swap fields
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_separateField.so as Separate Fields
Unable to load [/usr/lib/ADM_plugins/videoFilter//libADM_vf_hue_gtk.so]: libADM_UIGtk.so: cannot open shared object file: No such file or directory
/usr/lib/ADM_plugins/videoFilter//libADM_vf_hue_gtk.so:nogetdesc
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_tdeint.so as TDeint
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_telecide.so as Decomb Telecide
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_avisynthResize_qt4.so as Resize
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_decimate.so as Decomb Decimate
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_forcedPP.so as Forced postprocessing
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_keepOddField.so as Keep odd fields
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_blendRemoval.so as Blend Removal
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_denoise3dhq.so as MPlayer hqdn3d
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_mpdelogo_qt4.so as MPlayer delogo
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_chromaShift_qt4.so as Chroma shift
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_mSmooth.so as MSmooth by Donald Graft
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_cnr2_qt4.so as Cnr2
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_FluxSmooth.so as FluxSmooth
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vidChromaV.so as Chroma V
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_reverse.so as Reverse
[ADM_vf_plugin] Scanning done
[ADM_av_plugin] Scanning directory /usr/lib/ADM_plugins/audioDevices/
Name :PulseAudioS ApiVersion :1
[Filters] Registered filter /usr/lib/ADM_plugins/audioDevices//libADM_av_pulseAudioSimple.so as  PulseAudioSimple audio device (c) mean
Name :Oss ApiVersion :1
[Filters] Registered filter /usr/lib/ADM_plugins/audioDevices//libADM_av_oss.so as  Oss audio device (c) mean
Name :Sdl ApiVersion :1
[Filters] Registered filter /usr/lib/ADM_plugins/audioDevices//libADM_av_sdl.so as  Sdl audio device (c) mean
Name :Esd ApiVersion :1
[Filters] Registered filter /usr/lib/ADM_plugins/audioDevices//libADM_av_esd.so as  Esd audio device (c) mean
Name :Alsa ApiVersion :1
[Filters] Registered filter /usr/lib/ADM_plugins/audioDevices//libADM_av_alsa.so as  Alsa audio device (c) mean
Name :Jack ApiVersion :1
[Filters] Registered filter /usr/lib/ADM_plugins/audioDevices//libADM_av_jack.so as  Jack audio device (c) M. Zenkov 
[ADM_av_plugin] Scanning done
[ADM_ae_plugin] Scanning directory /usr/lib/ADM_plugins/audioEncoders/
[AudioEncoder] Loaded Lame version 01.00.00 wavTag :0x55
[AudioEncoder] Registered filter /usr/lib/ADM_plugins/audioEncoders//libADM_ae_lame.so as  Lame MP3 encoder plugin Mean 2008
[AudioEncoder] Loaded TwoLame version 01.00.00 wavTag :0x50
[AudioEncoder] Registered filter /usr/lib/ADM_plugins/audioEncoders//libADM_ae_twolame.so as  TwoLame MP2 encoder plugin Mean 2008
[AudioEncoder] Loaded PCM version 01.00.00 wavTag :0x1
[AudioEncoder] Registered filter /usr/lib/ADM_plugins/audioEncoders//libADM_ae_pcm.so as  PCM encoder plugin Mean 2008
[AudioEncoder] Loaded LavAC3 version 01.00.00 wavTag :0x2000
[AudioEncoder] Registered filter /usr/lib/ADM_plugins/audioEncoders//libADM_ae_lav_ac3.so as  AC3 LavEncoder encoder plugin Mean 2008
[AudioEncoder] Loaded LavMP2 version 01.00.00 wavTag :0x50
[AudioEncoder] Registered filter /usr/lib/ADM_plugins/audioEncoders//libADM_ae_lav_mp2.so as  MP2 LavCodec encoder plugin Mean 2008
[AudioEncoder] Loaded Vorbis version 01.00.00 wavTag :0x676f
[AudioEncoder] Registered filter /usr/lib/ADM_plugins/audioEncoders//libADM_ae_vorbis.so as  Vorbis encoder plugin Mean 2008
[AudioEncoder] Loaded Faac version 01.00.00 wavTag :0xff
[AudioEncoder] Registered filter /usr/lib/ADM_plugins/audioEncoders//libADM_ae_faac.so as  Faac AAC encoder plugin Mean 2008
[ADM_ae_plugin] Scanning done
[ADM_ad_plugin] Scanning directory /home/larry/.avidemux/plugins/audioDecoder/
[ADM_ad_plugin] Cannot parse plugin
[ADM_vf_plugin] Scanning directory /home/larry/.avidemux/plugins/videoFilter/
[ADM_vf_plugin] Cannot parse plugin
[ADM_vidEnc_plugin] Scanning directory /usr/lib/ADM_plugins/videoEncoder/
ignored: avcodec
ignored: x264
ignored: xvid
[ADM_vidEnc_plugin] Plugin loaded version 1.0.1, filename libADM_vidEnc_x264.so, desc: x264 video encoder plugin for Avidemux (c) Mean/Gruntster
[Xvid] Initialising Xvid
[Xvid] Build: xvid-1.2.2
[Xvid] SIMD supported: (1ff)
        MMX
        MMXEXT
        SSE
        SSE2
        SSE3
        3DNOW
        3DNOWEXT
        ALTIVEC
[ADM_vidEnc_plugin] Plugin loaded version 1.0.1, filename libADM_vidEnc_xvid.so, desc: Xvid video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Plugin loaded version 1.0.0, filename libADM_vidEnc_avcodec.so, desc: DV video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Plugin loaded version 1.0.0, filename libADM_vidEnc_avcodec.so, desc: FFV1 video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Plugin loaded version 1.0.0, filename libADM_vidEnc_avcodec.so, desc: FFVHuff video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Plugin loaded version 1.0.0, filename libADM_vidEnc_avcodec.so, desc: Huffyuv video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Plugin loaded version 1.0.0, filename libADM_vidEnc_avcodec.so, desc: MPEG-1 video encoder plugin for Avidemux (c) Mean/Gruntster
[ADM_vidEnc_plugin] Scanning done, found 7 codec
avidemux: symbol lookup error: avidemux: undefined symbol: movenc_init 

```I have tried installing and uninstalling with no results. Was working great with 10.04.

---

### Post by Ragnar! on 2010-11-12
One of the moderators on the avidemux forum suggested that this is caused by more than one version being installed. I had both types of avidemux installed in 10.04 and both worked. since then I have uninstalled both through Ubuntu program manager and then reinstalled just the non-gtk one. but I am still getting this error. Is it likely that the program manager is leaving some bits behind? If so, is there a way to do a clean manual uninstall? Or am I just barking up the wrong meerkat here..:)  ?

---

