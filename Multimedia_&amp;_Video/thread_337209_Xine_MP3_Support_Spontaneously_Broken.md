---
title: "Xine MP3 Support Spontaneously Broken"
date: 2007-01-12
forum: Multimedia &amp; Video
---

### Post by jamespi on 2007-01-12
The other day i tried to play an mp3 in totem and it said "no plugin found to handle this movie".

It worked fine the day before. I think i installed an update, but i cant remember what it was and i'm fairly sure it had nothing to do with multimedia but i just dont know.

It turns out it's a problem with libxine, becuase amarok and gxine (or is it xineui? the command to run it is just "xine") wont work either, and if i install totem-gstreamer i get mp3 support back.

the only trouble with totem-gstreamer is that the volume control in totem kills the sound if i touch it, so i reinstalled totem-xine with automatix 2.

so what do i do? i used xineui (or was it gxine?) to open an mp3 and looked at the debug messages; here is what its says (roughly, i cant copy and paste it):

```
xine:found demuxer plugin:Elementary MPEG Stream Demux plugin
xine:found input plugin: file input plugin
xine: couldnt find demux for >file://**path of the mp3**
xine:found input plugin: file input plugin
video_out: throwing away image with pts 291479 becuase it's too old (diff:82961)
****8 more lines as above
xine:found demuxer plugin:Elementary MPEG Stream Demux plugin
xine:found input plugin: file input plugin
```

then on the "plugins" tab it has a massive list of plugins with "found" written next to them, with the following at the bottom:

```
load_plugins:skipping unreadable plugin directory /home/jamespi/.xine/plugins
```

i had a look in the .xine folder and there is no plugins directory.

does anyone have the faintest idea what s happening as i'm totally stuck.
here is the directory listing of /usr/lib/xine/plugins/1.1.2
```

jamespi@hal9000:~$ ls -l /usr/lib/xine/plugins/1.1.2
total 6056
drwxr-xr-x 2 root root    4096 2006-12-14 23:24 post
drwxr-xr-x 2 root root    4096 2006-12-14 23:24 vidix
-rw-r--r-- 1 root root   32088 2006-12-02 01:50 xineplug_ao_out_alsa.so
-rw-r--r-- 1 root root    6120 2006-12-02 01:50 xineplug_ao_out_arts.so
-rw-r--r-- 1 root root    8840 2006-12-02 01:50 xineplug_ao_out_esd.so
-rw-r--r-- 1 root root    6152 2006-12-02 01:50 xineplug_ao_out_file.so
-rw-r--r-- 1 root root    4068 2006-12-02 01:50 xineplug_ao_out_none.so
-rw-r--r-- 1 root root   19528 2006-12-02 01:50 xineplug_ao_out_oss.so
-rw-r--r-- 1 root root   48416 2006-12-02 01:50 xineplug_decode_a52.so
-rw-r--r-- 1 root root   87820 2006-12-02 01:50 xineplug_decode_bitplane.so
-rw-r--r-- 1 root root  156264 2006-12-02 01:50 xineplug_decode_dts.so
-rw-r--r-- 1 root root   16016 2006-12-02 01:50 xineplug_decode_dxr3_spu.so
-rw-r--r-- 1 root root   12828 2006-12-02 01:50 xineplug_decode_dxr3_video.so
-rw-r--r-- 1 root root  297112 2006-07-14 04:45 xineplug_decode_faad.so
-rw-r--r-- 1 root root 2334752 2006-07-14 04:45 xineplug_decode_ff.so
-rw-r--r-- 1 root root   71468 2006-12-02 01:50 xineplug_decode_gsm610.so
-rw-r--r-- 1 root root    4856 2006-12-02 01:50 xineplug_decode_lpcm.so
-rw-r--r-- 1 root root    6172 2006-07-14 04:45 xineplug_decode_mad.so
-rw-r--r-- 1 root root   64252 2006-12-02 01:50 xineplug_decode_mpc.so
-rw-r--r-- 1 root root  113592 2006-12-02 01:50 xineplug_decode_mpeg2.so
-rw-r--r-- 1 root root   84408 2006-12-02 01:50 xineplug_decode_nsf.so
-rw-r--r-- 1 root root  118956 2006-12-02 01:50 xineplug_decode_qt.so
-rw-r--r-- 1 root root   11472 2006-12-02 01:50 xineplug_decode_real_audio.so
-rw-r--r-- 1 root root   10644 2006-12-02 01:50 xineplug_decode_real.so
-rw-r--r-- 1 root root    7540 2006-12-02 01:50 xineplug_decode_rgb.so
-rw-r--r-- 1 root root    7492 2006-12-02 01:50 xineplug_decode_speex.so
-rw-r--r-- 1 root root   15788 2006-12-02 01:50 xineplug_decode_spucc.so
-rw-r--r-- 1 root root    7620 2006-12-02 01:50 xineplug_decode_spucmml.so
-rw-r--r-- 1 root root   11060 2006-12-02 01:50 xineplug_decode_spudvb.so
-rw-r--r-- 1 root root   18452 2006-12-02 01:50 xineplug_decode_spu.so
-rw-r--r-- 1 root root   16368 2006-12-02 01:50 xineplug_decode_sputext.so
-rw-r--r-- 1 root root    7280 2006-12-02 01:50 xineplug_decode_theora.so
-rw-r--r-- 1 root root    6440 2006-12-02 01:50 xineplug_decode_vorbis.so
-rw-r--r-- 1 root root  159876 2006-12-02 01:50 xineplug_decode_w32dll.so
-rw-r--r-- 1 root root    5820 2006-12-02 01:50 xineplug_decode_yuv.so
-rw-r--r-- 1 root root   39364 2006-12-02 01:50 xineplug_dmx_asf.so
-rw-r--r-- 1 root root   61252 2006-12-02 01:50 xineplug_dmx_audio.so
-rw-r--r-- 1 root root   27584 2006-12-02 01:50 xineplug_dmx_avi.so
-rw-r--r-- 1 root root    6428 2006-12-02 01:50 xineplug_dmx_fli.so
-rw-r--r-- 1 root root    5720 2006-12-02 01:50 xineplug_dmx_flv.so
-rw-r--r-- 1 root root   45364 2006-12-02 01:50 xineplug_dmx_games.so
-rw-r--r-- 1 root root   21596 2006-12-02 01:50 xineplug_dmx_iff.so
-rw-r--r-- 1 root root   33928 2006-12-02 01:50 xineplug_dmx_matroska.so
-rw-r--r-- 1 root root    6924 2006-12-02 01:50 xineplug_dmx_mng.so
-rw-r--r-- 1 root root   15740 2006-12-02 01:50 xineplug_dmx_mpeg_block.so
-rw-r--r-- 1 root root    5100 2006-12-02 01:50 xineplug_dmx_mpeg_elem.so
-rw-r--r-- 1 root root   18080 2006-12-02 01:50 xineplug_dmx_mpeg_pes.so
-rw-r--r-- 1 root root   20164 2006-12-02 01:50 xineplug_dmx_mpeg.so
-rw-r--r-- 1 root root   18936 2006-12-02 01:50 xineplug_dmx_mpeg_ts.so
-rw-r--r-- 1 root root    8004 2006-12-02 01:50 xineplug_dmx_nsv.so
-rw-r--r-- 1 root root   31508 2006-12-02 01:50 xineplug_dmx_ogg.so
-rw-r--r-- 1 root root    7552 2006-12-02 01:50 xineplug_dmx_pva.so
-rw-r--r-- 1 root root   27580 2006-12-02 01:50 xineplug_dmx_qt.so
-rw-r--r-- 1 root root    8012 2006-12-02 01:50 xineplug_dmx_rawdv.so
-rw-r--r-- 1 root root   18356 2006-12-02 01:50 xineplug_dmx_real.so
-rw-r--r-- 1 root root    7440 2006-12-02 01:50 xineplug_dmx_slave.so
-rw-r--r-- 1 root root   24660 2006-12-02 01:50 xineplug_dmx_sputext.so
-rw-r--r-- 1 root root    7504 2006-12-02 01:50 xineplug_dmx_yuv4mpeg2.so
-rw-r--r-- 1 root root    4448 2006-12-02 01:50 xineplug_dmx_yuv_frames.so
-rw-r--r-- 1 root root   12852 2006-12-02 01:50 xineplug_flac.so
-rw-r--r-- 1 root root   34716 2006-12-02 01:50 xineplug_inp_cdda.so
-rw-r--r-- 1 root root   62144 2006-12-02 01:50 xineplug_inp_dvb.so
-rw-r--r-- 1 root root  171324 2006-12-02 01:50 xineplug_inp_dvd.so
-rw-r--r-- 1 root root   15884 2006-12-02 01:50 xineplug_inp_file.so
-rw-r--r-- 1 root root   15116 2006-12-02 01:50 xineplug_inp_gnome_vfs.so
-rw-r--r-- 1 root root   27152 2006-12-02 01:50 xineplug_inp_http.so
-rw-r--r-- 1 root root   40384 2006-12-02 01:50 xineplug_inp_mms.so
-rw-r--r-- 1 root root   15136 2006-12-02 01:50 xineplug_inp_net.so
-rw-r--r-- 1 root root   19508 2006-12-02 01:50 xineplug_inp_pnm.so
-rw-r--r-- 1 root root   20664 2006-12-02 01:50 xineplug_inp_pvr.so
-rw-r--r-- 1 root root   17564 2006-12-02 01:50 xineplug_inp_rtp.so
-rw-r--r-- 1 root root   49088 2006-12-02 01:50 xineplug_inp_rtsp.so
-rw-r--r-- 1 root root   11268 2006-12-02 01:50 xineplug_inp_smb.so
-rw-r--r-- 1 root root   14376 2006-12-02 01:50 xineplug_inp_stdin_fifo.so
-rw-r--r-- 1 root root   23068 2006-12-02 01:50 xineplug_inp_v4l.so
-rw-r--r-- 1 root root   12392 2006-12-02 01:50 xineplug_inp_vcdo.so
-rw-r--r-- 1 root root  326308 2006-12-02 01:50 xineplug_inp_vcd.so
-rw-r--r-- 1 root root    5852 2006-12-02 01:50 xineplug_vo_out_aa.so
-rw-r--r-- 1 root root   62592 2006-12-02 01:50 xineplug_vo_out_caca.so
-rw-r--r-- 1 root root   44916 2006-12-02 01:50 xineplug_vo_out_dxr3.so
-rw-r--r-- 1 root root   69808 2006-12-02 01:50 xineplug_vo_out_fb.so
-rw-r--r-- 1 root root    4808 2006-12-02 01:50 xineplug_vo_out_none.so
-rw-r--r-- 1 root root   94580 2006-12-02 01:50 xineplug_vo_out_opengl.so
-rw-r--r-- 1 root root    9884 2006-12-02 01:50 xineplug_vo_out_sdl.so
-rw-r--r-- 1 root root  318872 2006-12-02 01:50 xineplug_vo_out_vidix.so
-rw-r--r-- 1 root root   80200 2006-12-02 01:50 xineplug_vo_out_xshm.so
-rw-r--r-- 1 root root   25736 2006-12-02 01:50 xineplug_vo_out_xvmc.so
-rw-r--r-- 1 root root   35944 2006-12-02 01:50 xineplug_vo_out_xv.so
-rw-r--r-- 1 root root   57800 2006-12-02 01:50 xineplug_vo_out_xxmc.so

```

---

### Post by brian.baggett on 2007-01-12
I had the same problem (seen [here]("http://ubuntuforums.org/showthread.php?t=333728")). Removing my .xine directory from my home directory and then reinstalling totem-xine seems to have cleared it up though I've no idea why.

--
Brian

---

### Post by jamespi on 2007-01-14
i found that just deleting the .xine folder worked. that might be because i had already reinstalled xine about 3 times beforehand though.

---

### Post by kobewan on 2007-02-08
Just fixed the same problem on my computer. Deleting the .xine folder works just fine, but I wanted to save my settings so I backed it up. It turns out that the only two files  that you need to delete are file 'win32registry' and 'catalog.cache' in the .xine folder. I copied back the following files successfully:

config
keymap
skins  (which is a folder)
xine-ui_old_playlist.tox

So all my settings were saved.

---

### Post by kswenson on 2007-08-04
Wanted to bump this message because I just ran into the same problem and this is still the fix...
      BING.

---

### Post by lhomme on 2007-09-28
Same problem, xine (and all things that use it - amarok...)  randomly decided that there was no demuxer for .ogg and .mp3 (those were the only 2 I tried). I ran some updates the other day, but nothing xine related.

Anywho kobewan's fix worked just fine.

Weird

---

