---
title: "Hardware video acceleration with vdpau not working"
date: 2017-09-08
forum: Multimedia Software
---

### Post by howeishotweb on 2017-09-08
Ubuntu 16.04 Gnome, with a GeForce 760 on nvidia-375 drivers. All relevant vdpau packages are installed as far as I can see, but it's not working in VLC or SMplayer.

In SMplayer I have configured it for both vdpau hardware decoding and video output, video plays but in its mpv log I see "Using software decoding." Full Mplayer/mpv log: [https://paste.ubuntu.com/25490609/](https://paste.ubuntu.com/25490609/) Full SMplayer log: [https://paste.ubuntu.com/25490614/](https://paste.ubuntu.com/25490614/)

In VLC, if I set video output to vdpau, it can't play the video at all. In debug messages it repeats the following
```
[COLOR=#00008b]*core*[/COLOR][COLOR=#008000]* warning: *[/COLOR]no vout found, dropping subpicture
[COLOR=#00008b]*core*[/COLOR][COLOR=#008000]* warning: *[/COLOR]can't get output subpicture
[COLOR=#00008B]*libass*[/COLOR][COLOR=#008000]* warning: *[/COLOR]can't get spu buffer
```

---

### Post by mc4man on 2017-09-08
That smplayer log is pretty useless in regards to mpv. Do this, though obviously replacing /path/to/vid & attach the log, it'll be in home folder.
```
mpv --no-config --hwdec=vdpau --log-file=mpv.txt  /path/to/vid
```
That mpv you're using is quite old, superior version, build, ect. here
[https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)

---

### Post by howeishotweb on 2017-09-11
Thank you for your reply.

mpv log for a MKV h264 video: [https://paste.ubuntu.com/25516503/](https://paste.ubuntu.com/25516503/)
mpv log for a AVI xvid video: [https://paste.ubuntu.com/25516507/](https://paste.ubuntu.com/25516507/)

Sadly it didn't seem to help updating with mpv from your repository. mpv log after doing that: [https://paste.ubuntu.com/25516594/](https://paste.ubuntu.com/25516594/)

---

### Post by mc4man on 2017-09-11
As far as the avi - 
"Not trying to use hardware decoding: codec mpeg4 is not on whitelist, or does not support hardware acceleration."
There is also something up with the .mkv,  is it a 10bit file? If so I don't believe vdpau supports that..

If you could provide samples or links to similar tpyr non playing I'd check out further...

You could try cuda, I've enabled it in ppa builds (requires nvidia-378.13 at a min., prefers newer.
mpv --no-config --hwdec=cuda /path/to/file

Edit: it's likely the avi could get vdpau hw decoding in vlc. As far as mpv if the file is shown as supported in vdpauinfo then technically mpv should allow hw decoding.
In that case start an issue at mpv's github page. You'd need to 
Follow the template
Be using a recent mpv
Show as supported in vdpauinfo
Provide a small sample file

(- the other question is why the need for hw decode on an avi of that type?

---

### Post by howeishotweb on 2017-09-13
Oh yeah, I see now that those MKVs are 10 bit. Is there anything else than can hardware decode them (not as far as I remember, but would be nice)?
It seems to be using hardware correctly for 8 bit files, so thanks for that.

I don't care much about the avi file, just did that for comparison since its output was different

---

### Post by mc4man on 2017-09-13
As far as 10 bit, I *think* only for hevc & there that would be hardware dependent. (-  maybe cards supporting Feature Set F or better.
[http://us.download.nvidia.com/XFree86/Linux-x86_64/375.26/README/vdpausupport.html#vdpau-implementation-limits](http://us.download.nvidia.com/XFree86/Linux-x86_64/375.26/README/vdpausupport.html#vdpau-implementation-limits)

---

### Post by SeijiSensei on 2017-09-13
I have a GTX 750 with VDPAU enabled.  I think I'm using the nvidia-375 driver package.

I went onto a couple of torrent sites and downloaded some 10-bit files.  I had no trouble watching them with mpv and smplayer.  I'm using the versions from Doug's repository, 17.8.0-1~trusty1 for smplayer and 2:0.26.0+git1~trusty1 for mpv.   Smplayer did report it was using the plain H.264 codec, despite the supposed 10-bit encodings, rather than hevc.

---

### Post by mc4man on 2017-09-13
> **SeijiSensei said:**
> I have a GTX 750 with VDPAU enabled.  I think I'm using the nvidia-375 driver package.

I went onto a couple of torrent sites and downloaded some 10-bit files.  I had no trouble watching them with mpv and smplayer.  I'm using the versions from Doug's repository, 17.8.0-1~trusty1 for smplayer and 2:0.26.0+git1~trusty1 for mpv.   Smplayer did report it was using the plain H.264 codec, despite the supposed 10-bit encodings, rather than hevc.
What does mpv report from cli?
Also if you have ffprobe installed
```
ffprobe -show_streams /path/to/vid  | grep pix_fmt
```

---

### Post by SeijiSensei on 2017-09-14
> 
Playing: Kazemakase Tsukikage Ran - Episode 01 [OnDeed] [E269EA03].mkv
File uses ordered chapters, will build edit timeline.
This file references data from other sources.
Will scan other files in the same directory to find referenced sources.
Match for source 1: ./Kazemakase Tsukikage Ran - Opening [OnDeed] [09EAC8F9].mkv
 (+) Video --vid=1 (*) (h264 718x480 23.976fps)
 (+) Audio --aid=1 --alang=jpn (*) 'Japanese Audio (stereo)' (ac3 2ch 48000Hz)
 (+) Subs  --sid=1 --slang=eng (*) 'English Subtitles (R1 DVD script)' (ass)
File tags:
 Title: Kazemakase Tsukikage Ran (2000) [OnDeed]
AO: [pulse] 48000Hz stereo 2ch float
VO: [opengl] 718x480 => 718x527 yuv420p10


This is a rerelease of an older show, but the encoder claims he used 10-bit.

"Video
10-bit H264, 718x480, 4:3, 23.976 fps (2094-3011 KBit/s)
Ordered chapters / external opening."

ffprobe returns the following information about the video stream:

```
Stream #0:0: Video: h264 (High 10), yuv420p10le(tv, bt470bg/unknown/unknown, progressive), 718x480 [SAR 4320:4739 DAR 6462:4739], SAR 143:157 DAR 51337:37680, 23.98 fps, 23.98 tbr, 1k tbn, 239.76 tbc (default)
```

---

### Post by mc4man on 2017-09-14
> **SeijiSensei said:**
> 

```
Stream #0:0: Video: h264 (High 10), yuv420p10le(tv, bt470bg/unknown/unknown, progressive), 718x480 [SAR 4320:4739 DAR 6462:4739], SAR 143:157 DAR 51337:37680, 23.98 fps, 23.98 tbr, 1k tbn, 239.76 tbc (default)
```
Yeah, that's a 10bit (yuv420p10le) but you're not getting hwdec as somewhat expected

> AO: [pulse] 48000Hz stereo 2ch float
VO: [opengl] 718x480 => 718x527 yuv420p10 
This ^  section would have said so..
The smplayer logs aren't that reflective of what happens after mpv starts though they may have mentioned software decoding somewhere..

---

### Post by SeijiSensei on 2017-09-14
> Yeah, that's a 10bit (yuv420p10le) but you're not getting hwdec as somewhat expected

For the first output I posted, I forgot to force VDPAU so it used OpenGL instead.  But here I forced hardware decoding, and it still worked.

```

$ mpv -vo=vdpau Kazemakase\ Tsukikage\ Ran\ -\ Episode\ 01\ \[OnDeed\]\ \[E269EA03\].mkv 
Playing: Kazemakase Tsukikage Ran - Episode 01 [OnDeed] [E269EA03].mkv
File uses ordered chapters, will build edit timeline.
This file references data from other sources.
Will scan other files in the same directory to find referenced sources.
Match for source 1: ./Kazemakase Tsukikage Ran - Opening [OnDeed] [09EAC8F9].mkv
 (+) Video --vid=1 (*) (h264 718x480 23.976fps)
 (+) Audio --aid=1 --alang=jpn (*) 'Japanese Audio (stereo)' (ac3 2ch 48000Hz)
 (+) Subs  --sid=1 --slang=eng (*) 'English Subtitles (R1 DVD script)' (ass)
File tags:
 Title: Kazemakase Tsukikage Ran (2000) [OnDeed]
AO: [pulse] 48000Hz stereo 2ch float
Using conversion filter.
VO: [vdpau] 718x480 => 718x527 yuv420p
[vo/vdpau] Compositing window manager detected. Assuming timing info is inaccurate.

```
It certainly appears to be using the VDPAU driver and plays the video.

---

### Post by mc4man on 2017-09-14
> **SeijiSensei said:**
> For the first output I posted, I forgot to force VDPAU so it used OpenGL instead.  But here I forced hardware decoding, and it still worked.
....
VO: [vdpau] 718x480 => 718x527[COLOR="#FF0000"] yuv420p[/COLOR]

That's not 10bit output & you're not doing hwdec. -vo=vdpau has nothing to do with hwdec 
The command should be --hwdec=vdpau or --hwdec= or hwdec=yes
(- here in mpv.conf I just use this
hwdec=

As example of successful vdpau hwdec ( I generally just use opengl as the vo
```
mpv --hwdec=  /home/doug/Videos/amostviolentyear-nowplaying_h1080p.mkv
Playing: /home/doug/Videos/amostviolentyear-nowplaying_h1080p.mkv
 (+) Video --vid=1 (*) (h264 1920x816 23.000fps)
 (+) Audio --aid=1 (*) (mp3 2ch 44100Hz)
AO: [pulse] 44100Hz stereo 2ch s16
[COLOR="#0000CD"]Using hardware decoding (vdpau).[/COLOR]
VO: [opengl] 1920x816 [COLOR="#0000FF"]vdpau[yuv420p][/COLOR]
AV: 00:00:02 / 00:00:31 (8%) A-V:  0.000

```

Or lets say I wanted to use cuda, it must be specified or vdpau will be used. cuda only works with opengl
```
 mpv --hwdec=cuda /home/doug/Videos/amostviolentyear-nowplaying_h1080p.mkv
Playing: /home/doug/Videos/amostviolentyear-nowplaying_h1080p.mkv
 (+) Video --vid=1 (*) (h264 1920x816 23.000fps)
 (+) Audio --aid=1 (*) (mp3 2ch 44100Hz)
AO: [pulse] 44100Hz stereo 2ch s16
[COLOR="#0000CD"]Using hardware decoding (cuda).[/COLOR]
VO: [opengl] 1920x816[COLOR="#0000FF"] cuda[nv12][/COLOR]
AV: 00:00:01 / 00:00:31 (5%) A-V:  0.000
```

or for wmv I think a --vo of vdpau is better, that's set in my mpv.conf under [extension.wmv] & hwdec is also enabled in the .conf's general section so - 
```
$ mpv  /home/doug/Videos/Amazon_720.wmv
Auto-loading profile 'extension.wmv'
Playing: /home/doug/Videos/Amazon_720.wmv
 (+) Video --vid=1 (wmv3 1280x720 23.976fps)
 (+) Audio --aid=1 --alang=eng (wmapro 6ch 48000Hz)
AO: [pulse] 48000Hz 5.1 6ch float
[COLOR="#0000CD"]Using hardware decoding (vdpau)[/COLOR].
VO: [vdpau] 1280x720[COLOR="#0000FF"] vdpau[yuv420p][/COLOR]
[vo/vdpau] Compositing window manager detected. Assuming timing info is inaccurate
AV: 00:00:14 / 00:01:42 (13%) A-V:  0.000.
```



What you could also do is check vdpauinfo for what your card supports

Also what's quite useful is to add this to ~/.config/mpv/mpv.conf 
```
log-file=mpv.log
```
Then everytime mpv is run, (either standalone or thru a front-end) it will create a log in home folder, it's just an over-write so the log is just showing last time used. Read thru that for greater detail.

---

