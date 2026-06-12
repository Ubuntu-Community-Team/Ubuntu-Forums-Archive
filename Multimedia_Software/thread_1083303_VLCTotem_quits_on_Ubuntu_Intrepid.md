---
title: "VLC/Totem quits on Ubuntu Intrepid"
date: 2009-02-28
forum: Multimedia Software
---

### Post by covertops808 on 2009-02-28
I'm running Ubuntu Intrepid 32-bit on an AMD64 Turion laptop. When ever I try to play a DVD, weather through VLC or Totem, both programs just close. I got some info from another place that I should add NOPHET to the kernel line on the the boot/grub screen. Did that. But nothing I've tried has fixed the problem yet..

When I run the program with vlc -vvv in a terminal. I go to run a dvd, and get the following output...

[00000405] qt4 interface debug: New item: dvd:///dev/scd0
[00000371] main playlist debug: adding item `dvd:///dev/scd0' ( dvd:///dev/scd0 )
[00000371] main playlist debug: rebuilding array of current - root Playlist
[00000371] main playlist debug: rebuild done - 1 items, index -1
[00000371] main playlist debug: starting new item
[00000371] main playlist debug: processing request item dvd:///dev/scd0 node null skip 0
[00000371] main playlist debug: resyncing on dvd:///dev/scd0
[00000371] main playlist debug: dvd:///dev/scd0 is at 0
[00000371] main playlist debug: creating new input thread
[00000409] main input debug: Creating an input for 'dvd:///dev/scd0'
[00000409] main input debug: waiting for thread initialization
[00000409] main input debug: thread started
[00000409] main input debug: `dvd:///dev/scd0' gives access `dvd' demux `' path `/dev/scd0'
[00000409] main input debug: creating demux: access='dvd' demux='' path='/dev/scd0'
[00000410] main demux debug: looking for access_demux module: 2 candidates
[00000409] main input debug: thread 2955656080 (input) created at priority 10 (input/input.c:370)
[00000405] qt4 interface debug: Updating the stream status: 3
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: Hancock
libdvdnav: DVD Serial Number: 392d7b17
libdvdnav: DVD Title (Alternative): Hancock
libdvdnav: Unable to find map file '/home/shanon/.dvdnav/Hancock.map'
*** Zero check failed in ifo_read.c:439
    for vmgi_mat->zero_6 = 0x0000001900000000000000000000000000000000000000000000000000000000
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4
[00000410] dvdnav demux debug: trying to go to dvd menu
[00000412] main generic debug: thread 2945448848 (dvdnav event thread handler) created at priority 0 (dvdnav.c:351)
[00000410] main demux debug: using access_demux module "dvdnav"
[00000410] main demux debug: TIMER module_Need() : 171.257 ms - Total 171.257 ms / 1 intvls (Avg 171.257 ms)
[00000412] main generic debug: thread started
[00000409] main input debug: `dvd:///dev/scd0' successfully opened
[00000410] dvdnav demux debug: DVDNAV_HOP_CHANNEL
[00000409] main input debug: control type=1
[00000410] dvdnav demux debug: DVDNAV_VTS_CHANGE
[00000410] dvdnav demux debug:      - vtsN=1
[00000410] dvdnav demux debug:      - domain=8
[00000410] dvdnav demux debug: DVDNAV_CELL_CHANGE
[00000410] dvdnav demux debug:      - cellN=1
[00000410] dvdnav demux debug:      - pgN=1
[00000410] dvdnav demux debug:      - cell_length=5196000
[00000410] dvdnav demux debug:      - pg_length=5196000
[00000410] dvdnav demux debug:      - pgc_length=5196000
[00000410] dvdnav demux debug:      - cell_start=0
[00000410] dvdnav demux debug:      - pg_start=0
[00000410] dvdnav demux debug: DVDNAV_SPU_CLUT_CHANGE
[00000410] dvdnav demux debug: DVDNAV_SPU_STREAM_CHANGE
[00000410] dvdnav demux debug:      - physical_wide=0
[00000410] dvdnav demux debug:      - physical_letterbox=0
[00000410] dvdnav demux debug:      - physical_pan_scan=1
[00000410] dvdnav demux debug: buttonUpdate not done b=1 t=0
[00000409] main input debug: selecting program id=0
[00000413] main decoder debug: looking for decoder module: 30 candidates
[00000405] qt4 interface debug: New Event: type 1103
[00000405] qt4 interface debug: Updating the stream status: 3
[00000405] qt4 interface debug: New Event: type 1108
[00000413] main decoder debug: using decoder module "spudec"
[00000413] main decoder debug: TIMER module_Need() : 344.428 ms - Total 344.428 ms / 1 intvls (Avg 344.428 ms)
[00000413] main decoder debug: thread 2923985808 (decoder) created at priority 0 (input/decoder.c:217)
[00000413] main decoder debug: thread started
[00000410] dvdnav demux debug: DVDNAV_AUDIO_STREAM_CHANGE
[00000410] dvdnav demux debug:      - physical=0
[00000410] dvdnav demux debug: buttonUpdate 1
[00000464] main decoder debug: looking for decoder module: 30 candidates
[00000464] main decoder debug: using decoder module "libmpeg2"
[00000464] main decoder debug: TIMER module_Need() : 0.748 ms - Total 0.748 ms / 1 intvls (Avg 0.748 ms)
[00000464] main decoder debug: thread 2913340304 (decoder) created at priority 0 (input/decoder.c:217)
[00000464] main decoder debug: thread started
[00000410] dvdnav demux debug: buttonUpdate 1
[00000464] libmpeg2 decoder debug: 720x480 (display 540,480), aspect 768000, sar 0:0, 29.971 fps
[00000464] main decoder debug: no usable vout present, spawning one
[00000409] main input debug: crop: 116,363,242,38, palette forced: 1
[00000465] main video output debug: window size: 853x480
[00000465] main video output debug: looking for video output module: 6 candidates
[00000409] main input debug: idx1=-1(??) idx2=-1(??)
[00000465] xvideo video output debug: adaptor 0, port 57, format 0x32315659 (YV12) planar
[00000468] main window debug: looking for vout window module: 2 candidates
[00000469] main decoder debug: looking for decoder module: 30 candidates
[00000469] main decoder debug: using decoder module "a52"
[00000469] main decoder debug: TIMER module_Need() : 5.798 ms - Total 5.798 ms / 1 intvls (Avg 5.798 ms)
[00000469] main decoder debug: thread started
[00000469] main decoder debug: thread 2903829392 (decoder) created at priority 5 (input/decoder.c:217)
[00000469] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[00000469] main decoder debug: no aout present, spawning one
[00000470] main audio output debug: looking for audio output module: 4 candidates
[00000468] qt4 window debug: waiting for interface...
[00000468] qt4 window debug: requesting window...
[00000405] qt4 interface debug: Video was requested -1, -1
[00000405] qt4 interface debug: Video is resizing to: 853 480
[00000405] qt4 interface debug: Updating the geometry
[00000465] qt4 video output debug: Qt FS: Attaching Vout
[00000465] qt4 video output debug: Qt: Changing Fullscreen Mode
[00000468] main window debug: using vout window module "qt4"
[00000468] main window debug: TIMER module_Need() : 91.392 ms - Total 91.392 ms / 1 intvls (Avg 91.392 ms)
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[00000465] xvideo video output debug: XShm video extension v1.1 (with pixmaps, opcode: 145)
[00000465] xvideo video output debug: Window manager supports NetWM
[00000465] xvideo video output debug: Window manager supports _NET_WM_STATE_FULLSCREEN
[00000465] xvideo video output debug: Window manager supports _NET_WM_STATE_ABOVE
[00000465] xvideo video output debug: Window manager supports _NET_WM_STATE_BELOW
[00000465] main video output debug: using video output module "xvideo"
[00000465] main video output debug: TIMER module_Need() : 557.261 ms - Total 557.261 ms / 1 intvls (Avg 557.261 ms)
[00000465] main video output debug: waiting for thread initialization
[00000465] main video output debug: thread started
[00000470] alsa audio output debug: opening ALSA device `default'
[00000465] main video output debug: got 8 direct buffer(s)
[00000465] main video output debug: picture in 720x480 (0,0,720x480), chroma I420, ar 16:9, sar 32:27
[00000465] main video output debug: picture user 720x480 (0,0,720x480), chroma I420, ar 16:9, sar 32:27
[00000465] main video output debug: picture out 720x480 (0,0,720x480), chroma I420, ar 16:9, sar 32:27
[00000465] main video output debug: direct render, mapping render pictures 0-6 to system pictures 1-7
[00000465] main video output debug: thread 2893650832 (video output) created at priority 15 (video_output/video_output.c:504)
[00000405] qt4 interface debug: New Event: type 1109
[00000464] main decoder warning: dts != current_pts (419144)
[00000464] main decoder warning: backward_pts != current_pts (-33366)
[00000465] main video output warning: late picture skipped (121978)
[00000470] main audio output debug: thread 2869021584 (aout) created at priority 15 (alsa.c:687)
[00000470] main audio output debug: thread started
[00000470] main audio output debug: using audio output module "alsa"
[00000470] main audio output debug: TIMER module_Need() : 652.648 ms - Total 652.648 ms / 1 intvls (Avg 652.648 ms)
[00000470] main audio output debug: output 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
[00000470] main audio output debug: mixer 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
[00000470] main audio output debug: no need for any filter
[00000470] main audio output debug: looking for audio mixer module: 3 candidates
[00000470] main audio output debug: using audio mixer module "float32_mixer"
[00000470] main audio output debug: TIMER module_Need() : 14.879 ms - Total 14.879 ms / 1 intvls (Avg 14.879 ms)
[00000470] main audio output debug: input 'a52 ' 48000 Hz Stereo frame=1536 samples/768 bytes
[00000476] main spu text debug: looking for text renderer module: 2 candidates
[00000470] main audio output debug: filter(s) 'a52 '->'fl32' 48000 Hz->48000 Hz Stereo->Stereo
[00000477] main audio output debug: looking for audio filter module: 24 candidates
[00000479] main generic debug: thread started
[00000479] main generic debug: thread 2860628880 (fontlist builder) created at priority 0 (freetype.c:477)
[00000476] freetype spu text debug: using fontsize: 30
[00000476] main spu text debug: using text renderer module "freetype"
[00000476] main spu text debug: TIMER module_Need() : 18.516 ms - Total 18.516 ms / 1 intvls (Avg 18.516 ms)
[00000475] main blend debug: looking for video blending module: 1 candidate
[00000479] freetype generic debug: Building font database...
[00000477] main audio output debug: using audio filter module "a52tofloat32"
[00000477] main audio output debug: TIMER module_Need() : 25.762 ms - Total 25.762 ms / 1 intvls (Avg 25.762 ms)
[00000470] main audio output debug: found a filter for the whole conversion
[00000470] main audio output debug: filter(s) 'fl32'->'fl32' 52800 Hz->48000 Hz Stereo->Stereo
[00000484] main audio output debug: looking for audio filter module: 24 candidates
[00000479] freetype generic debug: Finished building font database.
[00000479] freetype generic debug: Took 0 seconds
[00000479] main generic debug: thread ended
[00000475] blend blend debug: chroma: YUVP -> I420
[00000475] main blend debug: using video blending module "blend"
[00000475] main blend debug: TIMER module_Need() : 41.865 ms - Total 41.865 ms / 1 intvls (Avg 41.865 ms)
[00000476] freetype spu text debug: using fontsize: 30
[00000484] main audio output debug: using audio filter module "bandlimited_resampler"
[00000484] main audio output debug: TIMER module_Need() : 34.320 ms - Total 34.320 ms / 1 intvls (Avg 34.320 ms)
[00000470] main audio output debug: found a filter for the whole conversion
[00000470] main audio output warning: PTS is out of range (365012), dropping buffer
[00000470] main audio output warning: PTS is out of range (333079), dropping buffer
[00000470] main audio output warning: PTS is out of range (301127), dropping buffer
[00000470] main audio output warning: PTS is out of range (269177), dropping buffer
[00000470] main audio output warning: PTS is out of range (237215), dropping buffer
[00000470] main audio output warning: PTS is out of range (205267), dropping buffer
[00000470] main audio output warning: PTS is out of range (173303), dropping buffer
[00000470] main audio output warning: PTS is out of range (141343), dropping buffer
[00000470] main audio output warning: PTS is out of range (109380), dropping buffer
[00000470] main audio output warning: PTS is out of range (77416), dropping buffer
[00000470] main audio output warning: PTS is out of range (45455), dropping buffer
[00000470] main audio output warning: PTS is out of range (13490), dropping buffer
[00000470] main audio output warning: PTS is out of range (-18474), dropping buffer
[00000475] main blend debug: removing module "blend"
[00000475] main blend debug: looking for video blending module: 1 candidate
[00000475] blend blend debug: chroma: YUVA -> I420
[00000475] main blend debug: using video blending module "blend"
[00000475] main blend debug: TIMER module_Need() : 0.265 ms - Total 0.265 ms / 1 intvls (Avg 0.265 ms)
[00000470] main audio output debug: audio output is starving (29993), playing silence
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  83
  Current serial number in output stream:  84

Can any one help?

---

