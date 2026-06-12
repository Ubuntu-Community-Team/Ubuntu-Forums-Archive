---
title: "can't seek mp3 track in any gstreamer-based player"
date: 2010-03-21
forum: Multimedia Software
---

### Post by SunnyOne on 2010-03-21
Hi everyone!

i've got the problem described in subj.
Any player (tried Exaile, RythmBox, Banshee, Totem) unable to seek over mp3 track.
However all is ok with FLAC, for example.

With Exaile in debug mode i've got the following when trying to seek:
DEBUG   : Couldn't send seek event (xl.player.engine_normal)

Looking though Exaile's source i have found code which issues this (/usr/lib/exaile/xl/player/engine_normal.py:262) - function seek(). That made me think that problem is not in players but in backend.

Am i right? How could i fix this?

i'm using:
Ubuntu                                9.10
exaile                                0.3.0.1-0ubuntu6
exaile-plugin-contextinfo             0.3.0.1-0ubuntu6
gstreamer-dbus-media-service          0.1.17-upstream-0ubuntu3
gstreamer-tools                       0.10.25-2
gstreamer0.10-alsa                    0.10.25-2ubuntu1.2
gstreamer0.10-ffmpeg                  0.10.9-1
gstreamer0.10-gnomevfs                0.10.25-2ubuntu1.2
gstreamer0.10-nice                    0.0.9-2
gstreamer0.10-plugins-bad             0.10.14-4ubuntu1
gstreamer0.10-plugins-bad-multiverse  0.10.13-0ubuntu1
gstreamer0.10-plugins-base            0.10.25-2ubuntu1.2
gstreamer0.10-plugins-base-apps       0.10.25-2ubuntu1.2
gstreamer0.10-plugins-good            0.10.16-1ubuntu3
gstreamer0.10-plugins-ugly-multiverse 0.10.12-0ubuntu1
gstreamer0.10-pulseaudio              0.10.16-1ubuntu3
gstreamer0.10-tools                   0.10.25-2
gstreamer0.10-x                       0.10.25-2ubuntu1.2
libgstfarsight0.10-0                  0.0.15-1ubuntu1
libgstreamer-plugins-base0.10-0       0.10.25-2ubuntu1.2
libgstreamer0.10-0                    0.10.25-2
phonon-backend-gstreamer              4:4.3.1-4ubuntu1
python-gst0.10                        0.10.17-1 

Is any other information needed?

---

### Post by boombox1387 on 2010-03-21
Not sure what the difference is between gstreamer0.10-plugins-ugly and gstreamer0.10-plugins-ugly-multiverse, but you'll want to make sure you have the first one installed.  I know the -ffmpeg plugin allows mp3 playback but not seeking.

---

### Post by SunnyOne on 2010-03-22
Thank You!!!

Installing those plugins solved my problem!

---

### Post by boombox1387 on 2010-03-22
> **SunnyOne said:**
> Thank You!!!

Installing those plugins solved my problem!

Great!  Glad to hear it.

---

### Post by promet on 2011-04-23
Hi guys, still having a little trouble with this. Is the idea that having the "ugly" plugins installed does the trick (I do have these installed), or do you also have to REMOVE the ffmpeg plugin to have success with seeking. I'm not really clear on that.

I'd test it myself, but removing the ffmpeg, on my install, would also remove Miro, which I'm kind of attached to at the moment... ;)

Thanks!

---

### Post by megamasha on 2011-06-21
The solution is based on installing the plain gstreamer0.10-plugins-ugly plugins, rather than the multiverse variant. I don't seem to be able to find the non-multiverse version. I have all software sources enabled on Kubuntu 11.04.

So this hasn't solved anything for me.

That said, not sure I've got backports... Would I need that? More to the point, should I need that?

---

