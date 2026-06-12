---
title: "ffmpeg x11grab not working?"
date: 2016-03-26
forum: Multimedia Software
---

### Post by vasa1 on 2016-03-26
I'n on Lubuntu 14.04 which doesn't have ffmpeg by default but I installed it via a ppa:```
$ apt-cache policy ffmpeg
ffmpeg:
  Installed: 7:3.0.0+git~trusty
  Candidate: 7:3.0.0+git~trusty
  Version table:
 *** 7:3.0.0+git~trusty 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
$
```
When I run```
$ ffmpeg -f x11grab -s 1360x765 -r 30 -i :0.0 -qscale 0 -vcodec huffyuv ~/Desktop/$(date +%H%M%S).avi
```I get this:```
$ ffmpeg -f x11grab -s 1360x765 -r 30 -i :0.0 -qscale 0 -vcodec huffyuv ~/Desktop/$(date +%H%M%S).avi
ffmpeg version N-78590-g5590ab4 Copyright (c) 2000-2016 the FFmpeg developers
  built with gcc 4.8 (Ubuntu 4.8.4-2ubuntu1~14.04.1)
  configuration: --extra-libs=-ldl --prefix=/opt/ffmpeg --mandir=/usr/share/man --enable-avresample --disable-debug --enable-nonfree --enable-gpl --enable-version3 --enable-libopencore-amrnb --enable-libopencore-amrwb --disable-decoder=amrnb --disable-decoder=amrwb --enable-libpulse --enable-libfreetype --enable-gnutls --enable-libx264 --enable-libx265 --enable-libfdk-aac --enable-libvorbis --enable-libmp3lame --enable-libopus --enable-libvpx --enable-libspeex --enable-libass --enable-avisynth --enable-libsoxr --enable-libxvid --enable-libvidstab
  libavutil      55. 18.100 / 55. 18.100
  libavcodec     57. 24.103 / 57. 24.103
  libavformat    57. 25.100 / 57. 25.100
  libavdevice    57.  0.101 / 57.  0.101
  libavfilter     6. 32.100 /  6. 32.100
  libavresample   3.  0.  0 /  3.  0.  0
  libswscale      4.  0.100 /  4.  0.100
  libswresample   2.  0.101 /  2.  0.101
  libpostproc    54.  0.100 / 54.  0.100
Trailing options were found on the commandline.
Unknown input format: 'x11grab'
$ 
```I don't know much about ffmpeg but I remember this command had worked previously in 14.04 IIRC. That's why I have it in my notes.

The man page for ffmpeg has this command:```
ffmpeg -f x11grab -video_size cif -framerate 25 -i :0.0 /tmp/out.mpg
```
but even that doesn't work:```
$ ffmpeg -f x11grab -video_size cif -framerate 25 -i :0.0 ~/Desktop/out.mpg
ffmpeg version N-78590-g5590ab4 Copyright (c) 2000-2016 the FFmpeg developers
  built with gcc 4.8 (Ubuntu 4.8.4-2ubuntu1~14.04.1)
  configuration: --extra-libs=-ldl --prefix=/opt/ffmpeg --mandir=/usr/share/man --enable-avresample --disable-debug --enable-nonfree --enable-gpl --enable-version3 --enable-libopencore-amrnb --enable-libopencore-amrwb --disable-decoder=amrnb --disable-decoder=amrwb --enable-libpulse --enable-libfreetype --enable-gnutls --enable-libx264 --enable-libx265 --enable-libfdk-aac --enable-libvorbis --enable-libmp3lame --enable-libopus --enable-libvpx --enable-libspeex --enable-libass --enable-avisynth --enable-libsoxr --enable-libxvid --enable-libvidstab
  libavutil      55. 18.100 / 55. 18.100
  libavcodec     57. 24.103 / 57. 24.103
  libavformat    57. 25.100 / 57. 25.100
  libavdevice    57.  0.101 / 57.  0.101
  libavfilter     6. 32.100 /  6. 32.100
  libavresample   3.  0.  0 /  3.  0.  0
  libswscale      4.  0.100 /  4.  0.100
  libswresample   2.  0.101 /  2.  0.101
  libpostproc    54.  0.100 / 54.  0.100
Unknown input format: 'x11grab'
$
```
Even this:```
ffmpeg -video_size 1024x768 -framerate 25 -f x11grab -i :0.0+100,200 output.mp4
```from [https://trac.ffmpeg.org/wiki/Capture/Desktop](https://trac.ffmpeg.org/wiki/Capture/Desktop) doesn't work. It gives the same "Unknown input format: 'x11grab'".

Could it be that I'm using an Openbox session with no session manager?

According to [https://ffmpeg.org/ffmpeg-devices.html#toc-x11grab](https://ffmpeg.org/ffmpeg-devices.html#toc-x11grab),> 3.21 x11grab

X11 video input device.

To enable this input device during configuration you need libxcb installed on your system. It will be automatically detected during configuration.

Alternatively, the configure option --enable-x11grab exists for legacy Xlib users.

This device allows one to capture a region of an X11 display. I don't have *libxcb* nor is it available via *apt-get*.

---

### Post by TheFu on 2016-03-26
openbox is X11. No DE is needed.  X11 should be enough.  I haven't used ffmpeg for this in years and cannot test it (chromebook with crouton has wonky graphics issues), but there are simple GUIs for this today. SimpleScreenRecorder is what I've been using lately.  Does a nice job.  Doesn't need a super-powerful CPU either.  Use the PPA version for 14.04:
```
sudo add-apt-repository ppa:maarten-baert/simplescreenrecorder
sudo apt-get update
sudo apt-get install simplescreenrecorder
```  If you need more "production" features, then OBS Studio is nice, but needs a more powerful CPU.

I won't be moving servers to 16.04 for about a year, perhaps 2. Desktops, perhaps in July if there don't seem to be issues.  Most systems here are 14.04, with one 12.04 left to be migrated.

Don't feel pressured to a "new" OS - newer isn't always better. Personally, I think systemd needs 3 more years to simmer before it is ready.  I've already had issues with it on Debian systems.  Plus the systemd documentation is "aspirational", not what really works today.  To me, that is unacceptable.  Documentation needs to describe the system deployed, not some future, hope.

---

### Post by vasa1 on 2016-03-26
> **TheFu said:**
> ... SimpleScreenRecorder is what I've been using lately.  Does a nice job.  Doesn't need a super-powerful CPU either.  Use the PPA version for 14.04:
```
sudo add-apt-repository ppa:maarten-baert/simplescreenrecorder
sudo apt-get update
sudo apt-get install simplescreenrecorder
```...
Thank you! I read good things about SSR as well. I will give it a go.

---

### Post by mc4man on 2016-03-26
try installing libxcb-shm0 & libxcb-shape0
screen grab works here ok on 16.04, I won't be able to ck. trusty till this evening
In any event that trusty build is overdue for a new one, willsquare up one way or the other...

---

### Post by vasa1 on 2016-03-26
> **mc4man said:**
> try installing libxcb-shm0 & libxcb-shape0
screen grab works here ok on 16.04, I won't be able to ck. trusty till this evening
In any event that trusty build is overdue for a new one, willsquare up one way or the other...
Both those are installed:```
$ acpo libxcb-shape0
libxcb-shape0:
  Installed: 1.10-2ubuntu1
  Candidate: 1.10-2ubuntu1
  Version table:
 *** 1.10-2ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
$ acpo libxcb-shm0
libxcb-shm0:
  Installed: 1.10-2ubuntu1
  Candidate: 1.10-2ubuntu1
  Version table:
 *** 1.10-2ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
$ 
```
I'll be moving to 16.04 as well :)

---

### Post by mc4man on 2016-03-26
I'll ck. out tonight, even though the build-deps were supplied for this it appears not to have built support.
So this should be what's returned on command - 
```
ldd /usr/bin/ffmpeg |grep libxcb	
        libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007f93ce7af000)
	libxcb-shm.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0 (0x00007f93ce5aa000)
	libxcb-xfixes.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-xfixes.so.0 (0x00007f93ce3a2000)
	libxcb-shape.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-shape.so.0 (0x00007f93ce19e000)

```
I'll bet you would only see the first one?

---

### Post by vasa1 on 2016-03-26
> **mc4man said:**
> ...
I'll bet you would only see the first one?
Yes!```
$ ldd /usr/bin/ffmpeg |grep libxcb
	libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007f2737938000)
$ 
```But the number, 0x00007f2737938000, is different?

---

### Post by mc4man on 2016-03-26
The number isn't important, anyway will not able to test locally till later,  I  put up a new build, try it.
(- building now, should be published in 1/2 hr. or so.
runing a lld on a testing ppa  build shows - 
```
$ ldd '/home/doug/Downloads/ffmpeg_3.0.0+git1~trusty_amd64/data/opt/ffmpeg/bin/ffmpeg' |grep libxcb
	libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007f926c101000)
	libxcb-shm.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0 (0x00007f926befc000)
	libxcb-xfixes.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-xfixes.so.0 (0x00007f926bcf4000)
	libxcb-shape.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-shape.so.0 (0x00007f926baf0000)

```

---

### Post by vasa1 on 2016-03-26
> **mc4man said:**
> The number isn't important, anyway will not able to test locally till later,  I  put up a new build, try it.
(- building now, should be published in 1/2 hr. or so.
runing a lld on a testing ppa  build shows - 
```
$ ldd '/home/doug/Downloads/ffmpeg_3.0.0+git1~trusty_amd64/data/opt/ffmpeg/bin/ffmpeg' |grep libxcb
	libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007f926c101000)
	libxcb-shm.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0 (0x00007f926befc000)
	libxcb-xfixes.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-xfixes.so.0 (0x00007f926bcf4000)
	libxcb-shape.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-shape.so.0 (0x00007f926baf0000)

```
I should get the update tomorrow then. I'll post back here when I do!

---

### Post by mc4man on 2016-03-26
> **vasa1 said:**
> I should get the update tomorrow then. I'll post back here when I do!
I'll ck. it out tonight on my trusty install. 
If you ever get issues with any of the ppa packages you can email me thru Launchpad. Lately I've been focusing on 16.04 so haven't checked 14.04.x as much as I should.

---

### Post by vasa1 on 2016-03-26
> **mc4man said:**
> ... Lately I've been focusing on 16.04 so haven't checked 14.04.x as much as I should.
That's perfectly understandable and totally appreciated :)

---

### Post by vasa1 on 2016-03-26
```
$ apt-cache policy ffmpeg
ffmpeg:
  Installed: 7:3.0.0+git1~trusty
  Candidate: 7:3.0.0+git1~trusty
  Version table:
 *** 7:3.0.0+git1~trusty 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
$ 
```

Problem solved with this update. Thank you very much!

---

