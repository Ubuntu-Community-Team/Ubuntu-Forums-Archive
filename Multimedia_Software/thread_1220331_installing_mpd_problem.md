---
title: "installing mpd problem"
date: 2009-07-22
forum: Multimedia Software
---

### Post by UnsafeData on 2009-07-22
```
john@john-desktop:~$ sudo apt-get install mpd
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic dkms
  fglrx-kernel-source
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libfreebob0 libjack0 libmikmod2
Suggested packages:
  jackd mpd-client icecast2
The following NEW packages will be installed:
  libfreebob0 libjack0 libmikmod2 mpd
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 559kB of archives.
After this operation, 1606kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com intrepid/universe libfreebob0 1.0.11-0ubuntu1 [146kB]
Get:2 http://us.archive.ubuntu.com intrepid/universe libjack0 0.109.2-3ubuntu1 [120kB]
Get:3 http://us.archive.ubuntu.com intrepid/main libmikmod2 3.1.11-a-6ubuntu3 [145kB]
Get:4 http://us.archive.ubuntu.com intrepid/universe mpd 0.13.2-2ubuntu1 [148kB]
Fetched 559kB in 1s (320kB/s)
Selecting previously deselected package libfreebob0.
(Reading database ... 126204 files and directories currently installed.)
Unpacking libfreebob0 (from .../libfreebob0_1.0.11-0ubuntu1_i386.deb) ...
Selecting previously deselected package libjack0.
Unpacking libjack0 (from .../libjack0_0.109.2-3ubuntu1_i386.deb) ...
Selecting previously deselected package libmikmod2.
Unpacking libmikmod2 (from .../libmikmod2_3.1.11-a-6ubuntu3_i386.deb) ...
Selecting previously deselected package mpd.
Unpacking mpd (from .../mpd_0.13.2-2ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up libfreebob0 (1.0.11-0ubuntu1) ...

Setting up libjack0 (0.109.2-3ubuntu1) ...

Setting up libmikmod2 (3.1.11-a-6ubuntu3) ...

Setting up mpd (0.13.2-2ubuntu1) ...
 * Starting Music Player Daemon mpd                                              * creating /var/lib/mpd/tag_cache... 
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
                                                                         [ OK ]

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```


Uh it's at the bottom.

What do I do?

---

