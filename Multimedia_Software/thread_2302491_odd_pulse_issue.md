---
title: "odd pulse issue"
date: 2015-11-10
forum: Multimedia Software
---

### Post by evan19 on 2015-11-10
Hey guys this is my first post here after about two years of ubuntu, so hopefully this is the right section for this. It's the only issue I've had of many where exhaustive search hasn't yielded results. I hope it's something easy I'm just missing.

So I want to use hdmi for surround sound passthrough. It works in vlc. I set up my pulse config files two years ago and have never had a problem with vlc once I finally had it running. Problem is now I wan't to switch to mpv and for the life of me I can not make it play. I set up my mpv.conf file correctly according to the devs there in their support irc chan. smplayer wont do the passthrough either.

mpv and smplayer both output stereo just fine. in pulse audio volume control I have my output set as hdmi stereo which allows the digital passthrough for vlc at least. Setting it as hdmi 5.1 breaks vlc's passthrough but will still playback stereo. Sounds odd, right?

I am not sure how to direct mpv or smplayer to output the same way vlc is. all three are set to output via pulse.

I'm also not sure what other info you guys might need but I will try to acquire whatever you need to get a clearer picture.

Thanks,
Evan

---

### Post by sandyd on 2015-11-10
Moved to *Multimedia Software*

---

### Post by tgalati4 on 2015-11-11
Welcome to the forums.  Well, you can turn off *[pulseaudio]("http://https://wiki.ubuntu.com/PulseAudio")* and then see if *vlc* still works.  That would indicate that *vlc* is using ALSA as a fallback sound path.  

[http://askubuntu.com/questions/82109/bursts-of-white-noise-sound-when-playing-videos](http://askubuntu.com/questions/82109/bursts-of-white-noise-sound-when-playing-videos)

---

### Post by evan19 on 2015-11-11
thanks for the idea tgalai4.

killing pulse and playing video in vlc yields this error:

[COLOR=#ff0000]Audio output failed:[/COLOR]
[COLOR=#000000]The audio device "default" could not be used:[/COLOR]
[COLOR=#000000]No such file or directory.

mpv and smplayer also produce no sound. mpv from command line shows this:

[/COLOR]
[ao/pulse] Init failed: Connection refused
[ao] Failed to initialize audio driver 'pulse'
Could not open/initialize audio device -> no sound.


which I am guessing should be expected, with pulse killed.

---

### Post by evan19 on 2015-11-11
> **tgalati4 said:**
> Welcome to the forums.  Well, you can turn off *[pulseaudio]("http://https://wiki.ubuntu.com/PulseAudio")* and then see if *vlc* still works.  That would indicate that *vlc* is using ALSA as a fallback sound path.  

[http://askubuntu.com/questions/82109/bursts-of-white-noise-sound-when-playing-videos](http://askubuntu.com/questions/82109/bursts-of-white-noise-sound-when-playing-videos)

And mpv with pulse back on shows this:

[stream] Video (+) --vid=1 (h264)
[stream] Audio (+) --aid=1 (*) (ac3)
libva info: VA-API version 0.38.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_38
libva info: va_openDriver() returns 0
Trying to use hardware decoding.
AO: [pulse] 48000Hz 5.1(side) 6ch float
VO: [opengl-hq] 1280x720 vaapi

it says 6ch float but is outputting stereo pcm according to my receiver.

sorry btw, forgot to quote you in my first response

---

### Post by evan19 on 2015-11-11
So through the mpv irc chan I have learned that passthrough isn't necessary. sending 6 channel pcm over hdmi works so apparently that's a better way of doing it. and pulse is handling that fine. So this may be solved. Thanks for the help!!!

---

