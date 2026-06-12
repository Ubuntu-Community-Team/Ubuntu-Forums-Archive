---
title: "Totem reads wrong size with H.264 codec"
date: 2012-10-19
forum: Multimedia Software
---

### Post by Chogogo on 2012-10-19
Hi!

I am using ubuntu 12.04 and hav all the codecs installed and running properly.

I have som videos with codec H.264 and size 720X480. When I play them under Totem, the size register is 720X720 and  That is the size of the visor, thus the lower part of the visor is filled with a green zone. 

This dosn't happen under VLC, eventhoght the size registered is 720x720 but the size of the visor is the appropiate (720x480)

Videos with other video codec are played right.

Any Idea ?? 

Thanks and God bless you!!

---

### Post by BicyclerBoy on 2012-10-19
From terminal:

```
mediainfo --Inform="Video;Width= %Width% Height= %Height%\rAspect= %DisplayAspectRatio/String%"  thevideofile 

```

If you have to install mediainfo then:
sudo apt-get install mediainfo

(there is a GUI package)

---

### Post by Chogogo on 2012-10-20
> **BicyclerBoy said:**
> From terminal:

```
mediainfo --Inform="Video;Width= %Width% Height= %Height%\rAspect= %DisplayAspectRatio/String%"  thevideofile 

```

If you have to install mediainfo then:
sudo apt-get install mediainfo

(there is a GUI package)

Here is therminal output
:~/Escritorio$ mediainfo --Inform="Video;Width= %Width% Height= %Height%\rAspect= %DisplayAspectRatio/String%" Video1.mov
Width= 720 Height= 480
Aspect= 1.000

Both VLC and Totem inform that video dimensions are 720X720 

VLC Info:
Codec : H264 AVC(part10)
Resolution: 720X720

Totem Info:
Codec:H264/AVC
Dimension: 720X720

A third program (Avidemux) detects 720X480. But the sound is very bad.

Any Idea??

Thanks

---

### Post by Chogogo on 2012-11-03
Hello again!!

Thanks God I found a solution:
[http://www.webupd8.org/2012/06/fix-mp4-playback-in-ubuntu-1204.html](http://www.webupd8.org/2012/06/fix-mp4-playback-in-ubuntu-1204.html)

It was a bug reported in this site:
[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014)

Here it is:

renaming the "libgstvideoparsersbad.so" file:

- 32bit:
sudo mv /usr/lib/i386-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so /usr/lib/i386-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so.bak
- 64bit:
sudo mv /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so.bak

There aren't any visible side effects to using this work-around, but in case you find one, you can simply rename "libgstvideoparsersbad.so.bak" back to "libgstvideoparsersbad.so".

Thanks and may God bless you!

---

### Post by mc4man on 2012-11-03
I provided a proper solution & David Henningsson was good enough to ppa it while a SRU for 12.04/12.10 is considered.
This is the preferred way vs. the mv to bak
[https://launchpad.net/~diwic/+archive/gstreamer-h264-testing](https://launchpad.net/~diwic/+archive/gstreamer-h264-testing)

---

