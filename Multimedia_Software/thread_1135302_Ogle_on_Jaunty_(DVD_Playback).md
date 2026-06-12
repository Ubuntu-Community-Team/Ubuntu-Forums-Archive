---
title: "Ogle on Jaunty (DVD Playback)"
date: 2009-04-24
forum: Multimedia Software
---

### Post by aidave on 2009-04-24
Hello,

I am very fond of Ogle on Intrepid.  I really like Jaunty, and everything works great except DVDs.  I can play a DVD back in Totem, but it is very awkward.  VLC just gives errors.  Totem does offer one advantage over Ogle, and that is being able to skip rewind.  However the keyboard interface for Ogle and the quickness of DVD menu navigation is superior to Totem.

I tried downloading the Ogle build for Jaunty:
[https://launchpad.net/ubuntu/jaunty/+source/ogle/0.9.2-5.3](https://launchpad.net/ubuntu/jaunty/+source/ogle/0.9.2-5.3)

This is what happens when running:
WARNING[ogle_mpeg_vs]: B-frame before forward ref frame
xscreensaver-command not found.
WARNING[ogle_mpeg_vs]: B-frame before forward ref frame
FATAL[ogle_audio]: failed opening the oss audio driver at /dev/dsp
WARNING[ogle_vout]: req_code: 133
WARNING[ogle_vout]: minor_code: 14
WARNING[ogle_vout]: error_code: 8
WARNING[ogle_vout]: XV_COLORKEY not available
ERROR[ogle_vout]: Couldn't get attribute: XV_COLORKEY

If I use PulseAudio for my main sound selection then I can get to the DVD menus in Ogle, but once a video starts playing it gives the same XV_COLORKEY message.

Does anyone know about how to fix this?
or,
Does anyone know of a good DVD player alternative for Jaunty?


cheers and thanks

---

### Post by aidave on 2009-04-24
Ogle is now working for me.  I installed a crapload of codecs from the multimedia thread: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

```

sudo apt-get install lsa-oss faac faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea6-plugin libmp3lame0 openjdk-6-jre unrar soundconverter audacity oggconvert avidemux ffmpeg winff gxine libxine1-ffmpeg

```

I think it was one of "gxine libxine1-ffmpeg" that probably did the trick.

Ogle is working good now, although I cannot run any other competing audio program alongside it... not even Firefox!  Still, its worth it since Ogle is the best DVD player I've used so far.

---

### Post by aidave on 2009-04-29
Another update.  You can also install "ogle-gui".

The skipping seconds back/forth feature still crashes for me.
Bookmark does work though.

I also noticed if you change the ogle config XML file to "alsa" instead of "oss", you can get sound from multiple apps at the same time.  However, if I have another sound app open before ogle, it shows a black screen.  So ogle has to be the first to be opened.

I'd like to fix ogle up a bit, gotta learn how.

---

