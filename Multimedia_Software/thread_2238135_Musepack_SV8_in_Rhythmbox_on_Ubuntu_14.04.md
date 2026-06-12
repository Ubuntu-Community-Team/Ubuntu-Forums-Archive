---
title: "Musepack SV8 in Rhythmbox on Ubuntu 14.04"
date: 2014-08-06
forum: Multimedia Software
---

### Post by spazzeri on 2014-08-06
Hello,

I have a few music files encoded with musepack SV8.

Rhythmbox 3.0.2 cannot play them, nor can Audacious 3.5.1

In RB a message appears:

"Required plugin could not be found.
Rhythmbox requires to install plugins to play media files of the following type: Musepack (MPC) decoder".

Note that I also have a musepack SV7 album, which Rhythmbox and Audacious can play.

---

### Post by mc4man on 2014-08-06
gstreamer apps don't support sv8, nor does audacious (audacious could/should, if inclined file an upstream bug - 
[http://redmine.audacious-media-player.org/projects/audacious/issues](http://redmine.audacious-media-player.org/projects/audacious/issues)
(- though maybe there is something because seeking is broken in many players for sv8

Many others will - vlc, mplayer, mpv, deadbeef, even the almost dead miro.

---

### Post by spazzeri on 2014-08-07
Thanks.

There is an issue with gmusicbrowser too:
[http://forum.gmusicbrowser.org/index.php?topic=815.msg3733#msg3733](http://forum.gmusicbrowser.org/index.php?topic=815.msg3733#msg3733)

Oh wait, you are the author of this post :)
[http://ubuntuforums.org/showthread.php?t=2217440&p=12991188#post12991188](http://ubuntuforums.org/showthread.php?t=2217440&p=12991188#post12991188)

--
[http://redmine.audacious-media-player.org/issues/459](http://redmine.audacious-media-player.org/issues/459)

---

### Post by mc4man on 2014-08-07
After that post decided to fix for trusty, you could get package from here, either from adding ppa or just download & install the libmpcdec6 .deb
[https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)

It also appears [14.10 picked up on the fix ]("https://bugs.launchpad.net/ubuntu/+source/libmpc/+bug/1310554") so alternate would be to install libmpcdec6 from 14.10

---

### Post by spazzeri on 2014-08-08
Thanks.
I installed the .deb from the ppa, mpc playback works in gmusicbrowser (with seeking).

---

