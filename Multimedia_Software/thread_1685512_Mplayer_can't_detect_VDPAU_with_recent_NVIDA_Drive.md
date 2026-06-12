---
title: "Mplayer can't detect VDPAU with recent NVIDA Driver"
date: 2011-02-10
forum: Multimedia Software
---

### Post by beterhans on 2011-02-10
I have a nVIDIA Geforce 8500 GT on my Ubuntu system.
and have the latest 260.19.36 driver installed.

the Mplayer was from SVN checkout also the latest version.

but the configure script from mplayer can't detect VDPAU on my system. just give me the output like this
Check VDPAU .... No

If I force Enable the VDPAU. the make process won't be successful.



just googled, most article that I can find about Mplayer and VDPAU is out of date. 


any idea??

---

### Post by BicyclerBoy on 2011-02-11
GeForce 8500 GT     0x0421     A

Your video card is feature set A vdpau
should do full h/w decode H264
partial VC1
partial mpeg2

install/run vdpauinfo or vdpautest

maybe the driver is not working/installed correctly.

---

### Post by beterhans on 2011-02-11
> **BicyclerBoy said:**
> GeForce 8500 GT     0x0421     A

Your video card is feature set A vdpau
should do full h/w decode H264
partial VC1
partial mpeg2

install/run vdpauinfo or vdpautest

maybe the driver is not working/installed correctly.

Thanks for the inputs
and I've tried vdpauinfo but failed to compile it.
it said I don't have the libvdpau and lvdpau libraries.

I did a little research and I found those library was delivered by the driver (nVIDIA Run file) but it has no .pc file for pkg-config. so I'm learning to write a .pc file for the pkg-config by myself.

---

### Post by beterhans on 2011-02-12
OK I wrote the vdpau.pc and mplayer can detect my vdpau library through pkg-config

but have error in make progress.

configure scrip
```

./configure --prefix=/usr/local --confdir=/etc/mplayer --enable-gui --with-vidix-drivers=nvidia

```

The results of configure script

```

hans@Galaxy:~/sourse/mplayer$ ./configure --prefix=/usr/local --confdir=/etc/mplayer --enable-gui 
Current branch master is up to date.
Checking for cc version ... 4.4.1 
Detected operating system: Linux
Detected host architecture: i386
Checking for host cc ... cc 
Checking for cross compilation ... no 
Checking for CPU vendor ... GenuineIntel (6:15:6) 
Checking for CPU type ...  Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz 
Checking for kernel support of mmx ... yes 
Checking for kernel support of mmxext ... yes 
Checking for kernel support of sse ... yes 
Checking for kernel support of sse2 ... yes 
Checking for kernel support of ssse3 ... yes 
Checking for kernel support of cmov ... yes 
Checking for mtrr support ... yes 
Checking for GCC & CPU optimization abilities ... native 
Checking for byte order ... little-endian 
Checking for extern symbol prefix ...  
Checking for assembler support of -pipe option ... yes 
Checking for compiler support of named assembler arguments ... yes 
Checking for assembler (as ) ... ok 
Checking for PIC ... no 
Checking for .align is a power of two ... no 
Checking for 10 assembler operands ... yes 
Checking for ebx availability ... yes 
Checking for yasm ... yasm 
Checking for bswap ... yes 
Checking for xmm clobbers ... no 
Checking for Linux kernel version ... 2.6.31-20-generic, ok 
Checking for -lposix ... no 
Checking for -lm ... yes 
Checking for langinfo ... yes 
Checking for language ... messages: en - man pages: en - documentation: en 
Checking for enable sighandler ... yes 
Checking for runtime cpudetection ... no 
Checking for restrict keyword ... restrict 
Checking for __builtin_expect ... yes 
Checking for kstat ... no 
Checking for posix4 ... no 
Checking for exp2 ... yes 
Checking for exp2f ... yes 
Checking for llrint ... yes 
Checking for llrintf ... yes 
Checking for log2 ... yes 
Checking for log2f ... yes 
Checking for lrint ... yes 
Checking for lrintf ... yes 
Checking for round ... yes 
Checking for roundf ... yes 
Checking for truncf ... yes 
Checking for mkstemp ... yes 
Checking for nanosleep ... yes 
Checking for socklib ... yes 
Checking for netdb.h, struct addrinfo ... yes 
Checking for netdb.h, getaddrinfo() ... yes 
Checking for sockaddr_storage ... yes 
Checking for struct ipv6_mreq ... yes 
Checking for struct sockaddr_in6 ... yes 
Checking for struct sockaddr sa_len ... no 
Checking for arpa/inet.h ... yes 
Checking for inet_pton() ... yes 
Checking for inet_aton() ... yes 
Checking for socklen_t ... yes 
Checking for closesocket() ... no 
Checking for networking ... yes 
Checking for inet6 ... yes 
Checking for gethostbyname2 ... yes 
Checking for sys/poll.h ... yes 
Checking for inttypes.h (required) ... yes 
Checking for int_fastXY_t in inttypes.h ... yes 
Checking for malloc.h ... yes 
Checking for memalign() ... yes 
Checking for posix_memalign() ... yes 
Checking for alloca.h ... yes 
Checking for fastmemcpy ... yes 
Checking for hard-coded tables ... no 
Checking for mman.h ... yes 
Checking for dynamic loader ... yes 
Checking for dynamic a/v plugins support ... no 
Checking for pthread ... yes (using -lpthread)
Checking for w32threads ... no (using pthread instead)
Checking for rpath ... no 
Checking for iconv ... yes 
Checking for soundcard.h ... yes (sys/soundcard.h)
Checking for sys/dvdio.h ... no 
Checking for sys/cdio.h ... no 
Checking for linux/cdrom.h ... yes 
Checking for dvd.h ... no 
Checking for termcap ... yes (using -lncurses)
Checking for termios ... yes (using termios.h)
Checking for shm ... yes 
Checking for strsep() ... yes 
Checking for vsscanf() ... yes 
Checking for swab() ... yes 
Checking for POSIX select() ... yes 
Checking for audio select() ... yes 
Checking for gettimeofday() ... yes 
Checking for glob() ... yes 
Checking for setenv() ... yes 
Checking for setmode() ... no 
Checking for sys/sysinfo.h ... yes 
Checking for Apple IR ... yes 
Checking for pkg-config ... yes 
Checking for Samba support (libsmbclient) ... yes 
Checking for /dev/mga_vid ... no 
Checking for tdfxfb ... no 
Checking for s3fb ... no 
Checking for wii ... no 
Checking for tdfxvid ... no 
Checking for xvr100 ... no 
Checking for tga ... yes 
Checking for md5sum support ... yes 
Checking for yuv4mpeg support ... yes 
Checking for bl ... no 
Checking for DirectFB ... yes 
Checking for X11 headers presence ... yes 
Checking for X11 ... yes 
Checking for Xss screensaver extensions ... no 
Checking for DPMS ... yes (using Xdpms 4)
Checking for Xv ... yes 
Checking for XvMC ... no 
Checking for VDPAU ... yes 
Checking for Xinerama ... yes 
Checking for Xxf86vm ... yes 
Checking for XF86keysym ... yes 
Checking for DGA ... yes (using DGA 2.0)
Checking for xmga ... no 
Checking for 3dfx ... no 
Checking for VIDIX ... yes 
Checking for VIDIX PCI device name database ... yes 
Checking for VIDIX dhahelper support ... no 
Checking for VIDIX svgalib_helper support ... no 
Checking for GGI ... no 
Checking for GGI extension: libggiwmh ... no 
Checking for AA ... yes 
Checking for CACA ... yes 
Checking for SVGAlib ... yes 
Checking for FBDev ... yes 
Checking for DVB ... yes 
Checking for PNG support ... yes 
Checking for MNG support ... yes 
Checking for JPEG support ... yes 
Checking for OpenJPEG (JPEG2000) support ... no 
Checking for PNM support ... yes 
Checking for GIF support ... yes 
Checking for broken giflib workaround ... disabled 
Checking for VESA support ... no 
Checking for SDL ... yes 
Checking for OpenGL ... yes (backends: x11 sdl)
Checking for MatrixView ... yes 
Checking for DXR2 ... no 
Checking for DXR3/H+ ... no 
Checking for IVTV TV-Out (pre linux-2.6.24) ... no 
Checking for V4L2 MPEG Decoder ... yes 
Checking for OSS Audio ... yes 
Checking for aRts ... no 
Checking for EsounD ... yes 
Checking for esd_get_latency() ... yes 
Checking for NAS ... yes 
Checking for pulse ... yes 
Checking for JACK ... yes 
Checking for OpenAL ... yes 
Checking for ALSA audio ... yes (using alsa 1.0.x and alsa/asoundlib.h)
Checking for Sun audio ... no 
Checking for VCD support ... yes 
Checking for Blu-ray support ... no 
Checking for dvdread ... yes (internal)
Checking for internal libdvdcss ... yes 
Checking for cdparanoia ... yes 
Checking for libcdio ... auto (using cdparanoia)
Checking for bitmap font support ... yes 
Checking for freetype >= 2.0.9 ... yes 
Checking for fontconfig ... yes 
Checking for SSA/*** support ... yes 
Checking for fribidi with charsets ... yes 
Checking for ENCA ... no 
Checking for zlib ... yes 
Checking for bzlib ... no 
Checking for RTC ... yes 
Checking for liblzo2 support ... yes 
Checking for mad support ... no 
Checking for Twolame ... no 
Checking for Toolame ... no 
Checking for OggVorbis support ... yes (internal Tremor)
Checking for libspeex (version >= 1.1 required) ... yes 
Checking for libgsm ... no 
Checking for OggTheora support ... yes 
Checking for mp3lib support ... yes 
Checking for mpg123 support ... no 
Checking for liba52 support ... yes 
Checking for libmpeg2 support ... yes (internal)
Checking for libdca support ... yes 
Checking for libmpcdec (musepack, version >= 1.2.1 required) ... no 
Checking for FAAC support ... yes (in FFmpeg: yes)
Checking for FAAD2 support ... yes 
Checking for LADSPA plugin support ... yes 
Checking for libbs2b audio filter support ... no 
Checking for Win32 codecs ... yes 
Checking for XAnim codecs ... yes (dynamic loader support needed)
Checking for RealPlayer codecs ... yes (dynamic loader support needed)
Checking for QuickTime codecs ... yes 
Checking for Nemesi Streaming Media libraries ... no 
Checking for LIVE555 Streaming Media libraries ... yes (using distribution version)
Checking for RTMPDump Streaming Media library ... no 
Checking for FFmpeg ... yes 
Checking for libopencore_amr narrowband ... no 
Checking for libopencore_amr wideband ... no 
Checking for libdv-0.9.5+ ... no 
Checking for Xvid ... yes 
Checking for Xvid two pass plugin ... yes 
Checking for x264 ... yes (in FFmpeg: yes)
Checking for libdirac ... no 
Checking for libschroedinger ... yes 
Checking for libvpx ... no 
Checking for libnut ... no 
Checking for zr ... no 
Checking for libmp3lame ... yes (in FFmpeg: yes)
Checking for mencoder ... yes 
Checking for UnRAR executable ... yes 
Checking for TV interface ... yes 
Checking for DirectShow TV interface ... no 
Checking for Video 4 Linux TV interface ... yes 
Checking for Video 4 Linux 2 TV interface ... yes 
Checking for Radio interface ... no 
Checking for Capture for Radio interface ... no 
Checking for Video 4 Linux 2 Radio interface ... no 
Checking for Video 4 Linux Radio interface ... no 
Checking for Video 4 Linux 2 MPEG PVR interface ... yes 
Checking for ftp ... yes 
Checking for vstream client ... yes 
Checking for OSD menu ... no 
Checking for Subtitles sorting ... yes 
Checking for XMMS inputplugin support ... no 
Checking for GUI ... yes
Checking for XShape extension ... yes 
Checking for GTK+ version ... 2.18.3 
Checking for glib version ... 2.22.3 
Checking for automatic gdb attach ... no 
Checking for compiler support for noexecstack ... yes 
Checking for linker support for --nxcompat --no-seh --dynamicbase ... no 
Checking for joystick ... no 
Checking for lirc ... yes 
Checking for lircc ... no 
Checking for DVD support (libdvdnav) ... yes (internal)
Creating config.mak
Creating config.h

Config files successfully generated by ./configure --prefix=/usr/local --confdir=/etc/mplayer --enable-gui !

  Install prefix: /usr/local
  Data directory: /usr/local/share/mplayer
  Config direct.: /etc/mplayer

  Byte order: little-endian
  Optimizing for: native

  Languages:
    Messages/GUI: en
    Manual pages: en
    Documentation: en

  Enabled optional drivers:
    Input: dvdnav(internal) vstream ftp pvr tv-v4l2 tv-v4l tv live555 cddb cdda libdvdcss(internal) dvdread(internal) vcd dvb smb networking 
    Codecs: libschroedinger x264 xvid ffmpeg(internal) qtx real xanim win32 faad2 faac libdca libmpeg2(internal) liba52 mp3lib(internal) libtheora speex tremor(internal) liblzo gif 
    Audio output: alsa openal jack pulse nas esd oss v4l2 sdl mpegpes(dvb) 
    Video output: v4l2 matrixview opengl sdl gif89a pnm jpeg mpegpes(dvb) fbdev svga caca aa xvidix cvidix dga vdpau xv x11 xover directfb dfbmga yuv4mpeg md5sum tga 

  Disabled optional drivers:
    Input: radio tv-dshow librtmp nemesi bluray 
    Codecs: libvpx libdirac libdv libopencore_amrwb libopencore_amrnb musepack mpg123 libgsm toolame twolame libmad OpenJPEG 
    Audio output: sun arts ivtv dxr2 
    Video output: zr zr2 ivtv dxr3 dxr2 vesa ggi winvidix 3dfx xmga xvmc bl xvr100 tdfx_vid wii s3fb tdfxfb mga 

'config.h' and 'config.mak' contain your configuration options.
Note: If you alter theses files (for instance CFLAGS) MPlayer may no longer
      compile *** DO NOT REPORT BUGS if you tweak these files ***

'make' will now compile MPlayer and 'make install' will install it.
Note: On non-Linux systems you might need to use 'gmake' instead of 'make'.

Please check mtrr settings at /proc/mtrr (see DOCS/HTML/en/video.html#mtrr)

Check config.log if you wonder why an autodetection failed (make sure
development headers/packages are installed).

NOTE: The --enable-* parameters unconditionally force options on, completely
skipping autodetection. This behavior is unlike what you may be used to from
autoconf-based configure scripts that can decide to override you. This greater
level of control comes at a price. You may have to provide the correct compiler
and linker flags yourself.
If you used one of these options (except --enable-menu and similar ones that
turn on internal features) and experience a compilation or linking failure,
make sure you have passed the necessary compiler/linker flags to configure.

If you suspect a bug, please read DOCS/HTML/en/bugreports.html.

```



Error when making
```

CC      x86/yuv2rgb_mmx.o
CC      yuv2rgb.o
yuv2rgb.c: In function 'ff_yuv2rgb_c_init_tables':
yuv2rgb.c:658: warning: 'abase' may be used uninitialized in this function
AR      libswscale.a
make[1]: Leaving directory `/home/hans/sourse/mplayer/ffmpeg/libswscale'
touch ffmpeg/libswscale/libswscale.a
cc -o mplayer command.o m_property.o mixer.o mp_fifo.o mplayer.o parser-mpcmd.o pnm_loader.o input/input.o libao2/ao_mpegpes.o libao2/ao_null.o libao2/ao_pcm.o libao2/audio_out.o libvo/aspect.o libvo/geometry.o libvo/video_out.o libvo/vo_mpegpes.o libvo/vo_null.o sub/spuenc.o libvo/vo_aa.o libao2/ao_alsa.o input/appleir.o libvo/vo_caca.o libvo/vo_dga.o libvo/vo_directfb2.o libvo/vo_dfbmga.o libao2/ao_esd.o libvo/vo_fbdev.o libvo/vo_fbdev2.o libvo/vo_png.o libvo/vo_gif89a.o libvo/gl_common.o libvo/vo_gl.o libvo/vo_gl2.o libvo/csputils.o libvo/sdl_common.o libvo/x11_common.o libvo/vo_matrixview.o libvo/matrixview.o gui/bitmap.o gui/app.o gui/cfg.o gui/interface.o gui/mplayer/gui_common.o gui/mplayer/menu.o gui/mplayer/mw.o gui/mplayer/pb.o gui/mplayer/play.o gui/mplayer/sw.o gui/mplayer/widgets.o gui/mplayer/gtk/about.o gui/mplayer/gtk/eq.o gui/mplayer/gtk/fs.o gui/mplayer/gtk/gtk_common.o gui/mplayer/gtk/gtk_menu.o gui/mplayer/gtk/gtk_url.o gui/mplayer/gtk/mb.o gui/mplayer/gtk/opts.o gui/mplayer/gtk/pl.o gui/mplayer/gtk/sb.o gui/skin/cut.o gui/skin/font.o gui/skin/skin.o gui/wm/ws.o gui/wm/wsxdnd.o libao2/ao_jack.o libvo/vo_jpeg.o input/lirc.o libvo/vo_md5sum.o libao2/ao_nas.o udp_sync.o libao2/ao_openal.o libao2/ao_oss.o libvo/vo_pnm.o libao2/ao_pulse.o libao2/ao_sdl.o libvo/vo_sdl.o libvo/vo_svga.o libvo/vo_tga.o libvo/vo_v4l2.o libao2/ao_v4l2.o libvo/vo_vdpau.o libvo/vo_cvidix.o libvo/vosub_vidix.o vidix/vidix.o vidix/drivers.o vidix/dha.o vidix/mtrr.o vidix/pci.o vidix/pci_names.o vidix/pci_dev_ids.o vidix/nvidia_vid.o libvo/vo_x11.o libvo/vo_xover.o libvo/vo_xv.o libvo/vo_xvidix.o libvo/vo_yuv4mpeg.o asxparser.o bstr.o codec-cfg.o cpudetect.o edl.o fmt-conversion.o m_config.o m_option.o m_struct.o mp_msg.o mpcommon.o parser-cfg.o path.o playtree.o playtreeparser.o subopt-helper.o libaf/af.o libaf/af_center.o libaf/af_channels.o libaf/af_comp.o libaf/af_delay.o libaf/af_dummy.o libaf/af_equalizer.o libaf/af_extrastereo.o libaf/af_format.o libaf/af_gate.o libaf/af_hrtf.o libaf/af_karaoke.o libaf/af_pan.o libaf/af_resample.o libaf/af_scaletempo.o libaf/af_sinesuppress.o libaf/af_stats.o libaf/af_sub.o libaf/af_surround.o libaf/af_sweep.o libaf/af_tools.o libaf/af_volnorm.o libaf/af_volume.o libaf/filter.o libaf/format.o libaf/reorder_ch.o libaf/window.o libmpcodecs/ad.o libmpcodecs/ad_alaw.o libmpcodecs/ad_dk3adpcm.o libmpcodecs/ad_dvdpcm.o libmpcodecs/ad_hwac3.o libmpcodecs/ad_hwmpa.o libmpcodecs/ad_imaadpcm.o libmpcodecs/ad_msadpcm.o libmpcodecs/ad_pcm.o libmpcodecs/dec_audio.o libmpcodecs/dec_teletext.o libmpcodecs/dec_video.o libmpcodecs/img_format.o libmpcodecs/mp_image.o libmpcodecs/pullup.o libmpcodecs/vd.o libmpcodecs/vd_hmblck.o libmpcodecs/vd_lzo.o libmpcodecs/vd_mpegpes.o libmpcodecs/vd_mtga.o libmpcodecs/vd_null.o libmpcodecs/vd_raw.o libmpcodecs/vd_sgi.o libmpcodecs/vf.o libmpcodecs/vf_1bpp.o libmpcodecs/vf_2xsai.o libmpcodecs/vf_blackframe.o libmpcodecs/vf_boxblur.o libmpcodecs/vf_crop.o libmpcodecs/vf_cropdetect.o libmpcodecs/vf_decimate.o libmpcodecs/vf_delogo.o libmpcodecs/vf_denoise3d.o libmpcodecs/vf_detc.o libmpcodecs/vf_dint.o libmpcodecs/vf_divtc.o libmpcodecs/vf_down3dright.o libmpcodecs/vf_dsize.o libmpcodecs/vf_dvbscale.o libmpcodecs/vf_eq.o libmpcodecs/vf_eq2.o libmpcodecs/vf_expand.o libmpcodecs/vf_field.o libmpcodecs/vf_fil.o libmpcodecs/vf_filmdint.o libmpcodecs/vf_fixpts.o libmpcodecs/vf_flip.o libmpcodecs/vf_format.o libmpcodecs/vf_framestep.o libmpcodecs/vf_gradfun.o libmpcodecs/vf_halfpack.o libmpcodecs/vf_harddup.o libmpcodecs/vf_hqdn3d.o libmpcodecs/vf_hue.o libmpcodecs/vf_il.o libmpcodecs/vf_ilpack.o libmpcodecs/vf_ivtc.o libmpcodecs/vf_kerndeint.o libmpcodecs/vf_mirror.o libmpcodecs/vf_noformat.o libmpcodecs/vf_noise.o libmpcodecs/vf_ow.o libmpcodecs/vf_palette.o libmpcodecs/vf_perspective.o libmpcodecs/vf_phase.o libmpcodecs/vf_pp7.o libmpcodecs/vf_pullup.o libmpcodecs/vf_rectangle.o libmpcodecs/vf_remove_logo.o libmpcodecs/vf_rgbtest.o libmpcodecs/vf_rotate.o libmpcodecs/vf_sab.o libmpcodecs/vf_scale.o libmpcodecs/vf_smartblur.o libmpcodecs/vf_softpulldown.o libmpcodecs/vf_stereo3d.o libmpcodecs/vf_softskip.o libmpcodecs/vf_swapuv.o libmpcodecs/vf_telecine.o libmpcodecs/vf_test.o libmpcodecs/vf_tfields.o libmpcodecs/vf_tile.o libmpcodecs/vf_tinterlace.o libmpcodecs/vf_unsharp.o libmpcodecs/vf_vo.o libmpcodecs/vf_yadif.o libmpcodecs/vf_yuvcsp.o libmpcodecs/vf_yvu9.o libmpdemux/aac_hdr.o libmpdemux/asfheader.o libmpdemux/aviheader.o libmpdemux/aviprint.o libmpdemux/demuxer.o libmpdemux/demux_aac.o libmpdemux/demux_asf.o libmpdemux/demux_audio.o libmpdemux/demux_avi.o libmpdemux/demux_demuxers.o libmpdemux/demux_film.o libmpdemux/demux_fli.o libmpdemux/demux_lmlm4.o libmpdemux/demux_mf.o libmpdemux/demux_mkv.o libmpdemux/demux_mov.o libmpdemux/demux_mpg.o libmpdemux/demux_nsv.o libmpdemux/demux_pva.o libmpdemux/demux_rawaudio.o libmpdemux/demux_rawvideo.o libmpdemux/demux_realaud.o libmpdemux/demux_real.o libmpdemux/demux_roq.o libmpdemux/demux_smjpeg.o libmpdemux/demux_ts.o libmpdemux/demux_ty.o libmpdemux/demux_ty_osd.o libmpdemux/demux_viv.o libmpdemux/demux_vqf.o libmpdemux/demux_y4m.o libmpdemux/ebml.o libmpdemux/extension.o libmpdemux/mf.o libmpdemux/mp3_hdr.o libmpdemux/mp_taglists.o libmpdemux/mpeg_hdr.o libmpdemux/mpeg_packetizer.o libmpdemux/parse_es.o libmpdemux/parse_mp4.o libmpdemux/video.o libmpdemux/yuv4mpeg.o libmpdemux/yuv4mpeg_ratio.o osdep/getch2.o osdep/timer-linux.o stream/open.o stream/stream.o stream/stream_bd.o stream/stream_cue.o stream/stream_file.o stream/stream_mf.o stream/stream_null.o stream/url.o sub/eosd.o sub/find_sub.o sub/osd.o sub/spudec.o sub/sub.o sub/sub_cc.o sub/subreader.o sub/vobsub.o stream/ai_alsa1x.o stream/ai_oss.o sub/font_load.o stream/stream_cdda.o stream/cdinfo.o stream/stream_cddb.o stream/dvb_tune.o stream/stream_dvb.o stream/stream_dvdnav.o libdvdnav/dvdnav.o libdvdnav/highlight.o libdvdnav/navigation.o libdvdnav/read_cache.o libdvdnav/remap.o libdvdnav/searching.o libdvdnav/settings.o libdvdnav/vm/decoder.o libdvdnav/vm/vm.o libdvdnav/vm/vmcmd.o stream/stream_dvd.o stream/stream_dvd_common.o libdvdread4/bitreader.o libdvdread4/dvd_input.o libdvdread4/dvd_reader.o libdvdread4/dvd_udf.o libdvdread4/ifo_print.o libdvdread4/ifo_read.o libdvdread4/md5.o libdvdread4/nav_print.o libdvdread4/nav_read.o libmpcodecs/ad_faad.o libvo/aclib.o av_opts.o libaf/af_lavcresample.o libmpcodecs/ad_ffmpeg.o libmpcodecs/vd_ffmpeg.o libmpcodecs/vf_lavc.o libmpcodecs/vf_lavcdeint.o libmpcodecs/vf_pp.o libmpcodecs/vf_screenshot.o libmpdemux/demux_lavf.o stream/stream_ffmpeg.o sub/av_sub.o libaf/af_lavcac3enc.o libmpcodecs/vf_fspp.o libmpcodecs/vf_geq.o libmpcodecs/vf_mcdeint.o libmpcodecs/vf_qp.o libmpcodecs/vf_spp.o libmpcodecs/vf_uspp.o sub/font_load_ft.o stream/stream_ftp.o libmpdemux/demux_gif.o libmpcodecs/vf_bmovl.o libaf/af_export.o osdep/mmap_anon.o libmpcodecs/vd_ijpg.o libaf/af_ladspa.o libmpcodecs/ad_liba52.o libmpcodecs/vf_***.o sub/***_mp.o sub/subassconvert.o libass/***.o libass/***_bitmap.o libass/***_cache.o libass/***_drawing.o libass/***_font.o libass/***_fontconfig.o libass/***_library.o libass/***_parse.o libass/***_render.o libass/***_render_api.o libass/***_strtod.o libass/***_utils.o libmpcodecs/ad_libdca.o libdvdcss/css.o libdvdcss/device.o libdvdcss/error.o libdvdcss/ioctl.o libdvdcss/libdvdcss.o libmpcodecs/vd_libmpeg2.o libmpeg2/alloc.o libmpeg2/cpu_accel.o libmpeg2/cpu_state.o libmpeg2/decode.o libmpeg2/header.o libmpeg2/idct.o libmpeg2/motion_comp.o libmpeg2/slice.o libmpeg2/idct_mmx.o libmpeg2/motion_comp_mmx.o stream/stream_smb.o libmpcodecs/vd_theora.o libmpdemux/demux_rtp.o libmpdemux/demux_rtp_codec.o stream/stream_live555.o libmpdemux/demux_mng.o libmpcodecs/ad_mp3lib.o mp3lib/sr1.o mp3lib/decode_i586.o mp3lib/dct64_mmx.o mp3lib/decode_mmx.o mp3lib/dct64_sse.o stream/stream_rtsp.o stream/freesdp/common.o stream/freesdp/errorlist.o stream/freesdp/parser.o stream/librtsp/rtsp.o stream/librtsp/rtsp_rtp.o stream/librtsp/rtsp_session.o osdep/shmem.o stream/stream_netstream.o stream/asf_mmst_streaming.o stream/asf_streaming.o stream/cookies.o stream/http.o stream/network.o stream/pnm.o stream/rtp.o stream/udp.o stream/tcp.o stream/stream_rtp.o stream/stream_udp.o stream/realrtsp/asmrp.o stream/realrtsp/real.o stream/realrtsp/rmff.o stream/realrtsp/sdpplin.o stream/realrtsp/xbuffer.o libmpcodecs/vd_mpng.o stream/stream_pvr.o libmpcodecs/ad_qtaudio.o libmpcodecs/vd_qtvideo.o libmpcodecs/ad_realaud.o libmpcodecs/vd_realvid.o libmpcodecs/ad_speex.o stream/cache2.o tremor/bitwise.o tremor/block.o tremor/codebook.o tremor/floor0.o tremor/floor1.o tremor/framing.o tremor/info.o tremor/mapping0.o tremor/mdct.o tremor/registry.o tremor/res012.o tremor/sharedbook.o tremor/synthesis.o tremor/window.o stream/stream_tv.o stream/tv.o stream/frequencies.o stream/tvi_dummy.o stream/tvi_v4l.o stream/audio_in.o stream/tvi_v4l2.o sub/unrar_exec.o stream/stream_vcd.o libmpcodecs/ad_libvorbis.o libmpdemux/demux_ogg.o stream/stream_vstream.o loader/wrapper.o loader/elfdll.o loader/ext.o loader/ldt_keeper.o loader/module.o loader/pe_image.o loader/pe_resource.o loader/registry.o loader/resource.o loader/win32.o libmpcodecs/ad_acm.o libmpcodecs/ad_dmo.o libmpcodecs/ad_dshow.o libmpcodecs/ad_twin.o libmpcodecs/vd_dmo.o libmpcodecs/vd_dshow.o libmpcodecs/vd_vfw.o libmpcodecs/vd_vfwex.o libmpdemux/demux_avs.o loader/afl.o loader/drv.o loader/vfl.o loader/dshow/DS_AudioDecoder.o loader/dshow/DS_Filter.o loader/dshow/DS_VideoDecoder.o loader/dshow/allocator.o loader/dshow/cmediasample.o loader/dshow/graph.o loader/dshow/guids.o loader/dshow/inputpin.o loader/dshow/mediatype.o loader/dshow/outputpin.o loader/dmo/DMO_AudioDecoder.o loader/dmo/DMO_VideoDecoder.o loader/dmo/buffer.o loader/dmo/dmo.o loader/dmo/dmo_guids.o libmpcodecs/vd_xanim.o libmpcodecs/vd_xvid4.o ffmpeg/libavformat/libavformat.a ffmpeg/libavcodec/libavcodec.a ffmpeg/libavcore/libavcore.a ffmpeg/libavutil/libavutil.a ffmpeg/libpostproc/libpostproc.a ffmpeg/libswscale/libswscale.a -Wl,-z,noexecstack  -ffast-math   -lncurses -lsmbclient -lpng -lz -lmng -lz -ljpeg -lungif -lasound -ldl -lpthread -lcdda_interface -lcdda_paranoia -lfreetype -lz -lfontconfig  -lfribidi -lz -llzo2 -lspeex -ltheora -logg   -la52 -ldca -lfaad -lliveMedia -lgroupsock -lUsageEnvironment -lBasicUsageEnvironment -lstdc++ -lxvidcore -lm -lschroedinger-1.0 -lpthread -loil-0.3 -lm -lrt   -lvstream-client -lpthread -ldl -rdynamic -L/usr/lib  -lm  -ldirectfb -lXext -lX11 -lpthread -lXv -lvdpau -lXinerama -lXxf86vm -lXxf86dga -laa -lcaca -lvga -lSDL -lGL -ldl -lesd -laudio -lXt -lpulse -ljack -lopenal -lfaac -lx264 -lpthread -lmp3lame -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0 -lglib-2.0 -llirc_client
ffmpeg/libavcodec/libavcodec.a(ac3dsp_mmx.o): In function `ff_ac3dsp_init_x86':
ac3dsp_mmx.c:(.text.unlikely+0x1d): undefined reference to `ff_ac3_exponent_min_mmxext'
ac3dsp_mmx.c:(.text.unlikely+0x27): undefined reference to `ff_ac3_exponent_min_sse2'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```


any help?

---

