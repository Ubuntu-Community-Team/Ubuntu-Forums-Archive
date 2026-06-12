---
title: "mpd crashes repeatedly"
date: 2011-03-29
forum: Multimedia Software
---

### Post by hibob on 2011-03-29
Hi everyone,
I'm using mpd on Ubuntu Lucid and channeling output through pulseaudio.

every few hours or so mpd will crash.
```
sudo dpkg-reconfigure mpd
``` will bring it back, but it's still very annoying.

`dmesg | tail` gives me
```
[55188.955785] mpd[1126] general protection ip:1422525 sp:b6db4850 error:0 in libavcodec.so.52.20.1[fd5000+531000]

```I also see this message when I restart mpd:
```
bob@bob-laptop:~$ sudo dpkg-reconfigure mpd
[sudo] password for bob: 
 * Stopping Music Player Daemon mpd                                                              [ OK ] 
 * Starting Music Player Daemon mpd
listen: bind to 127.0.0.1:6600 failed: Address already in use (continuing anyway, because at least one address is bound)
                                                                                                                    [ OK ]
bob@bob-laptop:~$ 

```Please help.
Thanks.

---

