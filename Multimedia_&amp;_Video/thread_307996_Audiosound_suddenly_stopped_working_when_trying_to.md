---
title: "Audio/sound suddenly stopped working when trying to compile Mplayer"
date: 2006-11-27
forum: Multimedia &amp; Video
---

### Post by KingArthur10 on 2006-11-27
After following a couple guides and ending up reinstalling gdm, sound drivers, gnome, etc, and reconfiguring alsa mixer, things work well again.

After doing: 
sudo apt-get install build-essential debhelper libx11-dev libxv-dev libpng12-dev checkinstall libavcodec-dev libaa1-dev caca-utils libcaca-dev libavcodec-dev libavifile-0.7-dev libsdl1.2debian-all libesd0-dev libfaac-dev libfaad2-dev libgtk2.0-dev liblame-dev libice-dev libjpeg62-dev libmatroska-dev libmad0-dev libmpcdec-dev libmp4v2-dev libmikmod2-dev libogg-dev libtheora-dev libvorbis-dev libxinerama-dev libxv-dev xlibs-dev x-dev cvs libquicktime0 libquicktime-dev fakeroot gnome-core-devel libpostproc-dev libx11-dev libxv-dev libavcodec-dev libgtk1.2-dev msttcorefonts nasm subversion

restarting caused sound to stop working.  I can't get anything at all to play (mplayer, VLC, totem, banshee, etc).  The OSS, ESD, and ALSA sounds do not work at all.  I would appreciate any help to restore my sound playback.  When libsdl1.2debian-all was installed, it required libsdl1.2debian-alsa to be removed and then gave an error message.  I tried reinstalling libsdl.2debian-alsa and it still didn't cure what ales my machine.

---

