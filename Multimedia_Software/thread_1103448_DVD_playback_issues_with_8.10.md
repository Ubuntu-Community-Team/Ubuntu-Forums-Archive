---
title: "DVD playback issues with 8.10"
date: 2009-03-22
forum: Multimedia Software
---

### Post by seamusandboo on 2009-03-22
So here's the problem. I have just done a fresh install of Ubuntu Intrepid Ibex on my laptop and everything went well. I wanted to enable DVD playback on this laptop so I followed the instructions on [this]("https://help.ubuntu.com/8.10/musicvideophotos/C/video.html#video-dvd") page on how to enable DVD playback. Did that but when I tried playing a commercial DVD with Movie Player, I got a message saying "Could not read from resource". So I then installed the "GStreamer ffmpeg video plugin" and "Ubuntu restricted extras" packages.

After I installed those I've had some success. It plays the menus and some of the little logos before the movie, but when the movie itself is supposed to start, I get that "Could not read from resource" message again. I've tried many different DVDs and it's the same with all of them.

I've tried installing VLC player to see if that would work, and I get something similar... It will play the menus, I can select the settings and all, but when the movie is supposed to start it simply stops the playback.

Is there something I'm missing here? This laptop played DVDs before with Ubuntu 8.04 without any problems. How can I fix this?

Thank you.

---

### Post by lisati on 2009-03-22
Many commercially produced DVDs are encrypted. Some information on how to play them can be cound here: [https://help.ubuntu.com/8.10/musicvideophotos/C/video.html](https://help.ubuntu.com/8.10/musicvideophotos/C/video.html)

Edit: I see you've been there. Have you done this yet?
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by mc4man on 2009-03-22
Did you install libdvdcss2?
Available in medibuntu repo or this should install it for you
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by seamusandboo on 2009-03-22
Yeah, well, I guess you didn't read my previous post thoroughly, but I already followed those instructions and I am still having problems.

---

### Post by mc4man on 2009-03-22
Missed that little link button, try starting vlc from the terminal with
```
vlc -vvv
```

---

### Post by seamusandboo on 2009-03-22
Ok, I ran:

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

in the terminal, no luck.

Then I opened the terminal and ran vlc -vvv. It opened VLC, I opened the disk, the menus came up, selected play movie and it stopped just like before. But here's what the terminal spits up:

```
[00000484] blend blend debug: chroma: YUVP -> I420
[00000484] main blend debug: using video blending module "blend"
[00000484] main blend debug: TIMER module_Need() : 0.419 ms - Total 0.419 ms / 1 intvls (Avg 0.419 ms)
[00000484] main blend debug: removing module "blend"
[00000484] main blend debug: looking for video blending module: 1 candidate
[00000484] blend blend debug: chroma: YUVA -> I420
[00000484] main blend debug: using video blending module "blend"
[00000484] main blend debug: TIMER module_Need() : 0.191 ms - Total 0.191 ms / 1 intvls (Avg 0.191 ms)
[00000484] main blend debug: removing module "blend"
[00000484] main blend debug: looking for video blending module: 1 candidate
[00000484] blend blend debug: chroma: YUVP -> I420
[00000484] main blend debug: using video blending module "blend"
[00000484] main blend debug: TIMER module_Need() : 0.349 ms - Total 0.349 ms / 1 intvls (Avg 0.349 ms)
[00000484] main blend debug: removing module "blend"
[00000484] main blend debug: looking for video blending module: 1 candidate
[00000484] blend blend debug: chroma: YUVA -> I420
[00000484] main blend debug: using video blending module "blend"
[00000484] main blend debug: TIMER module_Need() : 0.198 ms - Total 0.198 ms / 1 intvls (Avg 0.198 ms)
[00000484] main blend debug: removing module "blend"
[00000484] main blend debug: looking for video blending module: 1 candidate
[00000484] blend blend debug: chroma: YUVP -> I420
[00000484] main blend debug: using video blending module "blend"
[00000484] main blend debug: TIMER module_Need() : 0.345 ms - Total 0.345 ms / 1 intvls (Avg 0.345 ms)
[00000484] main blend debug: removing module "blend"
[00000484] main blend debug: looking for video blending module: 1 candidate
[00000484] blend blend debug: chroma: YUVA -> I420
[00000484] main blend debug: using video blending module "blend"
[00000484] main blend debug: TIMER module_Need() : 0.186 ms - Total 0.186 ms / 1 intvls (Avg 0.186 ms)
[00000484] main blend debug: removing module "blend"
[00000484] main blend debug: looking for video blending module: 1 candidate
[00000484] blend blend debug: chroma: YUVP -> I420
[00000484] main blend debug: using video blending module "blend"
[00000484] main blend debug: TIMER module_Need() : 0.349 ms - Total 0.349 ms / 1 intvls (Avg 0.349 ms)
[00000484] main blend debug: removing module "blend"
[00000484] main blend debug: looking for video blending module: 1 candidate
[00000484] blend blend debug: chroma: YUVA -> I420
[00000484] main blend debug: using video blending module "blend"
[00000484] main blend debug: TIMER module_Need() : 0.186 ms - Total 0.186 ms / 1 intvls (Avg 0.186 ms)
[00000484] main blend debug: removing module "blend"
[00000484] main blend debug: looking for video blending module: 1 candidate
[00000484] blend blend debug: chroma: YUVP -> I420
[00000484] main blend debug: using video blending module "blend"
[00000484] main blend debug: TIMER module_Need() : 0.374 ms - Total 0.374 ms / 1 intvls (Avg 0.374 ms)
[00000484] main blend debug: removing module "blend"
[00000484] main blend debug: looking for video blending module: 1 candidate
[00000484] blend blend debug: chroma: YUVA -> I420
[00000484] main blend debug: using video blending module "blend"
[00000484] main blend debug: TIMER module_Need() : 0.191 ms - Total 0.191 ms / 1 intvls (Avg 0.191 ms)
[00000408] main input debug: crop: 152,116,463,135, palette forced: 1
[00000409] dvdnav demux debug: buttonUpdate 1
[00000409] dvdnav demux debug: DVDNAV_HOP_CHANNEL
[00000409] dvdnav demux debug: DVDNAV_CELL_CHANGE
[00000409] dvdnav demux debug:      - cellN=1
[00000409] dvdnav demux debug:      - pgN=1
[00000409] dvdnav demux debug:      - cell_length=3816000
[00000409] dvdnav demux debug:      - pg_length=3816000
[00000409] dvdnav demux debug:      - pgc_length=3816000
[00000409] dvdnav demux debug:      - cell_start=0
[00000409] dvdnav demux debug:      - pg_start=0
[00000409] dvdnav demux debug: DVDNAV_SPU_CLUT_CHANGE
[00000409] dvdnav demux debug: DVDNAV_SPU_STREAM_CHANGE
[00000409] dvdnav demux debug:      - physical_wide=0
[00000409] dvdnav demux debug:      - physical_letterbox=1
[00000409] dvdnav demux debug:      - physical_pan_scan=0
[00000408] main input debug: crop: 152,116,463,135, palette forced: 1
[00000409] dvdnav demux debug: buttonUpdate 1
[00000412] main decoder debug: removing module "spudec"
[00000412] main decoder debug: thread ended
[00000412] main decoder debug: thread 2926029712 joined (input/decoder.c:248)
[00000412] main decoder debug: killing decoder fourcc `spu ', 0 PES in FIFO
[00000489] main decoder debug: looking for decoder module: 30 candidates
[00000489] main decoder debug: using decoder module "spudec"
[00000489] main decoder debug: TIMER module_Need() : 0.502 ms - Total 0.502 ms / 1 intvls (Avg 0.502 ms)
[00000489] main decoder debug: thread started
[00000489] main decoder debug: thread 2926029712 (decoder) created at priority 0 (input/decoder.c:217)
[00000409] dvdnav demux debug: DVDNAV_AUDIO_STREAM_CHANGE
[00000409] dvdnav demux debug:      - physical=0
[00000463] main decoder debug: decoded 94/106 pictures
[00000409] dvdnav demux debug: buttonUpdate not done b=1 t=0
[00000469] alsa audio output debug: recovered from buffer underrun
[00000468] a52 decoder debug: emulated sync word (no sync on following frame)
[00000469] main audio output warning: computed PTS is out of range (87369), clearing out
[00000469] main audio output warning: PTS is out of range (87398), dropping buffer
[00000469] main audio output warning: output PTS is out of range (98087), clearing out
[00000469] main audio output debug: audio output is starving (324075), playing silence
[00000463] main decoder warning: dts != current_pts (-74480)
[00000484] main blend debug: removing module "blend"
[00000484] main blend debug: looking for video blending module: 1 candidate
[00000484] blend blend debug: chroma: YUVP -> I420
[00000484] main blend debug: using video blending module "blend"
[00000484] main blend debug: TIMER module_Need() : 0.814 ms - Total 0.814 ms / 1 intvls (Avg 0.814 ms)
[00000408] main input debug: crop: 177,158,228,54, palette forced: 1
[00000409] dvdnav demux debug: buttonUpdate 1
[00000409] dvdnav demux debug: DVDNAV_HOP_CHANNEL
[00000409] dvdnav demux debug: DVDNAV_CELL_CHANGE
[00000409] dvdnav demux debug:      - cellN=1
[00000409] dvdnav demux debug:      - pgN=1
[00000409] dvdnav demux debug:      - cell_length=360000
[00000409] dvdnav demux debug:      - pg_length=360000
[00000409] dvdnav demux debug:      - pgc_length=360000
[00000409] dvdnav demux debug:      - cell_start=0
[00000409] dvdnav demux debug:      - pg_start=0
[00000409] dvdnav demux debug: DVDNAV_SPU_CLUT_CHANGE
[00000409] dvdnav demux debug: DVDNAV_SPU_STREAM_CHANGE
[00000409] dvdnav demux debug:      - physical_wide=0
[00000409] dvdnav demux debug:      - physical_letterbox=0
[00000409] dvdnav demux debug:      - physical_pan_scan=0
[00000408] main input debug: crop: 177,158,228,54, palette forced: 1
[00000409] dvdnav demux debug: buttonUpdate 1
[00000489] main decoder debug: removing module "spudec"
[00000489] main decoder debug: thread ended
[00000489] main decoder debug: thread 2926029712 joined (input/decoder.c:248)
[00000489] main decoder debug: killing decoder fourcc `spu ', 0 PES in FIFO
[00000490] main decoder debug: looking for decoder module: 30 candidates
[00000490] main decoder debug: using decoder module "spudec"
[00000490] main decoder debug: TIMER module_Need() : 0.597 ms - Total 0.597 ms / 1 intvls (Avg 0.597 ms)
[00000490] main decoder debug: thread started
[00000490] main decoder debug: thread 2926029712 (decoder) created at priority 0 (input/decoder.c:217)
[00000409] dvdnav demux debug: DVDNAV_AUDIO_STREAM_CHANGE
[00000409] dvdnav demux debug:      - physical=0
[00000469] alsa audio output debug: recovered from buffer underrun
[00000409] dvdnav demux debug: buttonUpdate not done b=1 t=0
[00000463] main decoder warning: dts != current_pts (-289815)
[00000468] a52 decoder debug: emulated sync word (no sync on following frame)
[00000469] main audio output warning: computed PTS is out of range (267930), clearing out
[00000469] main audio output warning: PTS is out of range (236013), dropping buffer
[00000469] main audio output warning: output PTS is out of range (268086), clearing out
[00000469] main audio output debug: audio output is starving (216271), playing silence
[00000469] alsa audio output debug: recovered from buffer underrun
[00000409] dvdnav demux debug: DVDNAV_NOP
[00000409] dvdnav demux debug: DVDNAV_VTS_CHANGE
[00000409] dvdnav demux debug:      - vtsN=2
[00000409] dvdnav demux debug:      - domain=2
[00000463] main decoder debug: removing module "libmpeg2"
[00000463] main decoder debug: thread ended
[00000463] main decoder debug: thread 2915384208 joined (input/decoder.c:248)
[00000463] main decoder debug: killing decoder fourcc `mpgv', 1 PES in FIFO
[00000484] main blend debug: removing module "blend"
[00000487] main generic debug: thread 2874211216 joined (freetype.c:511)
[00000485] main spu text debug: removing module "freetype"
[00000464] main video output debug: thread ended
[00000464] main video output debug: thread 2887699344 joined (video_output/video_output.c:536)
[00000464] qt4 video output debug: Qt FS: Detaching Vout
[00000464] qt4 video output debug: Qt: Changing Fullscreen Mode
[00000404] qt4 interface debug: Video is not needed anymore
[00000404] qt4 interface debug: Updating the geometry
[00000467] main window debug: removing module "qt4"
[00000464] main video output debug: removing module "xvideo"
[00000490] main decoder debug: removing module "spudec"
[00000490] main decoder debug: thread ended
[00000490] main decoder debug: thread 2926029712 joined (input/decoder.c:248)
[00000490] main decoder debug: killing decoder fourcc `spu ', 0 PES in FIFO
[00000468] main decoder debug: removing module "a52"
[00000468] main decoder debug: thread ended
[00000468] main decoder debug: thread 2905873296 joined (input/decoder.c:248)
[00000468] main decoder debug: killing decoder fourcc `a52 ', 0 PES in FIFO
[00000474] main audio output debug: removing module "a52tofloat32"
[00000479] main audio output debug: removing module "bandlimited_resampler"
[00000404] qt4 interface debug: New Event: type 1109
[00000469] main audio output debug: thread ended
[00000469] main audio output debug: thread 2896153488 joined (alsa.c:742)
[00000469] main audio output debug: removing module "alsa"
[00000469] main audio output debug: removing module "float32_mixer"
[00000408] main input debug: Program doesn't contain anymore ES
[00000409] dvdnav demux debug: DVDNAV_CELL_CHANGE
[00000409] dvdnav demux debug:      - cellN=1
[00000409] dvdnav demux debug:      - pgN=1
[00000409] dvdnav demux debug:      - cell_length=1260000
[00000409] dvdnav demux debug:      - pg_length=11160000
[00000409] dvdnav demux debug:      - pgc_length=833016000
[00000409] dvdnav demux debug:      - cell_start=0
[00000409] dvdnav demux debug:      - pg_start=0
[00000409] dvdnav demux debug: DVDNAV_SPU_CLUT_CHANGE
[00000409] dvdnav demux debug: DVDNAV_SPU_STREAM_CHANGE
[00000409] dvdnav demux debug:      - physical_wide=128
[00000409] dvdnav demux debug:      - physical_letterbox=129
[00000409] dvdnav demux debug:      - physical_pan_scan=128
[00000409] dvdnav demux debug: buttonUpdate not done b=1 t=1
[00000409] dvdnav demux debug: DVDNAV_AUDIO_STREAM_CHANGE
[00000409] dvdnav demux debug:      - physical=0
[00000409] dvdnav demux debug: buttonUpdate not done b=1 t=1
[00000491] main decoder debug: looking for decoder module: 30 candidates
[00000491] main decoder debug: using decoder module "libmpeg2"
[00000491] main decoder debug: TIMER module_Need() : 1.059 ms - Total 1.059 ms / 1 intvls (Avg 1.059 ms)
[00000491] main decoder debug: thread started
[00000491] main decoder debug: thread 2896153488 (decoder) created at priority 0 (input/decoder.c:217)
[00000409] dvdnav demux debug: buttonUpdate not done b=1 t=1
[00000491] libmpeg2 decoder debug: 720x480 (display 720,480), aspect 768000, sar 0:0, 29.971 fps
[00000491] main decoder debug: no usable vout present, spawning one
[00000492] main video output debug: window size: 853x480
[00000492] main video output debug: looking for video output module: 6 candidates
[00000492] xvideo video output debug: adaptor 0, port 158, format 0x32315659 (YV12) planar
[00000494] main window debug: looking for vout window module: 2 candidates
[00000494] qt4 window debug: waiting for interface...
[00000494] qt4 window debug: requesting window...
[00000404] qt4 interface debug: Video was requested -1, -1
[00000404] qt4 interface debug: Video is resizing to: 853 480
[00000404] qt4 interface debug: Updating the geometry
[00000492] qt4 video output debug: Qt FS: Attaching Vout
[00000492] qt4 video output debug: Qt: Changing Fullscreen Mode
[00000494] main window debug: using vout window module "qt4"
[00000494] main window debug: TIMER module_Need() : 9.226 ms - Total 9.226 ms / 1 intvls (Avg 9.226 ms)
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[00000492] xvideo video output debug: XShm video extension v1.1 (with pixmaps, opcode: 147)
[00000492] xvideo video output debug: Window manager supports NetWM
[00000492] xvideo video output debug: Window manager supports _NET_WM_STATE_FULLSCREEN
[00000492] xvideo video output debug: Window manager supports _NET_WM_STATE_ABOVE
[00000492] xvideo video output debug: Window manager supports _NET_WM_STATE_BELOW
[00000492] main video output debug: using video output module "xvideo"
[00000492] main video output debug: TIMER module_Need() : 84.132 ms - Total 84.132 ms / 1 intvls (Avg 84.132 ms)
[00000492] main video output debug: thread started
[00000492] main video output debug: waiting for thread initialization
[00000492] main video output debug: got 8 direct buffer(s)
[00000492] main video output debug: picture in 720x480 (0,0,720x480), chroma I420, ar 16:9, sar 32:27
[00000492] main video output debug: picture user 720x480 (0,0,720x480), chroma I420, ar 16:9, sar 32:27
[00000492] main video output debug: picture out 720x480 (0,0,720x480), chroma I420, ar 16:9, sar 32:27
[00000492] main video output debug: direct render, mapping render pictures 0-6 to system pictures 1-7
[00000492] main video output debug: thread 2905873296 (video output) created at priority 15 (video_output/video_output.c:504)
[00000491] main decoder warning: dts != current_pts (-41166)
[00000404] qt4 interface debug: New Event: type 1109
[00000491] main decoder warning: backward_pts != current_pts (-33366)
[00000492] main video output warning: late picture skipped (2602704)
[00000492] main video output warning: late picture skipped (2185699)
[00000495] main decoder debug: looking for decoder module: 30 candidates
[00000495] main decoder debug: using decoder module "a52"
[00000495] main decoder debug: TIMER module_Need() : 0.474 ms - Total 0.474 ms / 1 intvls (Avg 0.474 ms)
[00000495] main decoder debug: thread started
[00000495] main decoder debug: thread 2926029712 (decoder) created at priority 5 (input/decoder.c:217)
[00000495] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
[00000495] main decoder debug: no aout present, spawning one
[00000496] main audio output debug: looking for audio output module: 3 candidates
[00000496] alsa audio output warning: audio device: iec958:AES0=0x2,AES1=0x82,AES2=0x0,AES3=0x2 is already in use
[00000496] alsa audio output debug: opening ALSA device `default'
[00000492] main video output warning: late picture skipped (2200142)
[00000496] main audio output debug: thread started
[00000496] main audio output debug: thread 2887699344 (aout) created at priority 15 (alsa.c:687)
[00000496] main audio output debug: using audio output module "alsa"
[00000496] main audio output debug: TIMER module_Need() : 35.352 ms - Total 35.352 ms / 1 intvls (Avg 35.352 ms)
[00000496] main audio output debug: output 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
[00000496] main audio output debug: mixer 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
[00000496] main audio output debug: no need for any filter
[00000496] main audio output debug: looking for audio mixer module: 3 candidates
[00000496] main audio output debug: using audio mixer module "float32_mixer"
[00000496] main audio output debug: TIMER module_Need() : 0.317 ms - Total 0.317 ms / 1 intvls (Avg 0.317 ms)
[00000496] main audio output debug: input 'a52 ' 48000 Hz 3F2R/LFE frame=1536 samples/1792 bytes
[00000492] main video output warning: late picture skipped (2053480)
[00000496] main audio output debug: filter(s) 'a52 '->'fl32' 48000 Hz->48000 Hz 3F2R/LFE->Stereo
[00000497] main audio output debug: looking for audio filter module: 24 candidates
[00000497] main audio output debug: using audio filter module "a52tofloat32"
[00000497] main audio output debug: TIMER module_Need() : 1.429 ms - Total 1.429 ms / 1 intvls (Avg 1.429 ms)
[00000496] main audio output debug: found a filter for the whole conversion
[00000496] main audio output debug: filter(s) 'fl32'->'fl32' 52800 Hz->48000 Hz Stereo->Stereo
[00000498] main audio output debug: looking for audio filter module: 24 candidates
[00000498] main audio output debug: using audio filter module "bandlimited_resampler"
[00000498] main audio output debug: TIMER module_Need() : 0.464 ms - Total 0.464 ms / 1 intvls (Avg 0.464 ms)
[00000496] main audio output debug: found a filter for the whole conversion
[00000496] main audio output warning: PTS is out of range (2841663), dropping buffer
[00000496] main audio output warning: PTS is out of range (2809764), dropping buffer
[00000496] main audio output warning: PTS is out of range (2777852), dropping buffer
[00000496] main audio output warning: PTS is out of range (2745939), dropping buffer
[00000496] main audio output warning: PTS is out of range (2714026), dropping buffer
[00000496] main audio output warning: PTS is out of range (2682112), dropping buffer
[00000496] main audio output warning: PTS is out of range (2650198), dropping buffer
[00000496] main audio output warning: PTS is out of range (2618286), dropping buffer
[00000496] main audio output warning: PTS is out of range (2586372), dropping buffer
[00000496] main audio output warning: PTS is out of range (2554456), dropping buffer
[00000496] main audio output warning: PTS is out of range (2522542), dropping buffer
[00000496] main audio output warning: PTS is out of range (2490629), dropping buffer
[00000496] main audio output warning: PTS is out of range (2458714), dropping buffer
[00000496] main audio output warning: PTS is out of range (2426801), dropping buffer
[00000496] main audio output warning: PTS is out of range (2394887), dropping buffer
[00000496] main audio output warning: PTS is out of range (5499764), dropping buffer
[00000496] main audio output warning: PTS is out of range (5468106), dropping buffer
[00000496] main audio output warning: PTS is out of range (5436246), dropping buffer
[00000496] main audio output warning: PTS is out of range (5404336), dropping buffer
[00000496] main audio output warning: PTS is out of range (5372522), dropping buffer
[00000496] main audio output warning: PTS is out of range (5342171), dropping buffer
[00000496] main audio output warning: PTS is out of range (5310390), dropping buffer
[00000496] main audio output warning: PTS is out of range (5278478), dropping buffer
[00000496] main audio output warning: PTS is out of range (5246565), dropping buffer
[00000496] main audio output warning: PTS is out of range (5214650), dropping buffer
[00000496] main audio output warning: PTS is out of range (5182736), dropping buffer
[00000496] main audio output warning: PTS is out of range (5150823), dropping buffer
[00000496] main audio output warning: PTS is out of range (5118905), dropping buffer
[00000496] main audio output warning: PTS is out of range (5086990), dropping buffer
[00000496] main audio output warning: PTS is out of range (5055099), dropping buffer
[00000496] main audio output warning: PTS is out of range (5023140), dropping buffer
[00000496] main audio output warning: PTS is out of range (4991175), dropping buffer
[00000496] main audio output warning: PTS is out of range (4959209), dropping buffer
[00000496] main audio output warning: PTS is out of range (4927244), dropping buffer
[00000496] main audio output warning: PTS is out of range (4895347), dropping buffer
[00000496] main audio output warning: PTS is out of range (4863383), dropping buffer
[00000496] main audio output warning: PTS is out of range (4831415), dropping buffer
[00000496] main audio output warning: PTS is out of range (4799448), dropping buffer
[00000496] main audio output warning: PTS is out of range (4767482), dropping buffer
[00000496] main audio output warning: PTS is out of range (4735515), dropping buffer
[00000492] main video output warning: late picture skipped (4800248)
[00000492] main video output warning: late picture skipped (4439958)
[00000496] main audio output warning: PTS is out of range (8398127), dropping buffer
[00000496] main audio output warning: PTS is out of range (8366669), dropping buffer
[00000496] main audio output warning: PTS is out of range (8335112), dropping buffer
[00000496] main audio output warning: PTS is out of range (8303286), dropping buffer
[00000496] main audio output warning: PTS is out of range (8271417), dropping buffer
[00000496] main audio output warning: PTS is out of range (8239456), dropping buffer
[00000496] main audio output warning: PTS is out of range (8207627), dropping buffer
[00000496] main audio output warning: PTS is out of range (8175810), dropping buffer
[00000496] main audio output warning: PTS is out of range (8143958), dropping buffer
[00000496] main audio output warning: PTS is out of range (8112111), dropping buffer
[00000496] main audio output warning: PTS is out of range (8080257), dropping buffer
[00000496] main audio output warning: PTS is out of range (8048401), dropping buffer
[00000496] main audio output warning: PTS is out of range (8017199), dropping buffer
[00000492] main video output warning: late picture skipped (7686916)
[00000496] main audio output warning: PTS is out of range (52660099), dropping buffer
[00000496] main audio output warning: PTS is out of range (52628335), dropping buffer
[00000496] main audio output warning: PTS is out of range (52603426), dropping buffer
[00000496] main audio output warning: PTS is out of range (52572674), dropping buffer
[00000409] dvdnav demux warning: cannot get next block (Error reading from DVD.)
[00000404] qt4 interface debug: New Event: type 1103
[00000404] qt4 interface debug: Updating the stream status: 9
[00000370] main playlist debug: finished input
[00000370] main playlist debug: dying input
[00000408] main input debug: control type=0
[00000408] main input debug: control: stopping input
[00000404] qt4 interface debug: Updating the stream status: 8
[00000491] main decoder debug: removing module "libmpeg2"
[00000491] main decoder debug: thread ended
[00000411] main generic debug: thread ended
[00000411] main generic debug: thread 2947939216 joined (dvdnav.c:367)
[00000491] main decoder debug: thread 2896153488 joined (input/decoder.c:248)
[00000491] main decoder debug: killing decoder fourcc `mpgv', 30 PES in FIFO
[00000370] main playlist debug: dying input
[00000492] main video output debug: thread ended
[00000492] main video output debug: thread 2905873296 joined (video_output/video_output.c:536)
[00000492] qt4 video output debug: Qt FS: Detaching Vout
[00000492] qt4 video output debug: Qt: Changing Fullscreen Mode
[00000494] main window debug: removing module "qt4"
[00000492] main video output debug: removing module "xvideo"
[00000495] main decoder debug: removing module "a52"
[00000495] main decoder debug: thread ended
[00000495] main decoder debug: thread 2926029712 joined (input/decoder.c:248)
[00000495] main decoder debug: killing decoder fourcc `a52 ', 0 PES in FIFO
[00000497] main audio output debug: removing module "a52tofloat32"
[00000498] main audio output debug: removing module "bandlimited_resampler"
[00000496] main audio output debug: thread ended
[00000496] main audio output debug: thread 2887699344 joined (alsa.c:742)
[00000496] main audio output debug: removing module "alsa"
[00000496] main audio output debug: removing module "float32_mixer"
[00000499] main decoder debug: looking for decoder module: 30 candidates
[00000499] main decoder debug: using decoder module "a52"
[00000499] main decoder debug: TIMER module_Need() : 0.926 ms - Total 0.926 ms / 1 intvls (Avg 0.926 ms)
[00000499] main decoder debug: thread started
[00000499] main decoder debug: thread 2887699344 (decoder) created at priority 5 (input/decoder.c:217)
[00000499] main decoder debug: removing module "a52"
[00000499] main decoder debug: thread ended
[00000499] main decoder debug: thread 2887699344 joined (input/decoder.c:248)
[00000499] main decoder debug: killing decoder fourcc `a52 ', 0 PES in FIFO
[00000500] main decoder debug: looking for decoder module: 30 candidates
[00000500] main decoder debug: using decoder module "a52"
[00000500] main decoder debug: TIMER module_Need() : 0.418 ms - Total 0.418 ms / 1 intvls (Avg 0.418 ms)
[00000500] main decoder debug: thread started
[00000404] qt4 interface debug: Video is not needed anymore
[00000404] qt4 interface debug: Updating the geometry
[00000500] main decoder debug: thread 2887699344 (decoder) created at priority 5 (input/decoder.c:217)
[00000500] main decoder debug: removing module "a52"
[00000500] main decoder debug: thread ended
[00000500] main decoder debug: thread 2887699344 joined (input/decoder.c:248)
[00000500] main decoder debug: killing decoder fourcc `a52 ', 0 PES in FIFO
[00000501] main decoder debug: looking for decoder module: 30 candidates
[00000501] main decoder debug: using decoder module "a52"
[00000501] main decoder debug: TIMER module_Need() : 0.421 ms - Total 0.421 ms / 1 intvls (Avg 0.421 ms)
[00000501] main decoder debug: thread started
[00000370] main playlist debug: dying input
[00000501] main decoder debug: thread 2887699344 (decoder) created at priority 5 (input/decoder.c:217)
[00000501] main decoder debug: removing module "a52"
[00000501] main decoder debug: thread ended
[00000501] main decoder debug: thread 2887699344 joined (input/decoder.c:248)
[00000501] main decoder debug: killing decoder fourcc `a52 ', 0 PES in FIFO
[00000408] main input debug: Program doesn't contain anymore ES
[00000370] main playlist debug: dying input
[00000409] main demux debug: removing module "dvdnav"
[00000408] main input debug: thread ended
[00000370] main playlist debug: dead input
[00000408] main input debug: thread 2956663696 joined (playlist/engine.c:244)
[00000408] main input debug: TIMER input launching for 'dvd:///dev/scd0' : 3255.856 ms - Total 3255.856 ms / 1 intvls (Avg 3255.856 ms)
[00000370] main playlist debug: starting new item
[00000370] main playlist debug: changing item without a request (current 0/1)
[00000370] main playlist debug: nothing to play

```

So I've got not clue why this doesn't work.

---

### Post by mc4man on 2009-03-22
unfortunately with this new vlc you either get almost no info from from the terminal or tons to much. Would have been good to post the complete output but anyway out of all that junk this is of interest
> [00000409] dvdnav demux warning: cannot get next block (Error reading from DVD.)

Many times this indicates a failure to crack the css keys, or a dvd navigation problem because of stucture protection (a very few titles can't be played in open source players, probably not the case here

If you are sure libdvdcss2 is installed I'd go into the home folder, find a hidden folder, ".dvdcss", and delete it .
Then try vlc from the terminal again with just vlc

you should see something similar to this
> 
doug@doug-desktop:~$ vlc 
VLC media player 0.9.8a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.8a Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--with-live555-tree=/usr/lib/live' '--prefix=/usr' '--disable-zvbi' '--enable-flac' '--enable-libass' '--enable-faad' '--disable-kate' '--enable-twolame' '--enable-caca' '--enable-theora' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--with-x264-tree=./extras/x264-trunk'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: PERFUME_DOM
libdvdnav: DVD Serial Number: 36B68ECD
libdvdnav: DVD Title (Alternative): PERFUME_DOM
libdvdnav: Unable to find map file '/home/doug/.dvdnav/PERFUME_DOM.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000131
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000003ef
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00000470
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00001fc9
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00002005
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0000dfc1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0033c80d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003839e9
libdvdread: Elapsed time 0
libdvdread: Found 5 VTS's
libdvdread: Elapsed time 1
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[00000459] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[00000481] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 

---

### Post by 1BigBore on 2009-03-22
I am having seemingly similar problems...
when I typed in 'vlc -vvv' I got this
```

 vlc -vvv
The program 'vlc' is currently not installed.  You can install it by typing:
sudo apt-get install vlc-nox
bash: vlc: command not found
bill@linux-box:~$ sudo apt-get install vlc-nox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libdca0 libdvbpsi4 libebml0 libiso9660-5 liblua5.1-0 libmatroska0
  libmodplug0c2 libtwolame0 libvcdinfo0 libvlc2 libvlccore0 vlc-data
The following NEW packages will be installed:
  libdca0 libdvbpsi4 libebml0 libiso9660-5 liblua5.1-0 libmatroska0
  libmodplug0c2 libtwolame0 libvcdinfo0 libvlc2 libvlccore0 vlc-data vlc-nox
0 upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
Need to get 5470kB of archives.
After this operation, 25.0MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://mx.archive.ubuntu.com intrepid/universe libdvbpsi4 0.1.5-3.1 [32.6kB]
Get:2 http://mx.archive.ubuntu.com intrepid/universe libebml0 0.7.7-3.1 [63.7kB]
Get:3 http://mx.archive.ubuntu.com intrepid/universe libiso9660-5 0.78.2+dfsg1-3 [112kB]
Get:4 http://mx.archive.ubuntu.com intrepid/universe liblua5.1-0 5.1.3-1 [81.7kB]
Get:5 http://mx.archive.ubuntu.com intrepid/universe libmatroska0 0.8.1-1.1 [196kB]
Get:6 http://mx.archive.ubuntu.com intrepid/main libmodplug0c2 1:0.7-7 [122kB] 
Get:7 http://mx.archive.ubuntu.com intrepid/universe libtwolame0 0.3.12-1 [53.6kB]
Get:8 http://mx.archive.ubuntu.com intrepid/universe libvcdinfo0 0.7.23-4ubuntu1 [129kB]
Get:9 http://mx.archive.ubuntu.com intrepid-updates/multiverse vlc-data 0.9.4-1ubuntu3.1 [1410kB]
Get:10 http://mx.archive.ubuntu.com intrepid-updates/multiverse libvlccore0 0.9.4-1ubuntu3.1 [392kB]
Get:11 http://mx.archive.ubuntu.com intrepid-updates/multiverse libvlc2 0.9.4-1ubuntu3.1 [46.3kB]
Get:12 http://mx.archive.ubuntu.com intrepid/universe libdca0 0.0.5-0.1 [115kB]
Get:13 http://mx.archive.ubuntu.com intrepid-updates/multiverse vlc-nox 0.9.4-1ubuntu3.1 [2715kB]
Fetched 5470kB in 44s (124kB/s)                                                
Selecting previously deselected package libdvbpsi4.
(Reading database ... 118350 files and directories currently installed.)
Unpacking libdvbpsi4 (from .../libdvbpsi4_0.1.5-3.1_i386.deb) ...
Selecting previously deselected package libebml0.
Unpacking libebml0 (from .../libebml0_0.7.7-3.1_i386.deb) ...
Selecting previously deselected package libiso9660-5.
Unpacking libiso9660-5 (from .../libiso9660-5_0.78.2+dfsg1-3_i386.deb) ...
Selecting previously deselected package liblua5.1-0.
Unpacking liblua5.1-0 (from .../liblua5.1-0_5.1.3-1_i386.deb) ...
Selecting previously deselected package libmatroska0.
Unpacking libmatroska0 (from .../libmatroska0_0.8.1-1.1_i386.deb) ...
Selecting previously deselected package libmodplug0c2.
Unpacking libmodplug0c2 (from .../libmodplug0c2_1%3a0.7-7_i386.deb) ...
Selecting previously deselected package libtwolame0.
Unpacking libtwolame0 (from .../libtwolame0_0.3.12-1_i386.deb) ...
Selecting previously deselected package libvcdinfo0.
Unpacking libvcdinfo0 (from .../libvcdinfo0_0.7.23-4ubuntu1_i386.deb) ...
Selecting previously deselected package vlc-data.
Unpacking vlc-data (from .../vlc-data_0.9.4-1ubuntu3.1_all.deb) ...
Selecting previously deselected package libvlccore0.
Unpacking libvlccore0 (from .../libvlccore0_0.9.4-1ubuntu3.1_i386.deb) ...
Selecting previously deselected package libvlc2.
Unpacking libvlc2 (from .../libvlc2_0.9.4-1ubuntu3.1_i386.deb) ...
Selecting previously deselected package libdca0.
Unpacking libdca0 (from .../libdca0_0.0.5-0.1_i386.deb) ...
Selecting previously deselected package vlc-nox.
Unpacking vlc-nox (from .../vlc-nox_0.9.4-1ubuntu3.1_i386.deb) ...
Processing triggers for man-db ...
Setting up libdvbpsi4 (0.1.5-3.1) ...

Setting up libebml0 (0.7.7-3.1) ...

Setting up libiso9660-5 (0.78.2+dfsg1-3) ...

Setting up liblua5.1-0 (5.1.3-1) ...

Setting up libmatroska0 (0.8.1-1.1) ...

Setting up libmodplug0c2 (1:0.7-7) ...

Setting up libtwolame0 (0.3.12-1) ...

Setting up libvcdinfo0 (0.7.23-4ubuntu1) ...

Setting up vlc-data (0.9.4-1ubuntu3.1) ...
Setting up libvlccore0 (0.9.4-1ubuntu3.1) ...

Setting up libvlc2 (0.9.4-1ubuntu3.1) ...

Setting up libdca0 (0.0.5-0.1) ...

Setting up vlc-nox (0.9.4-1ubuntu3.1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place


```
I still cannot play DVDs.
p.s. I got fewer "May not have permission" type of errors, but the player "greyed" out and froze up
had to force quit

---

### Post by seamusandboo on 2009-03-23
Ok, I did as you suggested, located the folder .dvdcss under home, deleted it and ran vlc from the terminal. Then inside vlc I opened the DVD, the menus came up, selected play. This time it actually started playing the DVD, but after about 20 seconds it just stopped by itself again. Below is the transcript from the terminal output:

> daniel@ubuntu-laptop:~$ vlc
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3.1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: ALIENS_SE_US_DISC1
libdvdnav: DVD Serial Number: 2F2B6243
libdvdnav: DVD Title (Alternative): ALIENS_SE_US_DISC1
libdvdnav: Unable to find map file '/home/daniel/.dvdnav/ALIENS_SE_US_DISC1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[00000469] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[00000492] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1


I still got no idea why it won't play DVDs properly and I'm about to just give up. Spent the whole Sunday trying to make this work.

---

