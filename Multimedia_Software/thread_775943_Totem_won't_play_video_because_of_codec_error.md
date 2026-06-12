---
title: "Totem won't play video because of codec error"
date: 2008-04-30
forum: Multimedia Software
---

### Post by Maupertus on 2008-04-30
Hi everyone,

After upgrading to Hardy, I encountered this annoying problem.
I'm using Totem for all my video needs. When I tried opening a .avi file of .mkv, Totem would claim it didn't have the needed codecs.

However all codecs are properly installed.
When run in terminal, I get the following message at startup:
[quote= Totem v2.22.1]Totem (totem:14915): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpeg.so': /usr/lib/libavcodec.so.1d: undefined symbol: faacDecDecode

** (totem:14914): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name[/quote]

When I try opening a file, I get the following:

[quote= Totem v2.22.1]** Message: don't know how to handle video/x-divx, divxversion=(int)3, framerate=(fraction)2997/125, width=(int)576, height=(int)304
** Message: Missing plugin: gstreamer|0.10|totem|DivX MPEG-4 Version 3 decoder|decoder-video/x-divx, divxversion=(int)3 (DivX MPEG-4 Version 3 decoder[/quote]

I have medibuntu and all codecs/packages installed. So if anybody has an idea...

***[SOLVED]Cor2y had the idea that fixed everything and this is the solution:***
[quote=Cor2y]
1.**Ok lets see is libx264 installed?** Seems now theres an X264 error. Which is good we seem to be making progress.

2.Yup, but I have 3 options in Syn.
[b]libx264-54
libx264-57[/b]
libx264-dev

I can re-install the 57, but I can only completely remove the 54

3. Completely remove all three. The latest version is libx264-57 is the latest for hardy. libx264-dev is if you plan to compile a multimedia app that requires the use of libx264 an example would be your own version of mplayer or ffmpeg, avidemux etc. So you don't need libx264-dev installed. Then re-install only libx264-57 Do you have sources from the previous version of ubuntu enabled in your repos? libx264-54 was in gutsy.

4. Solved after removing gstreamer, then completely removing both libx264-54 and libx264-57, then reinstalling libx264-57.[/quote]

---

### Post by cor2y on 2008-04-30
It looks like you are missing some gstreamer plugins.
Install all the of gstreamer plugins.
This can be done from Add/Remove or synaptic just search for gstreamer plugin install the ones that have not been installed/checked as installed some you don't currently need like the dirac plugin or the dev and debug versions of the plugins.

---

### Post by Maupertus on 2008-04-30
> **cor2y said:**
> It looks like you are missing some gstreamer plugins.
Install all the of gstreamer plugins.
This can be done from Add/Remove or synaptic just search for gstreamer plugin install the ones that have not been installed/checked as installed some you don't currently need like the dirac plugin or the dev and debug versions of the plugins.

I wish it was that easy, I have un-installed and re-installed all gstreamer plugins to no avail.

---

### Post by cor2y on 2008-04-30
Ok here are the needed gstreamer plugins
gstreamer0.10-ffmpeg (ffmpeg support)
gstreamer0.10-fluendo-mp3 (mp3 support/playback)
gstreamer0.10-pitfdll (to use the w32codec pack if installed)
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse

Optional Plugins
gstreamer0.10-fluendo-mpegdemux
gstreamer0.10-fluendo-mpegmux

If you don't see some of these in synaptic you will need to enable the mulitverse, universe, and perhaps restricted repos, then reload

---

### Post by Gunman1982 on 2008-04-30
Another option would be to install totem-xine and either uninstall totem-gstreamer or set default to totem-xine in the config.

---

### Post by Maupertus on 2008-04-30
> **cor2y said:**
> Ok here are the needed gstreamer plugins
gstreamer0.10-ffmpeg (ffmpeg support)
gstreamer0.10-fluendo-mp3 (mp3 support/playback)
gstreamer0.10-pitfdll (to use the w32codec pack if installed)
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse

Optional Plugins
gstreamer0.10-fluendo-mpegdemux
gstreamer0.10-fluendo-mpegmux

If you don't see some of these in synaptic you will need to enable the mulitverse, universe, and perhaps restricted repos, then reload

Thanks Cor2y! What package is needed on Ubuntu 64 instead of gstreamer0.10-pitfdll?

I've installed all the rest.

@Gunman: I'm trying to have that as a last resort, but if I get frustrated enough...;)

---

### Post by cor2y on 2008-04-30
Unfortunately i don't think there is a gstreamer0.10-pitfdll for 64bit.
Although the lack of one should not effect mpeg4 playback

Heres what you could try is deleting and your .gstreamer-0.10 folder (its a hidden folder) in /home/username and try it again.
You did upgrade from gutsy so there could be some conflicts there.

---

### Post by Maupertus on 2008-05-01
> **cor2y said:**
> Unfortunately i don't think there is a gstreamer0.10-pitfdll for 64bit.
Although the lack of one should not effect mpeg4 playback

Heres what you could try is deleting and your .gstreamer-0.10 folder (its a hidden folder) in /home/username and try it again.
You did upgrade from gutsy so there could be some conflicts there.

Tried it and reinstalled, but still the same problem.
The message I get when I try to play something is:

Missing plugin: gstreamer|0.10|totem|H.264 decoder|decoder-video/x-h264 (H.264 decoder)

But the strange thing is that I must have reinstalled ffmpeg 10 times by now.

Is it possible that Totem (and VLC by the way) are looking in the wrong place?

---

### Post by cor2y on 2008-05-01
Ok lets see is libx264 installed? Seems now theres an X264 error. Which is good we seem to be making progress.

---

### Post by Maupertus on 2008-05-01
Yup, but I have 3 options in Syn. 
libx264-54
libx264-57
libx264-dev

I can re-install the 57, but I can only completely remove the 54

(sorry, I hope I'm not annoying you cor2y...I hope you're helping more people then just me by doing this.;) )

---

### Post by cor2y on 2008-05-01
Completely remove all three. The latest version is libx264-57 is the latest for hardy. libx264-dev is if you plan to compile a multimedia app that requires the use of libx264 an example would be your own version of mplayer or ffmpeg, avidemux etc. So you don't need libx264-dev installed. Then re-install only libx264-57 Do you have sources from the previous version of ubuntu enabled in your repos? libx264-54 was in gutsy.

---

### Post by Maupertus on 2008-05-01
> **cor2y said:**
> Completely remove all three. The latest version is libx264-57 is the latest for hardy. libx264-dev is if you plan to compile a multimedia app that requires the use of libx264 an example would be your own version of mplayer or ffmpeg, avidemux etc. So you don't need libx264-dev installed. Then re-install only libx264-57 Do you have sources from the previous version of ubuntu enabled in your repos? libx264-54 was in gutsy.

YEAH! SOLVED! Cor2y I really don't know how to thank you, but that did the trick.
I can imagine that more people that did an upgrade experienced this problem, so I guess that has to be it.:D

Thank you a thousand times over!

---

### Post by cor2y on 2008-05-01
glad i could help

---

### Post by IanW on 2008-05-19
I was having this problem too, but cor2y's fix has done the trick.

It also seems to solve the problem of failed video thumbnails in Nautilus,
and squashes [Launchpad bug #219621.](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/219621)

---

### Post by emid on 2008-06-04
I had the exact same problem, and this fixed it for me as well!

---

### Post by yizuman on 2008-06-23
Still having a plugin issue, I installed everything that was mentioned on the list..

still get this...

"The playback of this movie requires a audio/x-asf-unknown decoder plugin which is not installed." It's a video mpg file.

So there's still a plugin missing.

Anyone have a complete plugin list just like page one showed?

---

### Post by krsnendu on 2008-12-26
Quick fix solution:

I was having a similar problem with intrepid.
Totem, and vlc both refused to play xvid and flv files, despite having gstreamer-ffmpeg installed.

Reason:
gstreamer0.10-ffmpeg kept looking for libx264-57 (hardy version) instead of libx264-59 (the installed intrepid)

Running totem from the command line gave:
```
(totem:17363): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpeg.so': libx264.so.57: cannot open shared object file: No such file or directory
```


Despite completely uninstalling gstreamer and all unstripped libs, then reinstalling this error remained.

This command showed what was happening:
```

ldd /usr/lib/gstreamer-0.10/libgstffmpeg.so
...
libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0x00007fc959fad000)
libx264.so.57 => not found

```

As  work around it made a symlink to the installed file and everything started working. 

sudo ln -s libx264.so.59 libx264.so.57

This is not a proper solution, but it might help someone in a similar situation to myself.

---

### Post by theterabyteboy on 2011-08-18
TRY THIS TO FIX YOUR PROBLEM:

Totem worked as root, not as user. Fix was, as user:
rm ~/.gstreamer-0.10/*
then
gst-inspect
to rebuild the gstreamer registry

---

