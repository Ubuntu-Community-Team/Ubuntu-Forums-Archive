---
title: "After upgrade to 10.10 avidemux will not start"
date: 2010-11-12
forum: Multimedia Software
---

### Post by Ragnar! on 2010-11-12
I have posted this in an older thread about avidemux so forgive me if I am wrong to repost this, but after reading the original post, the problem i am experienceing seems to have nothing to do with the problem reported there. Feel free to remove this or chastise me if it is warranted :).

Since upgrading from 10.04 to 10.10 (through the update manager) my previously well working avidemux now will not even start. here is the output from the terminal.

```
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
```

I have unistalled and reinstalled avidemux with the same results.  I have also uninstalled the ffmpeg, mencoder, and medibuntu codecs and reinstalled, however, I am getting the same terminal output and the same results.

Is anyone else experiencing this? If so, or if any of you experts could help out here it would be much appreciated.

---

### Post by mc4man on 2010-11-12
Is there a reason you don't want to use the current mav version? (or is it installed but showing up as 2.5.2?
> avidemux
*************************
  Avidemux v2.5.3
 [http://www.avidemux.org](http://www.avidemux.org)
 Code      : Mean, JSC, Gruntster 
 GFX       : Nestor Di , [email]nestordi@augcyl.org[/email]
 Design    : Jakub Misak
 FreeBSD   : Anish Mistry, [email]amistry@am-productions.biz[/email]
 Audio     : Mihail Zenkov
 MacOsX    : Kuisathaverat
 Win32     : Gruntster

Compiler: GCC 4.4.5 20100728 (prerelease)
Build Target: Linux (x86)
User Interface: Qt (4.7.0)



(both the qt and gtk work ok here, switched from update-alternatives, though can't see much use to having both installed...

Edit: 
you may even wish to try the latest, released for natty but should be fine on maverick
To try I'd either do a complete removal of existing packages or just make sure you dl all that are installed. Stick them all in a folder, cd to it and 
sudo dpkg -i *.deb

i386 packages
[https://launchpad.net/ubuntu/+source/avidemux/1:2.5.4-0ubuntu2/+build/2019130](https://launchpad.net/ubuntu/+source/avidemux/1:2.5.4-0ubuntu2/+build/2019130)
amd_64
[https://launchpad.net/ubuntu/+source/avidemux/1:2.5.4-0ubuntu2/+build/2019129](https://launchpad.net/ubuntu/+source/avidemux/1:2.5.4-0ubuntu2/+build/2019129)

   >  * New upstream release (LP: #665630):
      - Support for MKV compressed headers.
      - Improved VC1 support.
      - New display : QtOpenGL.
      - Improved x264 dialog and options.
    * Add .gitignore,debian/gbp.conf files.

> doug@doug-laptop:~/Desktop/avid$ avidemux
*************************
  Avidemux v2.5.4
*************************


---

### Post by Ragnar! on 2010-11-12
I am at work right now but will try your suggestions when i get home. BTW that version is the one that is in the repository as I uninstalled the old version and reinstalled the one that this readout is from. I am obviously not as well versed at this as I would like to be, so perhaps i need to update the repository in some way and also try another fresh install as well.

In any event I thank you very much for your reply and help!

I want to add that
in my first post the line that seems to be where everything goes south is at the end:

**"avidemux: symbol lookup error: avidemux: undefined symbol: movenc_init"**

---

### Post by Ragnar! on 2010-11-12
I also have this submitted on the avidemux forums, and what one of the administrators thinks is that there may be a problem with two different versions being installed. Is this possible, even though I uninstalled and reinstalled using the Ubuntu software center? Is there a better way to totally uninstall avidemux so there's no trace left of it and do a clean reinstall? Or do you think this is not the problem?

Thank you for listening and helping!

---

### Post by Ragnar! on 2010-11-13
Thanks mc4man for giving me the idea to upgrade my version. I went a step further and installed the new archive from avidemux and installed v2.5.4. It now opens and am about to try encoding for a test!

---

### Post by mc4man on 2010-11-13
When you get home open up synaptic, search avidemux and check your installed versions and the latest version 

What you posted  is not the current maverick version - maverick updated to 2.5.3 way back in may during the development cycle using gcc 4.4.5 

Try marking all installed avidemux packages for 'complete removal'
After removing then open a terminal and run avidemux - see if it runs - it shouldn't
(also browse to /usr/local/bin and see if it's there. Also look in /usr/local/share and /usr/local/lib for an avidemux folder or any ADM* files or folders  - if anything is found then delete

Then run sudo apt-get update and re-install avidemux, either the gtk or qt4 version
It should be installing  the 2.5.3 version. If the 2.5.3 isn't shown then change to the main server in 'software sources'

---

### Post by mc4man on 2010-11-13
Missed your post while posting - seems like you've resolved...

---

### Post by Ragnar! on 2010-11-13
Encoding as I type, thank you so much for the help!

---

### Post by Ragnar! on 2010-11-13
One last thought on this. Should I still run that command to make sure that all the synaptic packages are updated to the latest version? It seems strange that I would get an update that wouldn't have included the synaptic updated packages. One more step on this very fun journey in Ubuntu. It reminds me of the fun I had when I first got into computers in '82.

---

