---
title: "vlc errors"
date: 2018-04-09
forum: Multimedia Software
---

### Post by monkeybrain20122 on 2018-04-09
When I use vlc to play a video (.mp4) in the terminal I get a bunch of errors like 


```
[0000000000a711a0] main libvlc error: stale plugins cache: modified /usr/local/lib/vlc/plugins/video_filter/libgrain_plugin.so
[0000000000a711a0] main libvlc error: stale plugins cache: modified /usr/local/lib/vlc/plugins/video_filter/libcolorthres_plugin.so
[0000000000a711a0] main libvlc error: stale plugins cache: modified /usr/local/lib/vlc/plugins/video_filter/libwave_plugin.so
[0000000000a711a0] main libvlc error: stale plugins cache: modified /usr/local/lib/vlc/plugins/video_filter/libball_plugin.so
[0000000000a711a0] main libvlc error: stale plugins cache: modified /usr/local/lib/vlc/plugins/video_filter/libscene_plugin.so
[0000000000a711a0] main libvlc error: stale plugins cache: modified /usr/local/lib/vlc/plugins/video_filter/libpostproc_plugin.so
[0000000000a711a0] main libvlc error: stale plugins cache: modified /usr/local/lib/vlc/plugins/video_filter/libedgedetection_plugin.so
[0000000000a711a0] main libvlc error: stale plugins cache: modified /usr/local/lib/vlc/plugins/video_filter/libdeinterlace_plugin.so
[0000000000a711a0] main libvlc error: stale plugins cache: modified /usr/local/lib/vlc/plugins/video_filter/libmagnify_plugin.so
[0000000000a711a0] main libvlc error: stale plugins cache: modified /usr/local/lib/vlc/plugins/video_filter/libcroppadd_plugin.so
[0000000000a711a0] main libvlc error: stale plugins cache: modified /usr/local/lib/vlc/plugins/video_filter/libsharpen_plugin.so
[0000000000a711a0] main libvlc error: stale plugins cache: modified /usr/local/lib/vlc/plugins/video_filter/libscale_plugin.so
[0000000000a711a0] main libvlc error: stale plugins cache: modified /usr/local/lib/vlc/plugins/video_filter/libcanvas_plugin.so
[0000000000a711a0] main libvlc error: stale plugins cache: modified /usr/local/lib/vlc/plugins/video_splitter/libpanoramix_plugin.so
[0000000000a711a0] main libvlc error: stale plugins cache: modified /usr/local/lib/vlc/plugins/video_splitter/libwall_plugin.so

```

There are many more, but similar.

Also ```
egl_x11 gl error: cannot select OpenGL API


```

But otherwise it works, video does play and nothing seems wrong, last line of terminal output is
 ```
avcodec decoder: Using NVIDIA VDPAU Driver Shared Library  390.48  Wed Mar 21 23:47:29 PDT 2018 for hardware decoding

```

Wonder why those errors and if I need to fix them.

vlc 3.0.2 on Ubuntu 16.04, compiled against  ffmpeg and libav libs 3.4.1 from [https://launchpad.net/~mc3man/+archive/ubuntu/xerus-media](https://launchpad.net/~mc3man/+archive/ubuntu/xerus-media) and qt5.9.4 (compiled locally in my $HOME) if that is relevant.

Thanks.

**Edited:** the stale plugins errors occur just by starting vlc in the terminal without any video.

---

### Post by #&amp;thj^% on 2018-04-09
I had seen similar errors with 3.0 but upgraded to 4.0.0-dev.
Now shows:
```
vlc
VLC media player 4.0.0-dev Otto Chriek (revision 4.0.0-dev-2226-g4bd4423629)
[000055f0760e2320] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
qt5ct: using qt5ct plugin
qt5ct: D-Bus global menu: no
qt5ct: D-Bus system tray: no
[000055f0760e56e0] main playlist: playlist is empty

```
It looks, at quick glance that QT5 and OpenGl are a bit dated on xenial.
Maybe mc4man can give more insight here.
BTW VLC  4.0.0 is looking pretty nice at this stage. ;)

---

### Post by monkeybrain20122 on 2018-04-09
> **1fallen said:**
> 
It looks, at quick glance that QT5 and OpenGl are a bit dated on xenial.


I built vlc against qt5.9.4 which is very new, OpenGL is rendered by Nvidia's driver on this machine, my driver version is 390.48 (the newest). I see the same errors on an intel machine (vlc 3.0.0 there) with the same qt5 set up and opengl is rendered by mesa 18.0.0 which is the latest stable (from  padoka ppa)

---

### Post by #&amp;thj^% on 2018-04-09
> **monkeybrain20122 said:**
> I built vlc against qt5.9.4 which is very new, OpenGL is rendered by Nvidia's driver on this machine, my driver version is 390.48 (the newest). I see the same errors on an intel machine (vlc 3.0.0 there) with the same qt5 set up and opengl is rendered by mesa 18.0.0 which is the latest stable (from  padoka ppa)
Yes I too seen those errors with VLC  3.0.0 on both intel and nvidia.
Bear in mind I often times run a lot of Newer versions as a tester so maybe I'm not so helpful here for you.
EG:
```
qt5-base 5.10.1-7

```
And:
```
: mesa
Version         : 18.0.0-2

```
VLC 3.0 was not my favorite lots of oddities for both my machines.
Kind regards

---

### Post by monkeybrain20122 on 2018-04-09
> **1fallen said:**
> 
VLC 3.0 was not my favorite lots of oddities for both my machines.


I use it for the odd 360 degree videos :) Otherwise I use mpv+Smplayer.

---

### Post by mc4man on 2018-04-09
Don't use vlc much, on 16.04 the 2.8 is generally ok (- doesn't handle vaapi correctly unless set specifically, nvidia is ok, I've only optimus machines.
In 18.04 only have the 4.x snap, it can't do hwdec on nvidia at all, as I remember the 3.x .deb did, sorta.. (- vlc cannot use nvidia drivers with an OpenGl output

As far as the stale plugins you could probably fix by _adjusting this command_ to reflect your /usr/local install locations
sudo /usr/lib/vlc/vlc-cache-gen  /usr/lib/vlc/plugins/

(- for a repo install on 64 bit install command would be 
```
sudo  /usr/lib/x86_64-linux-gnu/vlc/vlc-cache-gen /usr/lib/x86_64-linux-gnu/vlc/plugins
```

---

### Post by monkeybrain20122 on 2018-04-10
> **mc4man said:**
> 

As far as the stale plugins you could probably fix by _adjusting this command_ to reflect your /usr/local install locations
sudo /usr/lib/vlc/vlc-cache-gen -f /usr/lib/vlc/plugins/

Hi, 

```
 sudo /usr/local/lib/vlc/vlc-cache-gen /usr/local/lib/vlc/plugins/ 
```

works (it complains about the -f option being invalid)

What does it do though?

Thanks a lot!!

---

### Post by mc4man on 2018-04-10
> **monkeybrain20122 said:**
> Hi, 

```
 sudo /usr/local/lib/vlc/vlc-cache-gen /usr/local/lib/vlc/plugins/ 
```

works (it complains about the -f option being invalid)

What does it do though?

Thanks a lot!!
I gather it refreshes the 'list' of actual installed plugins. In your /usr/local/lib/vlc/plugins/ folder there would be a file named plugins.dat. That is what vlc-cache-gen generates. (to see remove plugins.dat, run the vlc-cache-gen command, it'll be created.

---

