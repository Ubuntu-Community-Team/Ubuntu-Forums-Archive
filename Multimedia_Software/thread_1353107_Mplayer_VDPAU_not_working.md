---
title: "Mplayer VDPAU not working?"
date: 2009-12-12
forum: Multimedia Software
---

### Post by nicoloks on 2009-12-12
Hi All,

Building a cheap Mythbuntu 9.10 based HTPC for a mate consisting of an Intel Celeron 2.8Ghz CPU, 1GB DDR400 and a Nvidia 8400GS on an old Intel D915GAG mATX motherboard. 

I've compiled mplayer with VDPAU several times before on other machines without issue, however after just checking the latest version of mplayer from SVN, VDPAU is not auto detected when simply running the ./configure script without any arguments. If I try forcing compiling VDPAU support I get several VDPAU errors during the make.

> htpc@htpc:~/mplayer$ make
cc -Wundef -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -Ilibdvdread4 -I.  -D_REENTRANT -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT    -I/usr/include/freetype2 -I/usr/include   -I/usr/include/schroedinger-1.0 -I/usr/include/liboil-0.3     -c -o libvo/vo_vdpau.o libvo/vo_vdpau.c
In file included from libvo/vo_vdpau.c:46:
./libavcodec/vdpau.h:76: error: expected specifier-qualifier-list before 'VdpPictureInfoMPEG4Part2'
libvo/vo_vdpau.c: In function 'create_vdp_mixer':
libvo/vo_vdpau.c:495: error: 'VDP_VIDEO_MIXER_FEATURE_HIGH_QUALITY_SCALING_L1' undeclared (first use in this function)
libvo/vo_vdpau.c:495: error: (Each undeclared identifier is reported only once
libvo/vo_vdpau.c:495: error: for each function it appears in.)
libvo/vo_vdpau.c: In function 'create_vdp_decoder':
libvo/vo_vdpau.c:580: error: 'VDP_DECODER_PROFILE_MPEG4_PART2_ASP' undeclared (first use in this function)
make: *** [libvo/vo_vdpau.o] Error 1
htpc@htpc:~/mplayer$ 

I'm using the Nvidia 185.18.36 drivers that came with Mythbuntu, which should have VDPAU support as I understand. I also ran "apt-get build-dep mplayer" to get all the mplayer dependencies before compiling. Any idea what I am missing here?

---

### Post by s3MA00RRNY on 2009-12-12
```
pcd 13:38:/home/pcdude2143% grep -i vdpau /etc/apt/sources.list
deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu karmic main 

```

---

### Post by andrew.46 on 2009-12-12
Hi nicoloks,

> **nicoloks said:**
> I'm using the Nvidia 185.18.36 drivers that came with Mythbuntu, which should have VDPAU support as I understand.

The svn MPlayer will not build vdpau support with these drivers, you will need to use the latest NVidia drivers.

Andrew

---

### Post by nicoloks on 2009-12-12
Thanks for the replies, but I have to say I am somewhat confused. I thought VDPAU support had been implemented since the 180.x drivers? Do I need a specific revision of mplayer for those drivers? 

The people I'm building this htpc for have not used linux before, and really just want something that works without needing to know what is going on under the hood. I suppose the important question for me is, is there anyway I can get mplayer up and running with VDPAU support without having to install drivers that are not coming out of the official repositories? I don't want things to break when they install their system updates.

---

### Post by andrew.46 on 2009-12-13
Hi nicoloks,

> **nicoloks said:**
> I suppose the important question for me is, is there anyway I can get mplayer up and running with VDPAU support without having to install drivers that are not coming out of the official repositories? I don't want things to break when they install their system updates.

In this case perhaps the repository MPlayer + the older NVidia drivers, also available in the Ubuntu repository, might be best? This will work with Karmic but not older versions...

If you are still keen to use svn, and I have complete agreement with the svn option, the following appears to be the revision that changed the driver requirements:

```

------------------------------------------------------------------------
r29823 | cehoyos | 2009-11-05 02:30:13 +1100 (Thu, 05 Nov 2009) | 2 lines

Add new VDPAU feature high-quality-scaling (and require newer library).

------------------------------------------------------------------------

```


All the best,

Andrew

---

### Post by meatbiscuit on 2009-12-15
Did you ever get this working?  On that note, has anyone successfully compiled Mplayer with VDPAU support under 9.10?  I am receiving the same error.

---

### Post by cor2y on 2009-12-15
Yes i have gotten it to work,
The easiest method is to add the ppa nvidia vdpau driver repo so that mplayer can be compiled with vdpau, the other method is to download the needed bin from nvidia's site and install.
PPA VDPAU Link : [https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

---

### Post by Luke has no name on 2009-12-15
I was looking for just this, and it worked. 1080p on my 9500GT is flawless.

If this build of mplayer (the VDPAU one) is compatible with non-nvidia cards, can we not add this to the repositories? Also, when will nvidia's 190 series drivers be backported to Karmic, if at all?

---

### Post by Linuxforall on 2009-12-15
mplayer vdpau works fine when compiled with andrew's guide and using latest 190.42 drivers.

In case you don't wish to compile this ppa is perfect, it contains the latest nvidia drivers and mplayer along with smplayer front end.

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

---

### Post by meatbiscuit on 2009-12-15
Got it working with the PPA -- thx for the info.

Regarding the 190 drivers, I suggest you download the source install package from nvidia and compile your own.  That route works fine on Karmic.

---

### Post by meatbiscuit on 2009-12-15
Also -- is anyone running 9.10 x86_64?  After ugrading ALSA, something hosed my system and X won't start, just hangs at a blank screen.  SSH also hangs so I can't login remotely.  I was thinking of re-installing 64-bit.  My only two major requirements are really mplayer and xbmc, both accelerated with VDPAU.  Anyone have any intel?

Thanks in advance.

By the way, has anyone else been seeing general instability issues with 9.10?  It seems very volatile.  I have been isntalling it onto some prototype systems at work and it has been very erratic.

---

### Post by frobnitzem on 2010-12-26
I've found that mplayer's pule-audio output works faster than ALSA.

---

