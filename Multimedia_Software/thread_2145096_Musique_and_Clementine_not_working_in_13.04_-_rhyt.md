---
title: "Musique and Clementine not working in 13.04 - rhythm box does?"
date: 2013-05-14
forum: Multimedia Software
---

### Post by kwildman on 2013-05-14
13.04 RR 32bit machine.

I have an extremely large music collection attached to a Drobo unit via USB.   Rhythm Box plays right out of the basic isntall.   I have enabled restricted formats as most music is mp3/wma/m4a.    Problem is that i really dont like Rhythm box.   I installed Clementine and get the following error trying to play files.[INDENT]
GStreamer could not create the element: audioconvert. Please make sure that you have installed all necessary GStreamer plugins (e.g. OGG and MP3)
[/INDENT]

I have checked packages and GStreamer is installed and current.

I have also installed Musique - the play buttons are all grayed out on all of my songs in my library.

Again RhythmBox plays fine. 

Thanks in advance for your help.

Kevin

---

### Post by Yellow Pasque on 2013-05-14
Rhythmbox has been updated to use gstreamer1.0, while the apps you list as problematic use gstreamer0.10. See if this helps:
```
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg
```

---

### Post by kwildman on 2013-05-15
Temujin - thanks for the reply.   My system reports that these items are already the current version installed.

Frustrating as Rhythmbox plays fine and is a decent application in itself but i prefer something that looks more polished.   I have been on both their support sites and cant find anything that leads in the right direction.

---

### Post by kurt18947 on 2013-05-15
Have you installed *buntu-restricted-extras from the repositories?  That will install codecs that are not open but required to play certain files.  It will also install a few Microsoft fonts so you'll need to agree to Microsoft's license to install those fonts.  Do you know about VLC?  VLC has a reputation for playing almost anything and can be found in the repositories.

---

### Post by kwildman on 2013-05-15
> **kurt18947 said:**
> Have you installed *buntu-restricted-extras from the repositories?  That will install codecs that are not open but required to play certain files.  It will also install a few Microsoft fonts so you'll need to agree to Microsoft's license to install those fonts.  Do you know about VLC?  VLC has a reputation for playing almost anything and can be found in the repositories.

Kurt - yes I have the all the restricted extras installed.   I have VLC and use it primarily for video.    I have a very large music collection.    Musique worked fine with 12.10.   Havent used Clementine since 11.04      Thanks for the comments.  :)

---

### Post by Jack Harper on 2013-05-15
Strange,I never had any issues with Clementine.Have you tried reinstalling the application and gstreamer plugins or checking the output in preferences?

This is my list of gstreamer,maybe it helps you to install what you are missing.

dpkg -l | grep gstreamer
ii  bluez-gstreamer                           4.101-0ubuntu8b1                       amd64        Bluetooth GStreamer support
ii  gir1.2-gstreamer-1.0                      1.0.6-1                                amd64        Description: GObject introspection data for the GStreamer library
ii  gstreamer0.10-alsa:amd64                  0.10.36-1.1ubuntu1                     amd64        GStreamer plugin for ALSA
ii  gstreamer0.10-ffmpeg:amd64                0.10.13-5                              amd64        FFmpeg plugin for GStreamer
ii  gstreamer0.10-fluendo-mp3:amd64           0.10.15.debian-1ubuntu1                amd64        Fluendo mp3 decoder GStreamer plugin
ii  gstreamer0.10-gconf:amd64                 0.10.31-3+nmu1ubuntu2                  amd64        GStreamer plugin for getting the sink/source information from GConf
ii  gstreamer0.10-gnomevfs:amd64              0.10.36-1.1ubuntu1                     amd64        GStreamer plugin for GnomeVFS
ii  gstreamer0.10-nice:amd64                  0.1.3-1                                amd64        ICE library (GStreamer plugin)
ii  gstreamer0.10-plugins-bad:amd64           0.10.23-7ubuntu2                       amd64        GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-base:amd64          0.10.36-1.1ubuntu1                     amd64        GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps           0.10.36-1.1ubuntu1                     amd64        GStreamer helper programs from the "base" set
ii  gstreamer0.10-plugins-good:amd64          0.10.31-3+nmu1ubuntu2                  amd64        GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-ugly:amd64          0.10.19-2                              amd64        GStreamer plugins from the "ugly" set
ii  gstreamer0.10-pulseaudio:amd64            0.10.31-3+nmu1ubuntu2                  amd64        GStreamer plugin for PulseAudio
ii  gstreamer0.10-tools                       0.10.36-1ubuntu2                       amd64        Tools for use with GStreamer
ii  gstreamer0.10-x:amd64                     0.10.36-1.1ubuntu1                     amd64        GStreamer plugins for X11 and Pango
ii  gstreamer1.0-alsa:amd64                   1.0.6-1                                amd64        GStreamer plugin for ALSA
ii  gstreamer1.0-clutter                      2.0.2-0ubuntu1                         amd64        Clutter PLugin for GStreamer 1.0
ii  gstreamer1.0-libav:amd64                  1.0.6-1                                amd64        FFmpeg plugin for GStreamer
ii  gstreamer1.0-nice:amd64                   0.1.3-1                                amd64        ICE library (GStreamer plugin)
ii  gstreamer1.0-plugins-bad:amd64            1.0.6-1ubuntu1                         amd64        GStreamer plugins from the "bad" set
ii  gstreamer1.0-plugins-base:amd64           1.0.6-1                                amd64        GStreamer plugins from the "base" set
ii  gstreamer1.0-plugins-base-apps            1.0.6-1                                amd64        GStreamer helper programs from the "base" set
ii  gstreamer1.0-plugins-good:amd64           1.0.6-1ubuntu1                         amd64        GStreamer plugins from the "good" set
ii  gstreamer1.0-plugins-ugly:amd64           1.0.6-1                                amd64        GStreamer plugins from the "ugly" set
ii  gstreamer1.0-pulseaudio:amd64             1.0.6-1ubuntu1                         amd64        GStreamer plugin for PulseAudio
ii  gstreamer1.0-tools                        1.0.6-1                                amd64        Tools for use with GStreamer
ii  gstreamer1.0-x:amd64                      1.0.6-1                                amd64        GStreamer plugins for X11 and Pango
ii  libgstreamer-plugins-bad0.10-0:amd64      0.10.23-7ubuntu2                       amd64        GStreamer shared libraries from the "bad" set
ii  libgstreamer-plugins-bad1.0-0:amd64       1.0.6-1ubuntu1                         amd64        GStreamer development files for libraries from the "bad" set
ii  libgstreamer-plugins-base0.10-0:amd64     0.10.36-1.1ubuntu1                     amd64        GStreamer libraries from the "base" set
ii  libgstreamer-plugins-base0.10-0:i386      0.10.36-1.1ubuntu1                     i386         GStreamer libraries from the "base" set
ii  libgstreamer-plugins-base1.0-0:amd64      1.0.6-1                                amd64        GStreamer libraries from the "base" set
ii  libgstreamer-plugins-good1.0-0:amd64      1.0.6-1ubuntu1                         amd64        GStreamer development files for libraries from the "good" set
ii  libgstreamer0.10-0:amd64                  0.10.36-1ubuntu2                       amd64        Core GStreamer libraries and elements
ii  libgstreamer0.10-0:i386                   0.10.36-1ubuntu2                       i386         Core GStreamer libraries and elements
ii  libgstreamer1.0-0:amd64                   1.0.6-1                                amd64        Core GStreamer libraries and elements
ii  phonon-backend-gstreamer:amd64            4:4.7.0really4.6.3-0ubuntu1            amd64        Phonon GStreamer 0.10.x backend

---

### Post by kwildman on 2013-05-15
Jack - thanks for the reply I am running 32bit on this machine.   I did try reinstalling the application and the gstreamer plugins.   I get the error listed in my OP for Clementine.   For Musique, there is no error.  I click play and nothing happens.  Its not just that there is no sound but that it does not show the timeline advancing, etc.    Here is my list of gstreamer in case that helps someone figure out where it broke.

dpkg -l|grep gstreamer
ii  bluez-gstreamer                           4.101-0ubuntu8b1                       i386         Bluetooth GStreamer support
ii  gir1.2-gstreamer-0.10                     0.10.36-1ubuntu2                       i386         Description: GObject introspection data for the GStreamer library
ii  gir1.2-gstreamer-1.0                      1.0.6-1                                i386         Description: GObject introspection data for the GStreamer library
ii  gstreamer0.10-alsa:i386                   0.10.36-1.1ubuntu1                     i386         GStreamer plugin for ALSA
ii  gstreamer0.10-ffmpeg:i386                 0.10.13-5                              i386         FFmpeg plugin for GStreamer
ii  gstreamer0.10-fluendo-mp3:i386            0.10.15.debian-1ubuntu1                i386         Fluendo mp3 decoder GStreamer plugin
ii  gstreamer0.10-gconf:i386                  0.10.31-3+nmu1ubuntu2                  i386         GStreamer plugin for getting the sink/source information from GConf
ii  gstreamer0.10-nice:i386                   0.1.3-1                                i386         ICE library (GStreamer plugin)
ii  gstreamer0.10-plugins-bad:i386            0.10.23-7ubuntu2                       i386         GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-bad-multiverse      0.10.21-1ubuntu1                       i386         GStreamer plugins from the "bad" set (Multiverse Variant)
ii  gstreamer0.10-plugins-base:i386           0.10.36-1.1ubuntu1                     i386         GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps           0.10.36-1.1ubuntu1                     i386         GStreamer helper programs from the "base" set
ii  gstreamer0.10-plugins-good:i386           0.10.31-3+nmu1ubuntu2                  i386         GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-ugly:i386           0.10.19-2                              i386         GStreamer plugins from the "ugly" set
ii  gstreamer0.10-pulseaudio:i386             0.10.31-3+nmu1ubuntu2                  i386         GStreamer plugin for PulseAudio
ii  gstreamer0.10-tools                       0.10.36-1ubuntu2                       i386         Tools for use with GStreamer
ii  gstreamer0.10-x:i386                      0.10.36-1.1ubuntu1                     i386         GStreamer plugins for X11 and Pango
ii  gstreamer1.0-alsa:i386                    1.0.6-1                                i386         GStreamer plugin for ALSA
ii  gstreamer1.0-clutter                      2.0.2-0ubuntu1                         i386         Clutter PLugin for GStreamer 1.0
ii  gstreamer1.0-libav:i386                   1.0.6-1                                i386         FFmpeg plugin for GStreamer
ii  gstreamer1.0-nice:i386                    0.1.3-1                                i386         ICE library (GStreamer plugin)
ii  gstreamer1.0-plugins-bad:i386             1.0.6-1ubuntu1                         i386         GStreamer plugins from the "bad" set
ii  gstreamer1.0-plugins-base:i386            1.0.6-1                                i386         GStreamer plugins from the "base" set
ii  gstreamer1.0-plugins-base-apps            1.0.6-1                                i386         GStreamer helper programs from the "base" set
ii  gstreamer1.0-plugins-good:i386            1.0.6-1ubuntu1                         i386         GStreamer plugins from the "good" set
ii  gstreamer1.0-plugins-ugly:i386            1.0.6-1                                i386         GStreamer plugins from the "ugly" set
ii  gstreamer1.0-pulseaudio:i386              1.0.6-1ubuntu1                         i386         GStreamer plugin for PulseAudio
ii  gstreamer1.0-tools                        1.0.6-1                                i386         Tools for use with GStreamer
ii  gstreamer1.0-x:i386                       1.0.6-1                                i386         GStreamer plugins for X11 and Pango
ii  libgstreamer-plugins-bad0.10-0:i386       0.10.23-7ubuntu2                       i386         GStreamer shared libraries from the "bad" set
ii  libgstreamer-plugins-bad1.0-0:i386        1.0.6-1ubuntu1                         i386         GStreamer development files for libraries from the "bad" set
ii  libgstreamer-plugins-base0.10-0:i386      0.10.36-1.1ubuntu1                     i386         GStreamer libraries from the "base" set
ii  libgstreamer-plugins-base1.0-0:i386       1.0.6-1                                i386         GStreamer libraries from the "base" set
ii  libgstreamer-plugins-good1.0-0:i386       1.0.6-1ubuntu1                         i386         GStreamer development files for libraries from the "good" set
ii  libgstreamer0.10-0:i386                   0.10.36-1ubuntu2                       i386         Core GStreamer libraries and elements
ii  libgstreamer1.0-0:i386                    1.0.6-1                                i386         Core GStreamer libraries and elements
ii  phonon-backend-gstreamer:i386             4:4.7.0really4.6.3-0ubuntu1            i386         Phonon GStreamer 0.10.x backend

---

### Post by Jack Harper on 2013-05-15
What do you have in this folder [COLOR=#000000][FONT=verdana]~/.gstreamer-0.10/[/FONT][/COLOR]

---

### Post by kwildman on 2013-05-15
Jack - the only file is

registry.i686.bin

---

### Post by Jack Harper on 2013-05-15
Try removing that file and try playing music after,if it doesnt work try rebooting (not sure when Gstreamer regenerates the folder).

---

### Post by kwildman on 2013-05-15
That got it!   Thanks for the help.   Musique is working fine now.   I am sure that Clementine will also if/when i reinstall it.     I appreciate everyone's help!

---

### Post by Jack Harper on 2013-05-15
> **kwildman said:**
> That got it!   Thanks for the help.   Musique is working fine now.   I am sure that Clementine will also if/when i reinstall it.     I appreciate everyone's help!

I am glad it worked :) You could mark your thread as Solved now if you want.

---

