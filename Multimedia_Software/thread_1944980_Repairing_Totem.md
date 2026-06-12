---
title: "Repairing Totem"
date: 2012-03-22
forum: Multimedia Software
---

### Post by MirkoK on 2012-03-22
Hello, somebody please help me repairing Totem on 10.04, I've damaged it on an online friend's system. Quick history:

OP installed VLC from the n-muench/vlc2 PPA which also installed libav* (libavformat52, ...) stuff version 0.6.2 Later he tried to install Frostwire which depends on mplayer which depends on libav* 0.5.1 and wasn't installable. Since I have mplayer, libav* 0.5.1 and the n-muench VLC installed on my 10.04, I idiotically suggested to force a downgrade of libavformat52 and libavcodec52 to the 0.5.1 version bypassing apt-get.

Now the trouble begun: broken packages, broken video players. Although we repaired the package system (ppa-purge, install/reinstall restricted-extras, libav*, gstreamer*, libxvidcore4, ...), Totem is still broken.

Situation now is: VLC (v1.0.6) plays the videos only after repairing the AVI index (it didn't before), Totem keeps saying that no package with requested plugin xvid mpeg-4 decoder could be found. mplayer and ffplay play the video without problems.


Output from dpkg --get-selections|awk '/libav|libxv|gstreamer/ && !/avahi/'

[http://pastebin.com/0UTfFmeP](http://pastebin.com/0UTfFmeP)

Output from apt-cache policy `dpkg --get-selections|awk '/libav|libxv|gstreamer/ && !/avahi/{print $1}'` 

[http://pastebin.com/51pESjjk](http://pastebin.com/51pESjjk)


Any idea what's missing or wrong?

---

### Post by MirkoK on 2012-03-23
Following a tip from the #ubuntu IRC channel, we purged then reinstalled Totem, but it didn't help, same problem.  I really suspect that there's something wrong with libav* or gstreamer*, either some package is missing or a wrong version is installed, I just don't know how to completely reinstall them without totally breaking Gnome.

---

