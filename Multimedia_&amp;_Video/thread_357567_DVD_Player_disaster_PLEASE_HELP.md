---
title: "DVD Player disaster PLEASE HELP"
date: 2007-02-09
forum: Multimedia &amp; Video
---

### Post by tjtansey on 2007-02-09
I've just installed edgy on my Dell Inspiron 9100.  I have a Samsung cd-rw/DVD rom mod# SN-324F.  When I first installed, the system recognized I had a DVD in the drive, but as soon as I install the upgrades to enable DVD playback, the system no longer recognizes DVD's present from ANY location or player.  Here is the list of what I installed/updated:

sudo aptitude update
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs
sudo aptitude install gstreamer0.10-pitfdll && rm -r ~/.gstreamer-0.10/
sudo aptitude install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo aptitude install totem-xine
sudo aptitude install libdvdcss2
sudo aptitude install mozilla-mplayer

I also installed xine and kaffeine in a desparate attempt to get something, here are snapshots of the screen for totem and kaffeine.  Any help would be greatly appreciated.

---

