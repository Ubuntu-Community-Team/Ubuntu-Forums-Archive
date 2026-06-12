---
title: "quicktime in browser not working"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by ttiga on 2007-05-07
hello everyone,

is  there someone out there who can help me watch a quicktime movie in firefox under Ubuntu?

i'm very new in linux 

thank you in advance for your help

ttiga

---

### Post by ahaslam on 2007-05-07
You'll need the mplayer plugin (1st remove the totem plugin)
You may also require the w32codecs from the medibuntu repo, can't remember :rolleyes:

---

### Post by wormser on 2007-07-31
I am unable to see Quicktime videos in Firefox.  The Quicktime video at the bottom of [http://www.apple.com/mac/](http://www.apple.com/mac/) does not play and asks you to install it.  I use the mplayer plugin in my browser.  Any ideas?

---

### Post by eggdeng on 2007-07-31
If you mean that black square thing, it seems to be just a link. You should be able to see the videos with the mplayer plugin by clicking on the play buttons below. Or click on the black X image and then on take a tour.

---

### Post by jctosu on 2007-08-15
install the following packages, you may need to enable the medibuntu repos [(http://medibuntu.sos-sts.com/repository.php]("http://medibuntu.sos-sts.com/repository.php"))

mplayer
mplayer-firefox
win32codecs
libquicktime
gstreamer ffmpeg
gstreamer gl
gstreamer plugin base
gstreamer plugin good
gstreamer plugin bad
gstreamer plugin ugly
gstreamer plugin bad multiverse
gstreamer plugin ugly multiverse


Search for vlc plugin for firefox.

DO NOT INSTALL IT.

If it is already installed, uninstall it.

Mplayer plugin seems to work much better, especially for QT format, and vlc plugin will take priority over mplayer in firefox.

(For someone who wants to manually uninstall vlc plugin, it's in /usr/lib/firefox/plugins)



Now hit Alt+F2 add copy in the following:

Quote:

gksudo gedit /etc/mplayer/codecs.conf

In the menu go to Search-->Find

type in "ffsvq3" and hit ok

comment out the paragraph so it looks like this:

Quote:

#videocodec ffsvq3

# info "FFmpeg Sorenson Video v3 (SVQ3)"

# status working

# fourcc SVQ3

# driver ffmpeg

# dll svq3

# out YV12,I420,IYUV

save the document



and restart firefox!


worked for me on most quicktime files, not all files work for me but a lot of them do

---

### Post by jctosu on 2007-08-15
install the following packages, you may need to enable the medibuntu repos [(http://medibuntu.sos-sts.com/repository.php]("http://medibuntu.sos-sts.com/repository.php"))

mplayer
mplayer-firefox
win32codecs
libquicktime
gstreamer ffmpeg
gstreamer gl
gstreamer plugin base
gstreamer plugin good
gstreamer plugin bad
gstreamer plugin ugly
gstreamer plugin bad multiverse
gstreamer plugin ugly multiverse


Search for vlc plugin for firefox.

DO NOT INSTALL IT.

If it is already installed, uninstall it.

Mplayer plugin seems to work much better, especially for QT format, and vlc plugin will take priority over mplayer in firefox.

(For someone who wants to manually uninstall vlc plugin, it's in /usr/lib/firefox/plugins)



Now hit Alt+F2 add copy in the following:

Quote:

gksudo gedit /etc/mplayer/codecs.conf

In the menu go to Search-->Find

type in "ffsvq3" and hit ok

comment out the paragraph so it looks like this:

Quote:

#videocodec ffsvq3

# info "FFmpeg Sorenson Video v3 (SVQ3)"

# status working

# fourcc SVQ3

# driver ffmpeg

# dll svq3

# out YV12,I420,IYUV

save the document



and restart firefox!


worked for me on most quicktime files, not all files work for me but a lot of them do

---

