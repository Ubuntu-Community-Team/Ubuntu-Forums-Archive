---
title: "No gstreamer plugins found"
date: 2008-08-12
forum: Multimedia Software
---

### Post by suryapraveen on 2008-08-12
hi 

i am using dell vostro 1000
and have installed hardy yesterday and couldnot fix this.

i installed module-asistant and also alsa and tried good,bad and ugly


nothing works.


needed help please.

---

### Post by cor2y on 2008-08-12
What version of Ubuntu are you using 32bit or 64bit?
Also enable all the repos.
Universe, Restricted and Multiverse then search via synaptic for gstreamer0.10 all the gstreamer plugins should be listed.
To enable repos see this [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
Here are the needed gstreamer plugins
Ok here are the needed gstreamer plugins
gstreamer0.10-ffmpeg (ffmpeg support)
gstreamer0.10-fluendo-mp3 (mp3 support/playback)
gstreamer0.10-pitfdll (to use the w32codec pack if installed)
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse

Optional Plugins
gstreamer0.10-fluendo-mpegdemux
gstreamer0.10-fluendo-mpegmux

---

### Post by suryapraveen on 2008-08-12
still the same problem

have done evrything

---

### Post by cor2y on 2008-08-13
Sorry for misreading the problem.
The problem is probably a loss of permission for the sound device tied to your login.
See the fix [here](http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/)

---

### Post by suryapraveen on 2008-08-13
i got this error message when i tried to dot that 
and i think its not 386 but i386.

i tried that to still the same problem
sudo apt-get install linux-ubuntu-modules-2.6.22-14-386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-ubuntu-modules-2.6.22-14-386

---

