---
title: "Totem Segmentation Fault"
date: 2007-09-18
forum: Multimedia &amp; Video
---

### Post by firedrow on 2007-09-18
When I try to run totem it opens and then closes.  I ran the gstreamer version from command and got 
```

drowland@Cambria:~$  totem
Segmentation fault (core dumped)
drowland@Cambria:~$  

```
When I changed to xine I got more, but still Segmentation Faults.
```

drowland@Cambria:~$  totem
Benchmarking memcpy methods (smaller is better):
        libc memcpy() : 345675736
        linux kernel memcpy() : 346615904
        MMX optimized memcpy() : 343404788
        MMXEXT optimized memcpy() : 212627288
        SSE optimized memcpy() : 209721764
load_plugins: skipping unreadable plugin directory /home/drowland/.xine/plugins.
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_iff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_image.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_ao_out_oss.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_nsf.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_mpeg_block.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_sputext.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_mpeg.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_dxr3_video.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_real.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_vo_out_fb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_real.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_mpeg_pes.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_theora.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_vo_out_xvmc.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_inp_dvd.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_inp_dvb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_speex.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_inp_http.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_pva.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/post/xineplug_post_switch.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/post/xineplug_post_tvtime.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/post/xineplug_post_mosaico.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/post/xineplug_post_goom.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_spu.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_yuv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_inp_mms.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_ao_out_file.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_inp_stdin_fifo.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_vo_out_none.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_mpc.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_bitplane.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_sputext.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_avi.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_image.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_inp_net.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_inp_smb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_inp_rtp.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_w32dll.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_w32dll.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_gsm610.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_inp_cdda.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_mpeg_elem.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_real_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_yuv_frames.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_faad.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_asf.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_vo_out_xxmc.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_dts.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_fli.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_vo_out_xv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_vo_out_xv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_ogg.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_ogg.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_flac.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_flac.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_vo_out_opengl.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_slave.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_vo_out_xshm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_vo_out_xshm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_inp_file.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_inp_rtsp.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_vo_out_sdl.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_ao_out_alsa.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_inp_v4l.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_inp_v4l.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_lpcm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_inp_vcd.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_flv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_ao_out_none.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_rawdv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_vo_out_dxr3.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_vo_out_dxr3.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_spudvb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_nsv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_dvaudio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_rgb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_mpeg2.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_matroska.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_mad.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_vo_out_syncfb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_inp_vcdo.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_spucmml.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_dxr3_spu.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_ao_out_pulseaudio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_a52.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_inp_pnm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_vorbis.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_inp_pvr.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_yuv4mpeg2.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_mpeg_ts.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_dmx_mng.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.4/xineplug_decode_spucc.so found
init class succeeded
params.c:OpenConfFile() - Unable to open configuration file "/home/drowland/.smb/smb.conf":
        No such file or directory
params.c:OpenConfFile() - Unable to open configuration file "/home/drowland/.smb/smb.conf.append":
        No such file or directory
Using netbios name CAMBRIA.
Using workgroup MSHOME.
video_out_xv: using Xv port 65 from adaptor NV Video Overlay for hardware colorspace conversion and scaling.
video_out_xv: double buffering mode = 1
video_out_xv: port attribute XV_COLORKEY (6) value is 66051
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
Segmentation fault (core dumped)
drowland@Cambria:~$

```
I can't seem to find anything useful on google or the forums.  Anyone got any help?

---

