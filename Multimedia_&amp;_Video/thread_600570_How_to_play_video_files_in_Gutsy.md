---
title: "How to play video files in Gutsy"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by vnetha on 2007-11-02
Hi,

I have a newly installed Gutsy on my DELL OptiPlex GX280.
I barely managed to get internet and audio working.
but i'm having trouble getting started with video.

when i try to open up any video file (.avi, .mpg, .mpeg)
the run in totem player by default.
and it says it needs extra plugins to play these files,
then searches and finds some gstreamer plugins.

when i try to mark and install them though,
it won't let me do it.

do i have install some other player?
or is there a more effective way to install the required codecs?

i'm a total novice.
so patient instructions would be very much appreciated.


thanks,
Vivek.

---

### Post by tech9 on 2007-11-02
> **vnetha said:**
> Hi,

I have a newly installed Gutsy on my DELL OptiPlex GX280.
I barely managed to get internet and audio working.
but i'm having trouble getting started with video.

when i try to open up any video file (.avi, .mpg, .mpeg)
the run in totem player by default.
and it says it needs extra plugins to play these files,
then searches and finds some gstreamer plugins.

when i try to mark and install them though,
it won't let me do it.

do i have install some other player?
or is there a more effective way to install the required codecs?

i'm a total novice.
so patient instructions would be very much appreciated.


thanks,
Vivek.

sudo apt-get install vlc

---

### Post by lisc998 on 2007-11-02
I agree - I even use vlc on my XP machine. It's especially useful when viewing output from youtube-dl :)

---

### Post by jwo7777777 on 2007-11-02
VLC would do it.  It already has decoders built in.

In the event that you want to use other players, though, go to the absolute beginners forums and search for how to setup the medibuntu archive so that the codec selections will ungray.

Another reason in support for VLC is that many many people are having trouble with video through xine and other players.  VLC just works if you can get it installed.

---

### Post by johnnyw on 2007-11-02
> **jwo7777777 said:**
> VLC would do it.  It already has decoders built in.

In the event that you want to use other players, though, go to the absolute beginners forums and search for how to setup the medibuntu archive so that the codec selections will ungray.

Another reason in support for VLC is that many many people are having trouble with video through xine and other players.  VLC just works if you can get it installed.

id install automatix and download all video codecs (there is a sweet bundle of em) :)

---

