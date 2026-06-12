---
title: "Problem with Movie Player"
date: 2013-05-27
forum: Multimedia Software
---

### Post by Sachil on 2013-05-27
Using Movie Player on Ubuntu 12.04.  Whenever I try to open a .mpg file, I get the message: 

"Python (v2.7) requires to install plugins to play media files of the following type: MPEG-1 video decoder"

When it tries to install missing plugins, it reports the following:

[I]Package depencies cannot be resolved

 The following packages have unmet dependencies:

gstreamer0.10-ffmpeg: Depends: libavcodec-extra-53 (>= 4:0.7.3-1) but 4:0.8.6ubuntu0.12.04.1 is to be installed
                      Depends: libavformat-extra-53 (>= 4:0.7.3-1) but 4:0.8.6ubuntu0.12.04.1 is to be installed
                      Depends: libavutil-extra-51 (>= 4:0.7.3-1) but 4:0.8.6ubuntu0.12.04.1 is to be installed
                      Depends: libc6 (>= 2.7) but 2.15-0ubuntu10.4 is to be installed
                      Depends: libglib2.0-0 (>= 2.31.2) but 2.32.3-0ubuntu1 is to be installed
                      Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.31) but 0.10.36-1ubuntu0.1 is to be installed
                      Depends: libgstreamer0.10-0 (>= 0.10.31) but 0.10.36-1ubuntu1 is to be installed
                      Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                      Depends: libpostproc-extra-52 (>= 4:0.7.3-1) but 4:0.8.6ubuntu0.12.04.1 is to be installed
                      Depends: libswscale-extra-2 (>= 4:0.7.3-1) but 4:0.8.6ubuntu0.12.04.1 is to be installed
gstreamer0.10-ffmpeg:i386: Depends: libavcodec-extra-53 (>= 4:0.7.3-1) but 4:0.8.6ubuntu0.12.04.1 is to be installed
                           Depends: libavformat-extra-53 (>= 4:0.7.3-1) but 4:0.8.6ubuntu0.12.04.1 is to be installed
                           Depends: libavutil-extra-51 (>= 4:0.7.3-1) but 4:0.8.6ubuntu0.12.04.1 is to be installed
                           Depends: libc6 (>= 2.7) but 2.15-0ubuntu10.4 is to be installed
                           Depends: libglib2.0-0 (>= 2.31.2) but 2.32.3-0ubuntu1 is to be installed
                           Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.31) but 0.10.36-1ubuntu0.1 is to be installed
                           Depends: libgstreamer0.10-0 (>= 0.10.31) but 0.10.36-1ubuntu1 is to be installed
                           Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                           Depends: libpostproc-extra-52 (>= 4:0.7.3-1) but 4:0.8.6ubuntu0.12.04.1 is to be installed
                           Depends: libswscale-extra-2 (>= 4:0.7.3-1) but 4:0.8.6ubuntu0.12.04.1 is to be installed
gstreamer0.10-plugins-bad:i386: Depends: libc6 (>= 2.15) but 2.15-0ubuntu10.4 is to be installed
                                Depends: libcairo2 (>= 1.2.4) but 1.10.2-6.1ubuntu3 is to be installed
                                Depends: libcdaudio1 (>= 0.99.12p2) but 0.99.12p2-10build1 is to be installed
                                Depends: libcurl3-gnutls (>= 7.16.2-1) but 7.22.0-3ubuntu4.1 is to be installed
                                Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                                Depends: libglib2.0-0 (>= 2.31.8) but 2.32.3-0ubuntu1 is to be installed
                                Depends: libgsm1 (>= 1.0.13) but 1.0.13-3 is to be installed
                                Depends: libgstreamer-plugins-bad0.10-0 (= 0.10.22.3-2ubuntu2.2) but 0.10.22.3-2ubuntu2.2 is to be installed
                                Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.36) but 0.10.36-1ubuntu0.1 is to be installed
                                Depends: libgstreamer0.10-0 (>= 0.10.36) but 0.10.36-1ubuntu1 is to be installed
                                Depends: libmpcdec6 (>= 1:0.1~r435) but 2:0.1~r459-1ubuntu1 is to be installed
                                Depends: libopenal1 (>= 1:1.13) but 1:1.13-4ubuntu3 is to be installed
                                Depends: libopenspc0 but it is not going to be installed
                                Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                                Depends: libpng12-0 (>= 1.2.13-4) but 1.2.46-3ubuntu4 is to be installed
                                Depends: librsvg2-2 (>= 2.14.4) but 2.36.1-0ubuntu1 is to be installed
                                Depends: librtmp0 (>= 2.3) but 2.4~20110711.gitc28f1bab-1 is to be installed
                                Depends: libschroedinger-1.0-0 (>= 1.0.9) but 1.0.11-1 is to be installed
                                Depends: libsndfile1 (>= 1.0.20) but 1.0.25-4 is to be installed
                                Depends: libssl1.0.0 (>= 1.0.0) but 1.0.1-4ubuntu5.9 is to be installed
                                Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is to be installed
                                Depends: libvpx1 (>= 1.0.0) but 1.0.0-1 is to be installed
                                Depends: libxvidcore4 (>= 1.2.2) but 2:1.3.2-6 is to be installed
gstreamer0.10-plugins-ugly: Depends: libc6 (>= 2.7) but 2.15-0ubuntu10.4 is to be installed
                            Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                            Depends: libglib2.0-0 (>= 2.31.2) but 2.32.3-0ubuntu1 is to be installed
                            Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu0.1 is to be installed
                            Depends: libgstreamer0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu1 is to be installed
                            Depends: libmad0 (>= 0.15.1b-3) but 0.15.1b-7ubuntu1 is to be installed
                            Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                            Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is to be installed
gstreamer0.10-plugins-ugly:i386: Depends: libc6 (>= 2.7) but 2.15-0ubuntu10.4 is to be installed
                                 Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                                 Depends: libglib2.0-0 (>= 2.31.2) but 2.32.3-0ubuntu1 is to be installed
                                 Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu0.1 is to be installed
                                 Depends: libgstreamer0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu1 is to be installed
                                 Depends: libmad0 (>= 0.15.1b-3) but 0.15.1b-7ubuntu1 is to be installed
                                 Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                                 Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is to be installed
[/I]
What do I do?

Thanks!

---

### Post by monkeybrain2012 on 2013-05-28
install gstreamer-plugins-bad and gstreamer-plugins-ugly.

---

### Post by Sachil on 2013-05-28
gstreamer-plugins-bad installed, but gstreamer-plugins-ugly didnt: 

"E: Unable to locate package gstreamer-plugins-ugly"

---

### Post by monkeybrain2012 on 2013-05-28
Ok, sorry, install Ubuntu-restricted-extras. When you install it a popup will appear asking you to agree to MicroSoft's EULA to install its fonts, just press Enter to skip it and it won't be installed. I don't know why they package it along with other codecs.

---

### Post by Sachil on 2013-05-28
Monkey brains must be the brains of genuises.  It worked :D

So can I uninstall gstreamer-plugins-bad, or do I still need that?

FYI, when I installed Ubuntu-restricted-extras, there was no popup whatsoever...

---

### Post by davie1994 on 2013-09-27
Hi guys,

I've been having a similar problem to Sachil. Here's the exact details :

 The following packages have unmet dependencies:

gstreamer0.10-plugins-ugly: Depends: libc6 (>= 2.7) but 2.15-0ubuntu10.4 is to be installed
                            Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                            Depends: libglib2.0-0 (>= 2.31.2) but 2.32.3-0ubuntu1 is to be installed
                            Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu0.1 is to be installed
                            Depends: libgstreamer0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu1 is to be installed
                            Depends: libmad0 (>= 0.15.1b-3) but 0.15.1b-7ubuntu1 is to be installed
                            Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                            Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is to be installed
gstreamer0.10-plugins-ugly:i386: Depends: libc6 (>= 2.7) but 2.15-0ubuntu10.4 is to be installed
                                 Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                                 Depends: libglib2.0-0 (>= 2.31.2) but 2.32.3-0ubuntu1 is to be installed
                                 Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu0.1 is to be installed
                                 Depends: libgstreamer0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu1 is to be installed
                                 Depends: libmad0 (>= 0.15.1b-3) but 0.15.1b-7ubuntu1 is to be installed
                                 Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                                 Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is to be installed


I tried to install ubuntu restriced extras but was told to delete libav codec libary and libav utility library first. When I tried to look for either of these two things on the software centre nothing came up.

Please help as I'm very confused

Davie

---

