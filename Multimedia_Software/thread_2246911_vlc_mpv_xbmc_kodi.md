---
title: "vlc mpv xbmc kodi"
date: 2014-10-04
forum: Multimedia Software
---

### Post by shantiq on 2014-10-04
Trying to play videos from YT in recent times through vlc and mpv and getting this message and this Never was a problem before


```
mpv http://www.youtube.com/watch?v=HQ1U3beMnGo
Playing: http://www.youtube.com/watch?v=HQ1U3beMnGo
[quvi] Checking URL...
[quvi] server response code 403 (conncode=0)
[ffmpeg] tls: A TLS packet with unexpected length was received.
Failed to recognize file format.



```

---

### Post by mc4man on 2014-10-04
mpv uses quvi which apparently  is no longer being developed so over time fewer & fewer yt vids will work.
(- forget any vevo & many official music vids in mpv/quvi

As far as your link in vlc it works ok here in vlc 2.2+ and should be ok in 3.0+ - ex.
> vlc [http://www.youtube.com/watch?v=HQ1U3beMnGo](http://www.youtube.com/watch?v=HQ1U3beMnGo)
VLC media player 2.2.0-pre4 Weatherwax (revision 2.2.0+ppa2.3)
[00000000011a6118] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libva info: VA-API version 0.36.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_36
libva info: va_openDriver() returns 0
[00007f7430c95bd8] avcodec decoder: Using Intel i965 driver for Intel(R) Haswell Mobile - 1.4.0 for hardware decoding.

---

### Post by shantiq on 2014-10-04
Thanx Mc   clarifies mpv

Was on 2.1.5 for vlc and no dice so went to Daily

[COLOR=#555555][FONT=consolas] sudo add-apt-repository ppa:videolan/master-daily[/FONT][/COLOR]
[COLOR=#555555][FONT=consolas] sudo apt-get update ; [/FONT][/COLOR][COLOR=#555555][FONT=consolas]sudo apt-get install vlc


and works better but still not right   too many problems with YouTube and vlc    i am now probably going to use xbmc more    as more reliable for this it seems at the moment[/FONT][/COLOR]

---

### Post by mc4man on 2014-10-26
Small info on mpv
As of 0.6.2 +git 9b45b48 quvi support is dropped. 
It will be replaced by a lua script that's a wip 
Atm one works pretty good in yt tests, an ex. is inc. in trusty package [here]("https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests")
(mpv with quvi disabled is needed for proper operation

If testing - copy /usr/share/doc/mpv/tools/lua/ytdl_hook.lua to either (depends on where one configs mpv
~/.mpv/lua/
or
~/.config/mpv/lua/
(creating the lua folder if need be

A very recent ((2014.10.25 or later) youtube-dl  must be installed in $PATH
Then simply mpv url
Ex. (vevo
>  mpv [http://www.youtube.com/watch?v=C-dW7z0QBNg](http://www.youtube.com/watch?v=C-dW7z0QBNg)
Playing: [http://www.youtube.com/watch?v=C-dW7z0QBNg](http://www.youtube.com/watch?v=C-dW7z0QBNg)
[ytdl_hook] WARNING: video doesn't have subtitles
[ytdl_hook] youtube-dl succeeded! 
Cache fill:  0.42% (108544 bytes)   
[stream] Video (+) --vid=1 (*) (h264)
[stream] Audio (+) --aid=1 --alang=und (*) (aac)
File tags:
 major_brand: mp42
 minor_version: 0
 compatible_brands: isommp42
 creation_time: 2014-03-07 12:48:13
libva info: VA-API version 0.36.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_36
libva info: va_openDriver() returns 0
Trying to use hardware decoding.
AO: [pulse] 44100Hz stereo 2ch float
VO: [opengl-hq] 1280x720 => 1280x720 vaapi
 AV: 00:00:13 / 00:04:17 (5%) A-V:  0.000 Cache:  1s+22394KB



---

### Post by shantiq on 2014-10-26
replicated here

```
mpv http://www.youtube.com/watch?v=C-dW7z0QBNgPlaying: http://www.youtube.com/watch?v=C-dW7z0QBNg
[ytdl_hook] WARNING: video doesn't have subtitles
[ytdl_hook] youtube-dl succeeded! 
[stream] Video (+) --vid=1 (*) (h264)
[stream] Audio (+) --aid=1 --alang=und (*) (aac)
File tags:
 major_brand: mp42
 minor_version: 0
 compatible_brands: isommp42
 creation_time: 2014-03-07 12:48:13
AO: [alsa] 44100Hz stereo 2ch float
VO: [opengl] 1280x720 => 1280x720 yuv420p
AV: 00:01:28 / 00:04:17 (34%) A-V:  0.021 D: 1258 Cache:  1s+12453KB
[2]+  Stopped                 mpv http://www.youtube.com/watch?v=C-dW7z0QBNg



```

only difference the script was somewhere different for me than folder you indicated

ie


```
/usr/share/doc/mpv/tools/[COLOR=#b22222]lua[/COLOR]/ytdl_hook.lua
```
and not /usr/share/doc/mpv/tools/ytdl_hook.lua


slight drag still here on my 9-year-old puter and none on XBMC


AND as a thank you   try     mpv [https://www.youtube.com/watch?v=rzZhUT6MgY4](https://www.youtube.com/watch?v=rzZhUT6MgY4)

---

### Post by mc4man on 2014-10-26
Correct, forgot i placed it in /usr/share/doc/mpv/tools/lua/

Edit: I'll have to give Kodi a try once I can get a new ssd to replace the one I've managed to screw up..

---

### Post by shantiq on 2014-10-27
Ha   so it becomes[ Kodi]("http://xbmc.org/download/#alphabuilds") now      i still will be with 13.2 Gotham xbmc    as so   stable right now  ::]]

---

