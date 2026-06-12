---
title: "sound, mplayer"
date: 2010-03-01
forum: Multimedia Software
---

### Post by cucuru on 2010-03-01
hello, I cant understand what is happen, when I tried to execute a mp3 file:

```

admin@wimax-server:/usr/local/movies$ mplayer sample.mp3
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing sample.mp3.
Audio only file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 160.0 kbit/11.34% (ratio: 20000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
AO: [pulse] Init failed: Connection refused
Failed to initialize audio driver 'pulse'
[AO_ALSA] alsa-lib: confmisc.c:768:(parse_card) cannot find card '0'
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:1251:(snd_func_refer) error evaluating name
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
[AO_ALSA] alsa-lib: conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
[AO_ALSA] Playback open error: No such file or directory
Failed to initialize audio driver 'alsa'
[AO SDL] Samplerate: 44100Hz Channels: Stereo Format s16le
[AO SDL] using aalib audio driver.
[AO SDL] Unable to open audio: No available audio device
Failed to initialize audio driver 'sdl:aalib'
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video

```

```

admin@wimax-server:/usr/local/movies$ getfacl /dev/snd/*
getfacl: Removing leading '/' from absolute path names
# file: dev/snd/by-path
# owner: root
# group: root
user::rwx
group::r-x
other::r-x

# file: dev/snd/controlC0
# owner: root
# group: audio
user::rw-
group::rw-
other::---

# file: dev/snd/hwC0D0
# owner: root
# group: audio
user::rw-
group::rw-
other::---

# file: dev/snd/pcmC0D0c
# owner: root
# group: audio
user::rw-
group::rw-
other::---

# file: dev/snd/pcmC0D0p
# owner: root
# group: audio
user::rw-
group::rw-
other::---

# file: dev/snd/pcmC0D1p
# owner: root
# group: audio
user::rw-
group::rw-
other::---

# file: dev/snd/timer
# owner: root
# group: audio
user::rw-
group::rw-
other::---


```

What can be missing? or what can be the problem?

Thanks!! regards

---

### Post by laceration on 2010-03-01
Ubuntu has a jumbled multilayered sound system, that gets tripped up.  I have gotten errors just like yours, but they have been have been temporary, I have attributed them to the inadequacy of the system itself.  Playing a file over a network has often been enough to cause errors like this.  I have also have had problems sometimes if I played flash in a browser and the browser was still open.  If this is more than a temporary thing for you, it is beyond me to help you.  You could try different audio output drivers.
$ mplayer -ao oss file
get a list of drivers from
$ mplayer -ao help

---

### Post by cucuru on 2010-03-02
hi! thanks for your help, but it doesnt work:

```

admin@wimax-server:/usr/local/movies$ mplayer -ao oss sample.mp3
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing sample.mp3.
Audio only file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 160.0 kbit/11.34% (ratio: 20000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
Failed to initialize audio driver 'oss'
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video


Exiting... (End of file)


admin@wimax-server:/usr/local/movies$ mplayer -ao help
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
Available audio output drivers:
    oss    OSS/ioctl audio output
    alsa    ALSA-0.9.x-1.x audio output
    esd    EsounD audio output
    pulse    PulseAudio audio output
    jack    JACK audio output
    nas    NAS audio output
    sdl    SDLlib audio output
    openal    OpenAL audio output
    mpegpes    DVB audio output
    v4l2    V4L2 MPEG Audio Decoder output
    null    Null audio output
    pcm    RAW PCM/WAVE file writer audio output


```Does anybody know how to solve my problem?

Thanks! regards

---

### Post by amrypma on 2010-03-02
laceration: oss is really old try alsa every time.

cucuru: it might be pulse audio has crashed or it just won't go for some reason.
What you could try is adding yourself to the audio group. (you propably already are in that group.)

```
sudo adduser <username> audio
```

reboot for pulse audio's sake.. (i haven't found any way of getting it to function again once it croaked)
Try again.

If it still doesn't work i'd remove pulse audio. and restart alsa.
```
sudo apt-get remove pulseaudio
sudo /etc/init.d/alsautils restart
```
and try again.

---

### Post by cucuru on 2010-03-02
Thank you very much amrypma!!! it worked adding the user! 

now I have the problem with video, i tried: sudo adduser <user> video but it doesnt work, this is the error:

```

admin@wimax-server:/usr/local/movies$ mplayer sample_100kbit.mp4
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing sample_100kbit.mp4.
libavformat file format detected.
[lavf] Audio stream found, -aid 0
[lavf] Video stream found, -vid 1
VIDEO:  [mp4v]  192x242  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
vo: couldn't open the X11 display ()!
[vdpau] Could not open dynamic library libvdpau.so.1
vo: couldn't open the X11 display ()!
VO XOverlay need a subdriver
[gl] using extended formats. Use -vo gl:nomanyfmts if playback fails.
vo: couldn't open the X11 display ()!
vo: couldn't open the X11 display ()!
vo: couldn't open the X11 display ()!
commandline read: mplayer
commandline read: sample_100kbit.mp4

   ~~~~~~~~~~~~~~~~~~~~~~~~~~| DirectFB 1.2.7 |~~~~~~~~~~~~~~~~~~~~~~~~~~
        (c) 2001-2008  The world wide DirectFB Open Source Community
        (c) 2000-2004  Convergence (integrated media) GmbH
      ----------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2009-06-02 06:26) 
(*) Direct/Memcpy: Using Generic 64bit memcpy()
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system_core' core!
    --> Initialization error!
[VO_SDL] SDL initialization failed: DirectFBCreate: Initialization error!.
Can't open /dev/fb0: No such file or directory
[fbdev2] Can't open /dev/fb0: No such file or directory
svgalib: Cannot get I/O permissions.


```

Im not sure if I should open a new thread and mark this one as solved. what do you think?

Regards!

---

### Post by amrypma on 2010-03-03
cucuru: you're welcome.

How ever I not brilliant with X servers. It seems you are missing a graphics driver. Have a look at what video card you have.

The listing mentiond /dev/vdpau which I think is NVidia specific and seemed too much hassle to try to configure on my machine. If you have an nvidia card install ubuntu-restricted-modules. That should have binary drivers for most nvidia cards.

I hope this helps.

---

### Post by cucuru on 2010-03-03
Thanks! I solved it yesterday, it is this link:

[http://ubuntuforums.org/showthread.php?t=1419674](http://ubuntuforums.org/showthread.php?t=1419674)

Regards!

---

