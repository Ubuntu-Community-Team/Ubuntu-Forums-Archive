---
title: "parole media player won't play avi/divx files?"
date: 2011-10-07
forum: Multimedia Software
---

### Post by davidlondonuk on 2011-10-07
Hi all,

Just installed xubuntu 11.04, downloaded the gstreamer plugins for the multimedia codecs but for some reason parole will not play avi (divx/xvid) video-it only plays the sound?

I can play an avi file no problem using ffplay (ffmpeg)- I am a bit stumped. I have the following installed:

gstreamer0.10-alsa
gstreamer0.10-ffmpeg
gstreamer0.10-nice
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-pulseaudio
gstreamer0.10-tools
gstreamer0.10-x
libgstreamer-perl
libgstreamer-plugins-base0.10-0
libgstreamer0.10-0

Am I missing a gstreamer plugin or codec- I also have the extra libs installed for ffmpeg to use libmp3lame etc.

Thanks for any help

---

### Post by Toz on 2011-10-07
Do you have **libavcodec52** installed?

I always install **xubuntu-restricted-extras** during setup and that allows me to view any type of media file. However, it also installs a number of other things:
>  Installing this package will pull in support for MP3 playback and decoding,
 Java runtime environment, Microsoft fonts, Flash plugin, DVD playback, and
 LAME (to create compressed audio files).


Perhaps you can try running parole from the command line and trying to load a video. Maybe an error message will display indicating which codec is required.

---

### Post by davidlondonuk on 2011-10-07
Thanks Toz,

I have libavcodec-extra-52 installed so I can use ffmpeg for the odd transcoding job. Ubuntu ffmpeg does not have libmp3lame support, I found an ubuntu site that recommended it but it removes libavcodec52.

Just installed xubuntu-restricted-extras, still can't play an avi file with parole? Uninstalled libavcodec-extra-52 and reinstalled libavcodec52-stiil can't play an xvid/divx file with parole?

Total mystery, never had a problem with parole on any linux distro.

---

### Post by Toz on 2011-10-07
Yes is is odd. Try running parole from the command line and loading a video. Perhaps an error message will appear that will give us a hint?

---

### Post by Toz on 2011-10-07
For comparison's sake, here is my list of currently installed gstreamer packages:

> gstreamer0.10-alsa
gstreamer0.10-ffmpeg
gstreamer0.10-fluendo-mp3
gstreamer0.10-gnomevfs
gstreamer0.10-nice
gstreamer0.10-pitfdll
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-pulseaudio
gstreamer0.10-tools
gstreamer0.10-x
libgstreamer-perl
libgstreamer-plugins-base0.10-0
libgstreamer0.10-0


There are some differences.

---

### Post by davidlondonuk on 2011-10-07
Thanks Toz,

I reinstalled the ffmpeg plugin, still doesn't work. Tried it from the command line and no error messages-just sound, no video. I decided to install vlc-the same file worked no problem. Tried parole again, in case vlc installed a codec that was missing-still just sound and no video.

Truly weird.

---

### Post by Toz on 2011-10-07
*scratches head*

There are some Display settings under Preferences. Does adjusting any of them make a difference?

---

### Post by only-exciter on 2012-01-20
Hi. I've got the same problem and here is output. Strange thing is that I can play any file in VLC but parole shouts the same error. 
Terminal msg:

:~$ parole
(parole:22419): window_title-DEBUG: Init

(parole:22419): GLib-GObject-WARNING **: cannot register existing type `ParoleProviderPlugin'

(parole:22419): GLib-GObject-CRITICAL **: g_type_add_interface_dynamic: assertion `g_type_parent (interface_type) == G_TYPE_INTERFACE' failed

(parole:22419): GLib-GObject-WARNING **: invalid cast from `StreamProperties' to `ParoleProviderPlugin'

** (parole:22419): CRITICAL **: parole_provider_plugin_set_player: assertion `PAROLE_IS_PROVIDER_PLUGIN (provider)' failed

(parole:22419): GLib-GObject-WARNING **: cannot register existing type `ParoleProviderPlugin'

(parole:22419): GLib-GObject-CRITICAL **: g_type_add_interface_dynamic: assertion `g_type_parent (interface_type) == G_TYPE_INTERFACE' failed

(parole:22419): GLib-GObject-WARNING **: invalid cast from `TrayProvider' to `ParoleProviderPlugin'

** (parole:22419): CRITICAL **: parole_provider_plugin_set_player: assertion `PAROLE_IS_PROVIDER_PLUGIN (provider)' failed
** Message: don't know how to handle video/x-xvid, framerate=(fraction)24000/1001, width=(int)720, height=(int)384
** Message: don't know how to handle audio/x-ac3, framed=(boolean)true, rate=(int)48000, channels=(int)6
^C(parole:22419): window_title-DEBUG: Finalized

(parole:22419): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

---

### Post by Toz on 2012-01-20
This is interesting:
> ** Message: don't know how to handle video/x-xvid, framerate=(fraction)24000/1001, width=(int)720, height=(int)384
** Message: don't know how to handle audio/x-ac3, framed=(boolean)true, rate=(int)48000, channels=(int)6

A few suggestions/questions:
1. It looks like you have some plugins enabled and they are not working properly. Can you disable all plugins and try again (Edit->Plugins)? Does it work? Do the error messages change?

2. Try deleting your ~/.gstreamer0.10 directory and trying again.

3. To determine whether its a gstreamer or parole issue, try running the video like this:
```
gst-launch-0.10 playbin uri=file:///path/to/video/file
```
...(make sure you get the number of forward slashes correct) Does it work? If so, its a parole issue. You might want to file a bug report: [https://bugzilla.xfce.org/buglist.cgi?quicksearch=parole]("https://bugzilla.xfce.org/buglist.cgi?quicksearch=parole")

4. Is this the case for just one video or many videos?

5. Which version of gstreamer0.10-ffmpeg do you have installed:
```
apt-cache policy gstreamer0.10-ffmpeg

```

---

### Post by only-exciter on 2012-01-21
> **Toz said:**
> This is interesting:


A few suggestions/questions:
1. It looks like you have some plugins enabled and they are not working properly. Can you disable all plugins and try again (Edit->Plugins)? Does it work? Do the error messages change?

2. Try deleting your ~/.gstreamer0.10 directory and trying again.

3. To determine whether its a gstreamer or parole issue, try running the video like this:
```
gst-launch-0.10 playbin uri=file:///path/to/video/file
```...(make sure you get the number of forward slashes correct) Does it work? If so, its a parole issue. You might want to file a bug report: [https://bugzilla.xfce.org/buglist.cgi?quicksearch=parole](https://bugzilla.xfce.org/buglist.cgi?quicksearch=parole)

4. Is this the case for just one video or many videos?

5. Which version of gstreamer0.10-ffmpeg do you have installed:
```
apt-cache policy gstreamer0.10-ffmpeg

```

1. Let's start from beginning. I don't have any plugins installed and when I try open a file window pop-ups saying "You do not have a decoder installed to handle this file. You might need to install the necessary plugins."  and I have no clue what plugins are missing as it doesn't give any suggestions. 
As I mentioned earlier I can play any file in VLC so what's missing? See Attch

2. Haven't tried to delete gstreamer dir

3. output from that code in terminal is:
Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
** Message: don't know how to handle video/x-xvid, framerate=(fraction)10000000/417083, width=(int)624, height=(int)352
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, mpegaudioversion=(int)1, layer=(int)3, rate=(int)48000, channels=(int)2, parsed=(boolean)true
ERROR: from element /GstPlayBin:playbin0: You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
Additional debug info:
gstplaybasebin.c(2322): prepare_output (): /GstPlayBin:playbin0
ERROR: pipeline doesn't want to preroll.
Setting pipeline to NULL ...
Freeing pipeline ...

4. Any video

5. Probably not having gstreamer installed so how is it possible that I can play any of video/audio files in VLC? 
apt-cache policy gstreamer0.10-ffmpeg
gstreamer0.10-ffmpeg:
  Installed: (none)
  Candidate: 0.10.12-1ubuntu1
  Version table:
     0.10.12-1ubuntu1 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric/universe i386 Packages

Why gstreamer is not suggested when installing ffmpeg if gstreamer is the case?

What VLC has that Parole doens't?

---

### Post by only-exciter on 2012-01-21
Gstreamer was missing and all is working. Didn't have audio but I do now after restart. What was wrong don't know. Thanks.

---

### Post by Toz on 2012-01-21
parole is a front-end to gstreamer. Not exactly sure what vlc uses, but I'm pretty sure its not gstreamer.

---

### Post by andrew.46 on 2012-01-24
> **Toz said:**
> Not exactly sure what vlc uses, but I'm pretty sure its not gstreamer.

vlc uses a large range of external libraries at build time but its decoding power comes mostly from libavcodec.

---

