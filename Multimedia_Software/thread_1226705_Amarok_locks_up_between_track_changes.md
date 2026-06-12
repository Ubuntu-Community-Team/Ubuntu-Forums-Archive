---
title: "Amarok locks up between track changes"
date: 2009-07-29
forum: Multimedia Software
---

### Post by themusicalduck on 2009-07-29
A problem with Amarok has cropped up for me where it'll completely freeze for about 10 seconds when you play a new track or it goes to the next track on the playlist. The music plays but Amarok is unresponsive to anything until it unfreezes itself.

This seemed to start happening after I installed the codecs from the medibuntu repo using the commands from here - [http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html](http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html)

I also recently tried to switch from ALSA to OSS4, but switched back after OSS4 didn't work with most apps.

I tried uninstalling the medibuntu codecs and reinstalling the codecs from the normal repository, but now Amarok refuses to play mp3s, even though the gstreamer plugins are shown as installed in Add/Remove. Clicking 'Install mp3 support' does nothing.

I'm using Amarok 1.4 and Jaunty.

---

### Post by vinutux on 2009-07-29
check what version of gstreamer you are installed.... **Synaptic> right clik gstreamer pakage > properties > version**

if you installed third party gstreamers....you want to force to default > **pakage menu > force version**

---

### Post by themusicalduck on 2009-07-30
I chose to use the previous version on packages gstreame0.10-ffmpeg and gstreamer0.10-pulseaudio, but it doesn't seem to have made a difference. Also update manager is now asking me to re-update, even though I disabled the medibuntu repository.

---

