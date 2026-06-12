---
title: "openshot 3.0.0 installation Ubuntu 22.04.2 LTS"
date: 2023-04-05
forum: Multimedia Software
---

### Post by ubontik22 on 2023-04-05
Hello,

I'm trying to install an Openshot
```

$ sudo add-apt-repository ppa:openshot.developers/ppa
$ sudo apt update
$ sudo apt install openshot-qt python3-openshot
```
and getting this messages:
```
The following packages have unmet dependencies: libopenshot23 : Depends: libavcodec58 (>= 7:4.4)
                 Depends: libavformat58 (>= 7:4.4)
 libqt5webenginecore5 : Depends: libavcodec58 (>= 7:4.4)
                        Depends: libavformat58 (>= 7:4.4)
E: Unable to correct problems, you have held broken packages.
```
How to fix this?
Thank you.

---

### Post by Dennis N on 2023-04-05
Install the Flatpak version and you shouldn't get dependency problems:

```
[dmn@Sydney ~]$ flatpak list --app | grep OpenShot
OpenShot Video Editor	org.openshot.OpenShot	3.0.0	stable	system

```

I have this Flatpak installed and no problem with dependencies.

---

### Post by ajgreeny on 2023-04-05
What versions of **libavcodec58** and **libavformat58** do you have installed or available?

On my install of Xubuntu 22.04.2 I have 
**libavcodec58**/jammy-updates,jammy-security 7:4.4.2-0ubuntu0.22.04.1 amd64
and
**libavformat58**/jammy-updates,jammy-security 7:4.4.2-0ubuntu0.22.04.1 amd64
Both of which would satisfy your dependency requirements.

Show us the output of ```
apt search libavcodec58
``` and ```
apt search libavformat58
```

Both of those packages are in the Universe repos so make sure they are enabled or you will not find them.

---

### Post by ubontik22 on 2023-04-05
> $ apt search libavcodec58Sorting... Done
Full Text Search... Done
libavcodec-extra58/jammy 7:4.4.3-0ubuntu1~22.04.sav3 amd64
  FFmpeg library with additional de/encoders for audio/video codecs


libavcodec58/jammy 7:4.4.3-0ubuntu1~22.04.sav3 amd64
  FFmpeg library with de/encoders for audio/video codecs - runtime files
$ apt search libavformat58
Sorting... Done
Full Text Search... Done
libavformat-extra58/jammy 7:4.4.3-0ubuntu1~22.04.sav3 amd64
  FFmpeg library with additional (de)muxers for multimedia containers


libavformat58/jammy 7:4.4.3-0ubuntu1~22.04.sav3 amd64
  FFmpeg library with (de)muxers for multimedia containers - runtime files.

---

### Post by ubontik22 on 2023-04-05
Thanks to all. I've installed with [COLOR=#000000][FONT=&quot]flatpak[/FONT][/COLOR]

---

