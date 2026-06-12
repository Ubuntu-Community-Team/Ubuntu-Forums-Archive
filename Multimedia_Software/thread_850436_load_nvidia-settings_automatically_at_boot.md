---
title: "load nvidia-settings automatically at boot"
date: 2008-07-05
forum: Multimedia Software
---

### Post by notmyidea on 2008-07-05
I am trying to get my nvidia-settings to load at boot up, automatically.

according to its documentation, you create a .xinitrc script that looks like so:

```
#!/usr/bin/env bash
# Custom Script to load nvidia settings at boot
# July 5, 2008

# Load in my NVidia Settings!!
nvidia-settings --load-config-only &

. /etc/X11/xinit/xinitrc

```

Upon doing so, nothing happens.  I then did a symbolic link to .xsession according to this wiki:
[https://wiki.ubuntu.com/CustomXSession]("https://wiki.ubuntu.com/CustomXSession")

Upon doing that, X fails to load. Attached is the .xsession-errors.  I am running Ubuntu 8.04.1, fresh install from two days ago.  Any help would be appreciated!!  Thanks, Jason


**Solved by System->Preferences->Sessions and adding nvidia-settings --load-config-only**

---

