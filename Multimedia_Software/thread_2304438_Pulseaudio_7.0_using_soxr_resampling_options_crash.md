---
title: "Pulseaudio 7.0 using soxr resampling options crash repeatedly."
date: 2015-11-26
forum: Multimedia Software
---

### Post by rickard-s on 2015-11-26
I am using Pulseaudio 7 from **ppa:ubuntu-audio-dev/pulse-testing **under Wily and using soxr-mq, soxr-hq and soxr-vhq makes a lot of programs crash as soon as audio is going to be played. Mostly it's apps that I think is using gstreamer like Quod Libet and Lollypop which makes the programs look for codecs. The codec search ends when using src or speex. I have configured daemon.conf correctly exactly like I have done in other distros that do work. Is this a bug in the build or something or maybe soxr-lsr0 is having problem being used by pulseaudio?

---

### Post by Yellow Pasque on 2015-11-26
It might help if you could get specific error messages related to the crash that you/we can google.
Also, it would be nice to make a distinction between "mostly" gstreamer apps and "only" gstreamer apps.

---

### Post by Yellow Pasque on 2015-11-26
Oh, I see. The maintainer for Debian and pulse-testing forgot to add the dependency on libsoxr, and then pulseaudio also had a bug in it where it falsely reported that sox resamplers were available:
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=804212](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=804212)
[http://cgit.freedesktop.org/pulseaudio/pulseaudio/commit/?id=daf326a9e4dcd5c9d716e6c2fc0a07b99f6ee1c0](http://cgit.freedesktop.org/pulseaudio/pulseaudio/commit/?id=daf326a9e4dcd5c9d716e6c2fc0a07b99f6ee1c0)

Bottom line? Wait for pulse-testing PPA to update to 7.1 (or build your own pulseaudio) if you want to use the sox resamplers.

---

