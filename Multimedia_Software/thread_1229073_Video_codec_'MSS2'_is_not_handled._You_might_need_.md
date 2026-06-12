---
title: "Video codec 'MSS2' is not handled. You might need to install additional plugins..."
date: 2009-08-01
forum: Multimedia Software
---

### Post by prs2ubu on 2009-08-01
Totem Movie Player v2.26.1
Movie Player using xine-lib version 1.1.16.3
Ubuntu v9.04 32 bit

Error message displayed by the Movie Player after opening the WMV file:

[B]Totem could not play '/home/kaska/Videos/ex236_04.wmv'.
Video codec 'MSS2' is not handled. You might need to install additional plugins to be able to play some types of movies

Result[/B] -- ex236_04.wmv file fails to open/play

launched **totem --debug** and attempted to play the ex236_04.wmv file:

kaska@laska:~$ totem --debug
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_rtsp.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_ogg.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_ogg.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_gsm610.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_spucc.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_mpeg_block.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_syncfb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_spudvb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_mpeg2.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_mpeg_elem.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_xshm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_xshm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_pnm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_vcd.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_cdda.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_ao_out_oss.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_v4l.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_v4l.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_mng.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_xvmc.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_sdl.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_yuv_frames.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_directfb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_image.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_aa.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_file.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_rawdv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_smb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_xv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_xv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_xcbxv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_ao_out_alsa.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_dxr3.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_dxr3.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_rgb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_http.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_opengl.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_stdin_fifo.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_caca.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_mad.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_ao_out_none.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_pva.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_fb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_sputext.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_flac.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_flac.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_mpeg.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_xxmc.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_iff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_image.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_real.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_real.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_net.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_asf.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_dvb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_spucmml.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_rtp.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_w32dll.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_w32dll.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_gdk_pixbuf.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_avi.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_vorbis.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_lpcm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_flv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_speex.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_fli.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_tvtime.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_mosaico.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_goom.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_switch.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_none.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_dvaudio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_mms.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_yuv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_dxr3_spu.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_wavpack.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_wavpack.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_theora.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_gnome_vfs.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_dts.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_xdirectfb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_xdirectfb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_nsv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_matroska.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_dxr3_video.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_ao_out_pulseaudio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_ao_out_file.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_spu.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_mpeg_pes.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_slave.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_vcdo.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_pvr.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_bitplane.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_dvd.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_ao_out_esd.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_sputext.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_xcbshm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_yuv4mpeg2.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_mpc.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_faad.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_real.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_mpeg_ts.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_a52.so found
init class succeeded
gnome_vfs init_input_class
gnome-vfs not initialised
params.c:OpenConfFile() - Unable to open configuration file "/home/kaska/.smb/smb.conf":
    No such file or directory
params.c:OpenConfFile() - Unable to open configuration file "/home/kaska/.smb/smb.conf.append":
    No such file or directory
Using netbios name LASKA.
Using workgroup WORKGROUP.
video_out_xv: using Xv port 57 from adaptor Radeon Textured Video for hardware colour space conversion and scaling.
video_out_xv: sync to vblank = 1
video_out_xv: this adaptor supports the yuy2 format.
video_out_xv: this adaptor supports the yv12 format.
x11osd: unscaled overlay created (XShape mode).
video_out: thread created
audio_pulse_out: host (null) sink (null)
audio_out: thread created
xine_stream_new
video_out_xv: VO_PROP_ZOOM_X = 100
video_out_xv: VO_PROP_ZOOM_Y = 100
load_plugins: no post plugin named GOOM: what a GOOM! found
video_out_xv: VO_PROP_INTERLACED(0)
libsputext: spu_src_encoding = utf-8
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
libsputext: spu_src_encoding = utf-8
video_out_xv: VO_PROP_ZOOM_X = 100
video_out_xv: VO_PROP_ZOOM_Y = 100
gnome_vfs init_input_class
gnome-vfs not initialised
xine: found input plugin  : file input plugin
load_plugins: probing demux 'anx'
load_plugins: probing demux 'image'
load_plugins: probing demux 'mpeg_block'
load_plugins: probing demux 'mng'
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
load_plugins: probing demux 'quicktime'
load_plugins: probing demux 'pva'
load_plugins: probing demux 'iff'
load_plugins: probing demux 'aud'
load_plugins: probing demux 'aiff'
load_plugins: probing demux 'flac'
load_plugins: probing demux 'realaudio'
load_plugins: probing demux 'snd'
load_plugins: probing demux 'tta'
load_plugins: probing demux 'voc'
load_plugins: probing demux 'vox'
load_plugins: probing demux 'mod'
TEST mod decode
load_plugins: probing demux 'asf'
xine: found demuxer plugin: ASF demux plugin
demux_asf: audio conceal interleave detected ( 1 x 1 x 1088 )
demux_asf: unknown video format MSS2
video discontinuity #1, type is 0, disc_off 0
waiting for audio discontinuity #1
audio discontinuity #1, type is 0, disc_off 0
waiting for in_discontinuity update #1
vpts adjusted with prebuffer to 332542
demux_asf: video stream_id: 2, audio stream_id: 1
load_plugins: plugin win32a will be used for audio streamtype 2e.
w32codec: increasing source buffer to 128 to avoid overflow.
audio_pulse_out: ao_open bits=16 rate=22050, mode=4
output sample rate 22050
GetOutput r=0x0   size:16384  align:1
StreamCount r=0x0  1  1
w32codec: output buffer size: 32768
w32codec: Recommended source buffer size: 8704
video_decoder: no plugin available to handle ''
input_cache: read calls: 40, main input read calls: 8
input_cache: seek_calls: 47, main input seek calls: 9


Thank you in advance

Pete

---

### Post by xc3RnbFO8P on 2009-08-01
Maybe this will help:
[http://ubuntuforums.org/showthread.php?t=356656]("http://ubuntuforums.org/showthread.php?t=356656")

---

### Post by andrew.46 on 2009-08-01
Hi prs2ubu,

> **prs2ubu said:**
> 
```
Totem could not play '/home/kaska/Videos/ex236_04.wmv'.
Video codec 'MSS2' is not handled. 
You might need to install additional plugins to be able to play 
some types of movies
```


I have bumped into these files before and I have a sample one stored:

```
wget http://samples.mplayerhq.hu/V-codecs/MSS2/intro_windows.wmv
```

which FFmpeg reveals as a stock standard asf container with the offending codec in place:

```
Input #0, asf, from 'intro_windows.wmv':
Duration: 00:01:45.80, start: 3.000000, bitrate: 141 kb/s
Stream #0.0(swe): Audio: wmav2, 44100 Hz, 1 channels, s16, 32 kb/s
**[COLOR="Red"]Stream #0.1(swe): Video: MSS2 / 0x3253534D, 800x548, 250 kb/s, 15 tbr, 1k tbn, 1k tbc[/COLOR]**
```

The good news is that MPlayer will play these files by using the external codec pack:

```
andrew@skamandros~/Desktop$ **[COLOR="Red"]mplayer -vc help | grep 'Windows Media Screen'[/COLOR]**
wmsdmod     dmo       working   Windows Media Screen Codec 2  [wmsdmod.dll]
```

and I attach a screenshot of the amazing SMPlayer frontend doing just that :-). So to cut a rambling story short you should be able to play these files with the MPlayer and w32codecs from Medibuntu :-). mc4man might be interested to see that even with the dmo-loader option vlc seems to fail with this file...

Andrew

---

### Post by mc4man on 2009-08-02
as Andrew mentioned mplayer with the win or w32codecs is your best and probably only decent option. (if you wanted to convert for more widespread playability then mencoder should work.

As far as vlc the file won't be rejected, it will either play audio only or segfault.
The fourcc has been in the code for quite some time (dmo), it just doesn't work

The tail end of this thread sums it up quite well

[https://trac.videolan.org/vlc/ticket/750](https://trac.videolan.org/vlc/ticket/750)

I wouldn't think xine based players would play unless ffmpeg could decode which it doesn't.

---

### Post by andrew.46 on 2009-08-02
Hi mc4man,

> **mc4man said:**
> 
The tail end of this thread sums it up quite well
[https://trac.videolan.org/vlc/ticket/750](https://trac.videolan.org/vlc/ticket/750)


I love it:

> *   milestone  changed from 1.0 bugs to Bugs paradize

When someone has time...

Andrew

---

### Post by piedro on 2009-11-03
Hi! 

I have the same problem, 
But: What is the "external codecs"? 

I tried with the essential codecs from the official mplayer site. 
They are dated 2007, In my /usr/lib/codecs directory the same files are already present with a file date of 2008. 

I replaced them, can play sound with both versions, But no video. 
I get the same infos using your commands. It says the codec should be handled. 

I'm using a fresh Karmic koala 64bit. 

And yes: Windows Mediaplayer in Virtualbox can play them. 

I have many files like that cause I'm member of a coaching site which uses these files for every single tutorial. So I really look for a solution. 

But I have to admit that I don't fully understand the whole multimediaframework-codecs-player context. But I would be glad to find a comprehensive guide.

Any ideas or solutions, 
thx a lot, 
p.

---

### Post by mc4man on 2009-11-03
> I'm using a fresh Karmic koala 64bit. 

There are only a couple of realmedia codecs in the 64bit version of the codecs ( whether from mplayer site or from w64codecs

So for an 64 bit install you'd need to either build/install a 32 bit mplayer or run a windows mplayer build thru wine ( as far as mss2 files

---

### Post by piedro on 2009-11-03
thx mc4 for your answer. 

Now i see the problem. Are there any plans to fix this soon? 
Running mplayer through Wine might be an option though ugly. 

Is it possible to have a mplayer-32bit next to the mplayer-64bit? 
I have no clue how to do that ... 

thx anyway, 
piedro 

p.s.: I will check out a Virtualbox with mplayer to find out whether the Wine-Solution works by the player first ...

---

### Post by mc4man on 2009-11-03
> Are there any plans to fix this soon? 
If no one has 'converted' the win codecs to 64 bit .so's by now then I doubt it will be forthcoming.


> Running mplayer through Wine might be an option though ugly.

Is it possible to have a mplayer-32bit next to the mplayer-64bit?
I have no clue how to do that ... 


see here for some info on a win player in wine ( limited use

As far as side by side mplayers, don't know, (would think you'd only want one.

Can track down how I built it on a jaunty live cd, wasn't that difficult, a few bumps so to speak

[http://ubuntuforums.org/showthread.php?p=8191113#post8191113](http://ubuntuforums.org/showthread.php?p=8191113#post8191113)

---

