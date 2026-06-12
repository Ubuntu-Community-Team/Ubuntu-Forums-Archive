---
title: "How to open or view qtl files?"
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by rare HERO on 2007-12-02
I'm trying to open / view a qtl file, no luck.  Here is what I've done thus far:
```
sudo apt-get install ubuntu-restricted-extras
```
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
```
sudo apt-get install libdvdcss2
```
```
sudo apt-get install w32codecs
```
```
sudo nano /etc/firefox/firefoxrc
```
```
sudo apt-get install vlc vlc-plugin-* mozilla-plugin-vlc
```
```
sudo apt-get install avahi-daemon
```
```
sudo apt-get install avahi-utils
```
```
sudo apt-get install ubuntu-restricted-extras
```
```
sudo apt-get install ubuntu-restricted-extras
```
```
sudo apt-get install libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
```

I downloaded qtl file to desktop.  VLC, xine, totem, & mplayer will not open / play it.
I opened it with the text editor.  Copied the link rtsp://cronkitevideo.asu.edu/benefitmufire.mov into the VLC to open it as a stream.  Didn't work.  Copied the link into firefox where totem attempted to play it.  I got this message:
"The playback of this movie requires the following decoders which are not installed:
PUREVOICE audio RTP depayloader
SV3V-ES video RTP depayloader"

Assistance is appreciated.

---

### Post by Palmyra on 2008-05-03
Have you tried Totem?  It didn't actually work for me, but it looked like it was about to play the video, but it then failed.

---

### Post by Jetze on 2008-05-07
Totem opens .qtl files just fine on Heron, but 'forgets' to stream, so after every 3 seconds playback halts to buffer. 

This, and many, MANY other minor bugs like this one, is what keep me from recommending Linux for the desktop, and even makes me consider moving back to Windows. If anyone in codec-devolpment is reading this: Desktop = Media (& Responsiveness, but Herons sluggishness is something else)

---

