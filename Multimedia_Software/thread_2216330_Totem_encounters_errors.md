---
title: "Totem encounters errors"
date: 2014-04-11
forum: Multimedia Software
---

### Post by tthtlc on 2014-04-11
My version is:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"

Now after I clicked on one of the mp4 files, totem automatically start running, and immediately prompt me that it needs to install something.  

I acknowledge ok, and upon attempting to install some additional packages, the following is encountered:

>  The following packages have unmet dependencies:

gstreamer0.10-ffmpeg: Depends: libavcodec-extra-53 (>= 4:0.7.3-1) but 4:0.8.10ubuntu0.12.04.1 is to be installed
                      Depends: libavformat-extra-53 (>= 4:0.7.3-1) but 4:0.8.10ubuntu0.12.04.1 is to be installed
                      Depends: libavutil-extra-51 (>= 4:0.7.3-1) but 4:0.8.10ubuntu0.12.04.1 is to be installed
                      Depends: libc6 (>= 2.7) but 2.15-0ubuntu10.5 is to be installed
                      Depends: libglib2.0-0 (>= 2.31.2) but 2.32.4-0ubuntu1 is to be installed
                      Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.31) but 0.10.36-1ubuntu0.1 is to be installed
                      Depends: libgstreamer0.10-0 (>= 0.10.31) but 0.10.36-1ubuntu1 is to be installed
                      Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                      Depends: libpostproc-extra-52 (>= 4:0.7.3-1) but 4:0.8.10ubuntu0.12.04.1 is to be installed
                      Depends: libswscale-extra-2 (>= 4:0.7.3-1) but 4:0.8.10ubuntu0.12.04.1 is to be installed
gstreamer0.10-ffmpeg:i386: Depends: libavcodec-extra-53 (>= 4:0.7.3-1) but 4:0.8.10ubuntu0.12.04.1 is to be installed
                           Depends: libavformat-extra-53 (>= 4:0.7.3-1) but 4:0.8.10ubuntu0.12.04.1 is to be installed
                           Depends: libavutil-extra-51 (>= 4:0.7.3-1) but 4:0.8.10ubuntu0.12.04.1 is to be installed
                           Depends: libc6 (>= 2.7) but 2.15-0ubuntu10.5 is to be installed
                           Depends: libglib2.0-0 (>= 2.31.2) but 2.32.4-0ubuntu1 is to be installed
                           Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.31) but 0.10.36-1ubuntu0.1 is to be installed
                           Depends: libgstreamer0.10-0 (>= 0.10.31) but 0.10.36-1ubuntu1 is to be installed
                           Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                           Depends: libpostproc-extra-52 (>= 4:0.7.3-1) but 4:0.8.10ubuntu0.12.04.1 is to be installed
                           Depends: libswscale-extra-2 (>= 4:0.7.3-1) but 4:0.8.10ubuntu0.12.04.1 is to be installed

How do I install the additional packages needed?

Your help is much appreciated.

---

### Post by SeijiSensei on 2014-04-11
I'd start by installing the **ubuntu-restricted-extras** package.

---

