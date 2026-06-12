---
title: "amarok can't play mp3 or ogg anymore, wma and mpg work"
date: 2010-03-26
forum: Multimedia Software
---

### Post by KIAaze on 2010-03-26
Hi,

I can't play any mp3 or ogg files in amarok anymore.
.wma and .mpg files still seem to work.
Everything works fine in Rhytmbox.

distro: Kubuntu 9.10

Sound related packages:
```
ii  pulseaudio                               1:0.9.19-0ubuntu4.1                        PulseAudio sound server
ii  pulseaudio-esound-compat                 1:0.9.19-0ubuntu4.1                        PulseAudio ESD compatibility layer
ii  pulseaudio-module-udev                   1:0.9.19-0ubuntu4.1                        udev device detection module for PulseAudio
ii  pulseaudio-module-x11                    1:0.9.19-0ubuntu4.1                        X11 module for PulseAudio sound server
ii  pulseaudio-utils                         1:0.9.19-0ubuntu4.1                        Command line tools for the PulseAudio sound
ii  alsa-base                                1.0.20+dfsg-1ubuntu5                       ALSA driver configuration files
ii  alsa-oss                                 1.0.17-1                                   ALSA wrapper for OSS applications
ii  alsa-utils                               1.0.20-2ubuntu6                            ALSA utilities
ii  oss-compat                               0.0.4+nmu3                                 OSS compatibility package
ii  phonon                                   4:4.3.1-4ubuntu1                           metapackage for Phonon multimedia framework
ii  phonon-backend-gstreamer                 4:4.3.1-4ubuntu1                           Phonon GStreamer 0.10.x backend
ii  phonon-backend-xine                      4:4.3.1-4ubuntu1                           Phonon Xine 1.1.x backend
ii  amarok                                   2:2.2.0-0ubuntu2                           easy to use media player based on the KDE 4 technology platform
ii  amarok-common                            2:2.2.0-0ubuntu2                           architecture independent files for Amarok
ii  amarok-utils                             2:2.2.0-0ubuntu2                           utilities for Amarok media player

```

Amarok version:
Qt: 4.5.2
KDE: 4.3.2 (KDE 4.3.2)
Amarok: 2.2.0

---

### Post by KIAaze on 2010-03-26
SOLVED! :)

First I tried upgrading to the latest stable amarok:
[http://amarok.kde.org/wiki/Download:Kubuntu](http://amarok.kde.org/wiki/Download:Kubuntu)

After that, it still didn't work, but I got a little message saying "phonon claims it cannot play mp3 files. You may want to examine the installation of the backend that phonon uses.".

After googling for this message I found this:
[http://ubuntuforums.org/showthread.php?t=951470](http://ubuntuforums.org/showthread.php?t=951470)

This did not work for me directly, but the following did:
```
mv ~/.xine{,.bak}
```

mp3 and ogg files work again. :guitar:

---

### Post by marriedman on 2010-12-04
> **KIAaze said:**
> This did not work for me directly, but the following did:
```
mv ~/.xine{,.bak}
```

mp3 and ogg files work again.

Dude, thank you. This was killing me. Could not figure this out. Who would have thought deleting that folder would fix mp3 playback?

---

### Post by thilina on 2011-02-10
I found an easier way than this.

[http://blog.ishans.info/2011/02/10/cant-play-songs-in-amarok-after-installing-it-in-ubuntu/](http://blog.ishans.info/2011/02/10/cant-play-songs-in-amarok-after-installing-it-in-ubuntu/)

:)

---

### Post by somakd on 2011-08-05
install 
libxine1-ffmpeg

sudo apt-get install libxine1-ffmpeg

and it works like charm :guitar:

---

### Post by Walking Turtle on 2011-12-09
Libxine1-ffmpeg was missing from my MEPIS 10.9.88 installation too.  Found the fix here, installed, and voilah!  Space Music all night long once more!

Thank you for this!  And that is all. :KS

---

