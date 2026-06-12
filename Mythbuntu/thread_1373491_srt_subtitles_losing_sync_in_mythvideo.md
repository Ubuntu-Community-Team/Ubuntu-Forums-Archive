---
title: "srt subtitles losing sync in mythvideo"
date: 2010-01-05
forum: Mythbuntu
---

### Post by mxander on 2010-01-05
Hello everyone. I've been using MythTV (Mythbuntu 8.04) for some time now and decided to upgrade from my P3 1ghz to something more juicy (core 2 duo 2. and to Mythtv 0.22 (Mythbuntu 9.10). Most of the stuff worked almost out of the box (serial lirc, PVR-150, SPDIF, VDPAU) but... In Mythvideo .srt subtitles lose sync with video. Sync is recovered with pause or step forward. The files look ok if playing in VLC. Have you heard about it? Another thing, how do I change the subtitle font size?

---

### Post by mxander on 2010-01-10
I've found there is an open ticket for this issue:
"http://svn.mythtv.org/trac/ticket/7515"
[http://svn.mythtv.org/trac/ticket/7515](http://svn.mythtv.org/trac/ticket/7515)
There is a patch to solve this issue.
Tried to follow the instructions on this page:

[http://ubuntuforums.org/showthread.php?t=758593](http://ubuntuforums.org/showthread.php?t=758593)
But I cannot manage to follow the first step of their Howto:
"[Newbie/8.04]Mythstream, Mythbrowser, Howto apply patches?"

sudo apt-get build-dep mythtv
[sudo] password for MyUserName: 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
The following packages have unmet dependencies:
nvidia-185-libvdpau-dev: Depends: nvidia-185-libvdpau (>= 185.18.36) but it is not going to be installed
E: Build-dependencies for mythtv could not be satisfied.

---

