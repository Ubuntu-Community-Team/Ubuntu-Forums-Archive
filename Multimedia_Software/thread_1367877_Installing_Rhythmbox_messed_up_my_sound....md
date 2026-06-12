---
title: "Installing Rhythmbox messed up my sound..."
date: 2009-12-30
forum: Multimedia Software
---

### Post by buntolith on 2009-12-30
Hi,

I had a perfectly tuned Kubuntu 9.10 running but I had some problems to get Amarok to play streaming audio. So I installed Rhythmbox because I know it works fine to listen to streaming radio in Ubuntu. There was also a bunch of pulse audio drivers that came as a dependency with Rhythmbox. After install I could get the streaming radio to work but now I can't watch youtube *.flv anymore. The video is playing in double speed with no sound.

I have removed Rhythmbox but I still have the same problem. I don't think I managed to remove all the pulse audio files. What can I do to fix the problem?

---

### Post by Yellow Pasque on 2009-12-30
Remove pulseaudio. Purge (or 'completely remove') as many pulseaudio packages as you can (including gstreamer0.10-pulseaudio). Make sure there are no hidden .pulse files/folders in your user's home directory.

> bunch of pulse audio drivers that came as a dependency with Rhythmbox.
Rhythmbox doesn't need pulseaudio. Maybe you can just install RB like:
```
sudo apt-get install gstreamer0.10-alsa
sudo apt-get --no-install-recommends install rhythmbox
```

---

### Post by buntolith on 2009-12-30
Ok, so if I go ```
dpkg -l | grep pulse
``` I get the following result:

ii  gstreamer0.10-pulseaudio              0.10.16-1ubuntu3                           GStreamer plugin for PulseAudio
ii  libpulse-browse0                      1:0.9.19-0ubuntu4                          PulseAudio client libraries (zeroconf suppor
ii  libpulse-mainloop-glib0               1:0.9.19-0ubuntu4                          PulseAudio client libraries (glib support)
ii  libpulse0                             1:0.9.19-0ubuntu4                          PulseAudio client libraries
ii  pulseaudio                            1:0.9.19-0ubuntu4                          PulseAudio sound server
ii  pulseaudio-esound-compat              1:0.9.19-0ubuntu4                          PulseAudio ESD compatibility layer
ii  pulseaudio-module-udev                1:0.9.19-0ubuntu4                          udev device detection module for PulseAudio
ii  pulseaudio-module-x11                 1:0.9.19-0ubuntu4                          X11 module for PulseAudio sound server
ii  pulseaudio-utils                      1:0.9.19-0ubuntu4                          Command line tools for the PulseAudio sound
ii  vlc-plugin-pulse                      1.0.2-1ubuntu2

Would it be ok to just go ```
sudo apt-get --purge remove package-name
``` on all of these packages?

---

### Post by Yellow Pasque on 2009-12-30
Yes, although make sure no other packages are removed. You may have to keep the libpulse packages installed, but that's ok.

---

### Post by buntolith on 2009-12-30
Ok, I will try. Thanks a lot for your help. I will report back when I am done...

---

### Post by buntolith on 2009-12-30
Yes. That fixed the problem. I went ```
$ sudo aptitude --purge remove gstreamer0.10-pulseaudio pulseaudio pulseaudio-esound-compat pulseaudio-module-udev pulseaudio-module-x11 pulseaudio-utils vlc-plugin-pulse
``` and I got the following...```
The following packages will be REMOVED:
  gnome-icon-theme{ap} gnome-media{ap} gnome-media-common{ap} gstreamer0.10-pulseaudio{a}
  libcanberra-gtk-module{ap} libcanberra-gtk0{ap} libgnome-media0{ap} libpulse-browse0{ap}
  libpulse-mainloop-glib0{ap} librsvg2-common{ap} libspeexdsp1{ap} media-player-info{ap} pulseaudio{a}
  pulseaudio-esound-compat{a} pulseaudio-module-udev{a} pulseaudio-module-x11{a} pulseaudio-utils{a}
  python-gconf{ap} python-gnome2{ap} python-gnomecanvas{ap} python-gst0.10{ap} python-pyorbit{ap}
  vlc-plugin-pulse
0 packages upgraded, 0 newly installed, 23 to remove and 0 not upgraded
```Some more packages than what I expected but I put my faith in aptitude and let it get on with it. 

Now I am listening to Norah Jones on youtube and it's working great. Thank's for your help Temüjin!

---

