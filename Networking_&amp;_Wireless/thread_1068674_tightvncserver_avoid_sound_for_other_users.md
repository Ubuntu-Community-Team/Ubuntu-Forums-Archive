---
title: "tightvncserver: avoid sound for other users"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by flapane on 2009-02-13
Hi
if I try to launch via remote ssh a tightvncserver session (desktop :1) 
> 
#! /bin/bash
tightvncserver :1 -geometry 1280x1024

for the same username already logged locally, and then try to play some audio file, the local user (desktop :0) can hear that sound from my remote :1 session.
Furthermore, all the windows of the local user become closed whenever a remote user tries to login
Any way to avoid this?

---

