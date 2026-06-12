---
title: "Silly codecs- you can't just give up!"
date: 2006-11-29
forum: Multimedia &amp; Video
---

### Post by Madhatter14641 on 2006-11-29
I always begin my installations of Ubuntu with a nice dose of Automatix. Just makes my life easier. Among the things that get installed quickly are the codecs for music and video. I like music. I'm sure that's a shared sentiment. 

For some reason my codecs decided to give up on me recently. While I can play MP3's, M4A files just don't work. In anything. Totem fails. Songbird fails. Amarok fails. Everything fails. I'm not sure why. 

[INDENT]totem-xine is already the newest version.
libxvidcore4 is already the newest version.
lame is already the newest version.
sox is already the newest version.
ffmpeg is already the newest version.
mjpegtools is already the newest version.
vorbis-tools is already the newest version.
mpg321 is already the newest version.
libxine-main1 is already the newest version.
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-gl is already the newest version.
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
libxine-extracodecs is already the newest version.
gstreamer0.10-fluendo-mp3 is already the newest version.
gstreamer0.10-fluendo-mpegdemux is already the newest version.
gstreamer0.10-gnonlin is already the newest version.
gstreamer0.10-sdl is already the newest version.
faac is already the newest version.
faad is already the newest version.
alsa-oss is already the newest version. [/INDENT]

I can't figure out for the life of me what happened... seems to me they worked at one point. I can read the tags. I can't play the files. ](*,) Any ideas?

---

### Post by Madhatter14641 on 2006-11-29
Bump! :-k

---

### Post by lordchaos on 2006-11-29
Have you tried to uninstall the Codecs from Automatix and re-install them?

---

### Post by Madhatter14641 on 2006-11-30
I have! I even tried a reformat (with a complimentary reinstall). When I try to play a file through gstreamer directly, I get this:

[INDENT]
madhatter@madhatter-desktop:~$ gst-launch-0.10 filesrc location=/home/madhatter/Desktop/Flake.m4a  ! faad ! audioconvert ! gconfaudiosink
Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
ERROR: from element /pipeline0/faad0: Could not decode stream.
Additional debug info:
gstfaad.c(1396): gst_faad_chain (): /pipeline0/faad0:
Failed to init decoder from stream
ERROR: pipeline doesn't want to preroll.
Setting pipeline to NULL ...
FREEING pipeline ...
[/INDENT]

I don't understand! What is it trying to tell me? ](*,)

---

### Post by alican timur on 2006-11-30
I got everything up and running too. I can't run m4a's either. On the other hand, for .mpc files, i couldn't find anything about playing them in linux.

---

