---
title: "Totem fails with BadAlloc error"
date: 2005-12-04
forum: Multimedia &amp; Video
---

### Post by zeeone on 2005-12-04
I've installed all video plug-ins and followed all advice on installing and configuring totem, but it crashes with the following message. Can anyone help?

```

(totem:20881): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:20881): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
Benchmarking memcpy methods (smaller is better):
        libc memcpy() : 242050305
        linux kernel memcpy() : 253390627
        MMX optimized memcpy() : 245644597
        MMXEXT optimized memcpy() : 170554755
        SSE optimized memcpy() : 168795547
load_plugins: skipping unreadable plugin directory /home/stefan/.xine/plugins.
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_flac.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_flac.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_goom.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_mosaico.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_switch.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_tvtime.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_bitplane.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_ao_out_alsa.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_ao_out_arts.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_ao_out_esd.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_ao_out_file.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_ao_out_none.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_ao_out_oss.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_a52.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_dvaudio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_dts.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_dxr3_video.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_dxr3_spu.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_gsm610.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_faad.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_real_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_image.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_lpcm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_mad.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_mpc.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_mpeg2.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_nsf.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_real.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_speex.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_rgb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_spucc.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_spu.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_spucmml.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_spudvb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_sputext.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_theora.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_vorbis.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_w32dll.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_w32dll.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_decode_yuv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_asf.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_avi.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_fli.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_flv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_iff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_image.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_matroska.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_mng.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_mpeg.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_mpeg_block.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_mpeg_elem.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_mpeg_pes.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_mpeg_ts.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_nsv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_ogg.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_ogg.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_pva.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_rawdv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_real.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_slave.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_sputext.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_yuv4mpeg2.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_dmx_yuv_frames.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_cdda.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_dvb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_dvd.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_file.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_gnome_vfs.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_http.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_mms.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_net.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_pnm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_pvr.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_rtp.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_rtsp.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_smb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_stdin_fifo.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_v4l.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_v4l.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_vcd.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_inp_vcdo.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_aa.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_caca.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_dxr3.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_dxr3.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_fb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_none.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_opengl.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_sdl.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_vidix.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_vidix.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_xshm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.0.1/xineplug_vo_out_xv.so found
init class succeeded
gnome_vfs init_input_class
params.c:OpenConfFile() - Unable to open configuration file &quot;/home/stefan/.smb/smb.conf&quot;:
        No such file or directory
Using netbios name GAZELLE.
Using workgroup MSHOME.
video_out_xv: using Xv port 61 from adaptor NV Video Overlay for hardware colorspace conversion and scaling.
video_out_xv: double buffering mode = 1
video_out_xv: port attribute XV_COLORKEY (6) value is 66046
video_out_xv: port attribute XV_AUTOPAINT_COLORKEY (7) value is 0
video_out_xv: port attribute XV_BRIGHTNESS (5) value is -1
video_out_xv: port attribute XV_CONTRAST (4) value is 4095
video_out_xv: port attribute XV_SATURATION (3) value is 4095
video_out_xv: ignoring broken XV_HUE settings on NVidia cardsvideo_out_xv: this adaptor supports the yuy2 format.
video_out_xv: this adaptor supports the yv12 format.
x11osd: unscaled overlay created (Colorkey mode).
video_out: thread created
audio_alsa_out : supported modes are 8bit 16bit 24bit 32bit mono stereo (4-channel not enabled in xine config) (4.1-channel not enabled in xine config) (5-channel not enabled in xine config) (5.1-channel not enabled in xine config) (a/52 and DTS pass-through not enabled in xine config)
audio_out: thread created
xine_stream_new
video_out_xv: VO_PROP_INTERLACED(0)
xine: found input plugin  : file input plugin
load_plugins: probing demux 'anx'
load_plugins: probing demux 'asf'
load_plugins: probing demux 'aud'
load_plugins: probing demux 'aiff'
load_plugins: probing demux 'cdda'
load_plugins: probing demux 'flac'
load_plugins: probing demux 'nsf'
load_plugins: probing demux 'realaudio'
load_plugins: probing demux 'snd'
load_plugins: probing demux 'voc'
load_plugins: probing demux 'vox'
load_plugins: probing demux 'wav'
load_plugins: probing demux 'mod'
TEST mod decode
load_plugins: probing demux 'avi'
load_plugins: probing demux 'fli'
load_plugins: probing demux 'flashvideo'
load_plugins: probing demux 'wve'
load_plugins: probing demux 'idcin'
load_plugins: probing demux 'ipmovie'
load_plugins: probing demux 'vqa'
load_plugins: probing demux 'wc3movie'
load_plugins: probing demux 'roq'
load_plugins: probing demux 'str'
load_plugins: probing demux 'film'
load_plugins: probing demux 'smjpeg'
load_plugins: probing demux 'fourxm'
load_plugins: probing demux 'vmd'
load_plugins: probing demux 'iff'
load_plugins: probing demux 'image'
load_plugins: probing demux 'matroska'
ebml: invalid master element
load_plugins: probing demux 'mng'
xine: found demuxer plugin: Multiple-image Network Graphics demux plugin
video discontinuity #1, type is 0, disc_off 0
waiting for audio discontinuity #1
audio discontinuity #1, type is 0, disc_off 0
waiting for in_discontinuity update #1
vpts adjusted with prebuffer to 31586
load_plugins: plugin rgb will be used for video streamtype 10.
xine_play
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 87 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by Baddox on 2006-06-11
I have a very similar problem.  When I try to play a video with totem, vlc, or mplayer, the command line gives the same error.   
For totem:
```
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 86 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```
For vlc:
```
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  83
  Current serial number in output stream:  84
```

It's clearly a problem with the actual displaying of video, because vlc does not crash until a video file is loaded (it will play mp3's, ogg's, etc. fine).  Also, I have uninstalled and reinstalled the video players, so I know the programs themselves are not the issue.

I've scoured forums like crazy, and several people have posted these errors, but with no successful results.  It's not just an Ubuntu thing, because people on Fedora forums have posted the same problem.  Most people indicate a likely xorg.conf problem, although I can't pin down what it could be.  I'm using a Dell 2005fpw monitor with resolution of 1680x1050, which required some tweaking in xorg.conf, but everything worked great in Ubuntu 5.10, which I just got rid of in lieu of 6.06 (I didn't actually upgrade, I just formatted and installed 6.06).  This is *extremely* frustrating, if anyone has any clue what's going on, I would definitely appreciate it.

---

### Post by cdude on 2006-06-11
Same here :(

```
$ totem
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 81 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by iinode on 2006-12-29
Hello everybody

I'm new to ubuntu, and an XP convert.

But i've used vlc on windows

What fixed my problem (in vlc for linux) was changing the output display.

Start up vlc (from the command line as "vlc" (no quotes) or from the menu).

From there, type Ctrl-S

You should be at the preferences window

In the menu to the left, expand Video -> Output Modules.

From here, if you expand Output Modules, you will see a list of modules.  You can configure them here

If you click on Output Modules and check the "advanced options" box, you can choose your output module.

Every computer is different, so it's up to you to figure out the rest.

Keep in mind, i'm not even in high school yet.

---

