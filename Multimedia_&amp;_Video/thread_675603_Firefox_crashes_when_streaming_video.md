---
title: "Firefox crashes when streaming video"
date: 2008-01-22
forum: Multimedia &amp; Video
---

### Post by fiskking on 2008-01-22
Launched firefox through terminal and played 2 videos to retrieve output. Usually the browser crashes after the 2nd. or 3rd video streaming.  I am not using totem video player (completely removed) but using VLC.  Never had a problem with Totem crashing browser, only playback, which is the reason for the removal.  

priority 0 (video_output/video_output.c:421)
[00000411] main private warning: dts != current_pts (-975588)
[00000411] main private warning: backward_pts != current_pts (-33367)
[00000408] main private debug: Registering subpicture channel, ID: 2
[00000408] main private debug: Registering subpicture channel, ID: 3
[00000408] main private debug: Registering subpicture channel, ID: 4
[00000408] main private debug: Registering subpicture channel, ID: 5
[00000407] x11 video output debug: x11 image size 684x513 (0,0,684x513)
[00000400] main input debug: EOF reached
[00000400] main input debug: waiting decoder fifos to empty
[00000400] main input debug: waiting decoder fifos to empty
[00000400] main input debug: waiting decoder fifos to empty
[00000400] main input debug: waiting decoder fifos to empty
[00000400] main input debug: waiting decoder fifos to empty
[00000400] main input debug: waiting decoder fifos to empty
[00000400] main input debug: waiting decoder fifos to empty
[00000400] main input debug: waiting decoder fifos to empty
[00000400] main input debug: waiting decoder fifos to empty
[00000400] main input debug: waiting decoder fifos to empty
[00000001] main private debug: removing all interfaces
[00000291] main interface debug: thread 2998229904 joined (interface/interface.c:258)
[00000291] main interface debug: removing module "screensaver"
[00000407] x11 video output debug: x11 image size 721x541 (0,0,721x541)
[00000400] main input debug: closing input
[00000405] main decoder debug: removing module "mpeg_audio"
[00000405] main decoder debug: thread 2898860944 joined (input/decoder.c:191)
[00000405] main decoder debug: killing decoder fourcc `mpga', 0 PES in FIFO
[00000409] main private debug: removing module "mpgatofixed32"
[00000410] main private debug: removing module "bandlimited_resampler"
[00000358] main audio output debug: thread 2885225360 joined (alsa.c:714)
[00000358] main audio output debug: removing module "alsa"
[00000358] main audio output debug: removing module "trivial_mixer"
[00000406] main decoder debug: removing module "libmpeg2"
[00000406] main decoder debug: thread 2907253648 joined (input/decoder.c:191)

[00000406] main decoder debug: killing decoder fourcc `mpgv', 0 PES in FIFO
[00000400] main input debug: Program doesn't contain anymore ES
[00000404] main demuxer debug: removing module "ps"
[00000402] main access debug: removing module "access_http"
[00000289] main interface debug: thread 2964061072 joined (interface/interface.c:258)
[00000289] main interface debug: removing module "hotkeys"
[00000001] main private debug: removing playlist handler
[00000400] main input debug: thread 2938882960 joined (input/input.c:412)
[00000407] main video output debug: removing module "i420_rgb"
[00000407] main video output debug: removing module "x11"
[00000407] main video output debug: thread 2916871056 joined (video_output/video_output.c:461)
[00000288] main private debug: thread 2972453776 joined (playlist/playlist.c:247)
[00000287] main playlist debug: thread 2980846480 joined (playlist/playlist.c:248)
[00000287] main playlist: stopping playback
[00000287] main playlist debug: deleting playlist item `[http://www.*website*.mpg](http://www.*website*.mpg)'
[00000001] main private debug: removing all video outputs
[00000001] main private debug: removing all audio outputs
[00000001] main private debug: removing module "memcpy"
[00000001] main private debug: saving plugins cache file /home/fisk/.vlc/cache/plugins-04041e.dat
argn=type, argv=video/mpeg
argn=src, argv=http://www.*website*.mpg
argn=name, argv=plugin
argn=height, argv=100%
argn=width, argv=100%
Segmentation fault (core dumped)

I am able to stream at least one or two videos but the browser crashes when attempting to stream another vid.
Any help guys?

---

### Post by fiskking on 2008-01-23
bump:guitar:

---

