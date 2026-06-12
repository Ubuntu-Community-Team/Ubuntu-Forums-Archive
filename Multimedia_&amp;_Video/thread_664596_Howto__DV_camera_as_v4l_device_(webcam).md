---
title: "Howto : DV camera as v4l device (webcam)"
date: 2008-01-11
forum: Multimedia &amp; Video
---

### Post by phyre-x on 2008-01-11
Ok i've got a solution working on my gutsy install  now to use my dv camcorder connected on 1394 to work as a webcam, its not pretty but it does work, I've never written a how to or guide but i'll do my best. This is also done using subversion packages so is probably unstable/unlikely to work perfectly however its still worth a go i think.

**this assumes that you've got the camera workin alright in programs such as kino etc first.**

You need a few things to start with so in a terminal do

1:sudo apt-get install libdv-dev libiec61883-dev libraw1394-dev subversion build-essential camorama linux-headers-$(uname -r)

that should be everything (unless i've forgotten things, i wasnt taking notes)(duh)

firstly you need the vloopback module loaded and working properly,

1: download the package from here [http://www.lavrsen.dk/twiki/pub/Motion/VideoFourLinuxLoopbackDevice/vloopback-1.0.tar.gz](http://www.lavrsen.dk/twiki/pub/Motion/VideoFourLinuxLoopbackDevice/vloopback-1.0.tar.gz)
2: untar it
3: in a terminal cd to the directory
4: make
5: sudo -s
6: make install
7: modprobe videodev
8: modprobe vloopback
9: exit

that should be the vloopback module loaded. next is to install the dependencies for dv4linux

Plug in your camera and switch it on (i forgot the first few times)

Now to actually download DV4L

1: cd
2: svn checkout svn://svn.berlios.de/dv4l/trunk
3: cd ./trunk
4: ./configure
5: make
6: sudo make install 

that should be it installed, open a run dialog (press alt + f2 i think) or type in a terminal

1: "dv4l"
2: start camorama from the graphics menu and see if you have anything , it should come up like the screenshots.

good luck - any corretions more than welcome, i just scribbled this down before i forgot.

A huge thanks to the developer of DV4Linux !!  [http://developer.berlios.de/projects/dv4l/](http://developer.berlios.de/projects/dv4l/)

The screenshots are aMSN webcam setup and camorama

---

### Post by bewo02 on 2008-01-19
> **phyre-x said:**
> 


1: cd
2: svn checkout svn://svn.berlios.de/dv4l/trunk


Please download the latest release from **[here](https://developer.berlios.de/project/showfiles.php?group_id=8221)**. While the svn version is more recent, it's not tested to build and run properly.

Since 0.98, vloopback is only required for V4L applications that don't support
the read mode. In 0.99, vloopback will only be required for some exotic cases.

---

### Post by Dyst Mingus on 2008-02-01
Yikes!
does anybody have a clue? I got this trying to make vloopback.

```
houk@black:~/dls/vloopback-1.0$ make
make -C /lib/modules/2.6.20-15-386/build SUBDIRS=/home/houk/dls/vloopback-1.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-386'
  CC [M]  /home/houk/dls/vloopback-1.0/vloopback.o
/home/houk/dls/vloopback-1.0/vloopback.c:136:75: error: linux/config.h: No such file or directory
/home/houk/dls/vloopback-1.0/vloopback.c: In function ‘vloopback_open’:
/home/houk/dls/vloopback-1.0/vloopback.c:313: warning: implicit declaration of function ‘video_devdata’
/home/houk/dls/vloopback-1.0/vloopback.c:313: warning: initialization makes pointer from integer without a cast
/home/houk/dls/vloopback-1.0/vloopback.c:314: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:339: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:339: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c: In function ‘vloopback_release’:
/home/houk/dls/vloopback-1.0/vloopback.c:355: warning: initialization makes pointer from integer without a cast
/home/houk/dls/vloopback-1.0/vloopback.c:356: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c: In function ‘vloopback_write’:
/home/houk/dls/vloopback-1.0/vloopback.c:398: warning: initialization makes pointer from integer without a cast
/home/houk/dls/vloopback-1.0/vloopback.c:399: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c: In function ‘vloopback_read’:
/home/houk/dls/vloopback-1.0/vloopback.c:444: warning: initialization makes pointer from integer without a cast
/home/houk/dls/vloopback-1.0/vloopback.c:445: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c: In function ‘vloopback_mmap’:
/home/houk/dls/vloopback-1.0/vloopback.c:513: warning: initialization makes pointer from integer without a cast
/home/houk/dls/vloopback-1.0/vloopback.c:514: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c: In function ‘vloopback_ioctl’:
/home/houk/dls/vloopback-1.0/vloopback.c:571: warning: initialization makes pointer from integer without a cast
/home/houk/dls/vloopback-1.0/vloopback.c:572: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:852: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:854: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c: In function ‘vloopback_poll’:
/home/houk/dls/vloopback-1.0/vloopback.c:903: warning: initialization makes pointer from integer without a cast
/home/houk/dls/vloopback-1.0/vloopback.c:904: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:914: error: ‘POLLIN’ undeclared (first use in this function)
/home/houk/dls/vloopback-1.0/vloopback.c:914: error: (Each undeclared identifier is reported only once
/home/houk/dls/vloopback-1.0/vloopback.c:914: error: for each function it appears in.)
/home/houk/dls/vloopback-1.0/vloopback.c:914: error: ‘POLLPRI’ undeclared (first use in this function)
/home/houk/dls/vloopback-1.0/vloopback.c:914: error: ‘POLLOUT’ undeclared (first use in this function)
/home/houk/dls/vloopback-1.0/vloopback.c:914: error: ‘POLLRDNORM’ undeclared (first use in this function)
/home/houk/dls/vloopback-1.0/vloopback.c: At top level:
/home/houk/dls/vloopback-1.0/vloopback.c:934: error: variable ‘vloopback_template’ has initializer but incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:936: error: unknown field ‘owner’ specified in initializer
/home/houk/dls/vloopback-1.0/vloopback.c:936: warning: excess elements in struct initializer
/home/houk/dls/vloopback-1.0/vloopback.c:936: warning: (near initialization for ‘vloopback_template’)
/home/houk/dls/vloopback-1.0/vloopback.c:937: error: unknown field ‘name’ specified in initializer
/home/houk/dls/vloopback-1.0/vloopback.c:937: warning: excess elements in struct initializer
/home/houk/dls/vloopback-1.0/vloopback.c:937: warning: (near initialization for ‘vloopback_template’)
/home/houk/dls/vloopback-1.0/vloopback.c:938: error: unknown field ‘type’ specified in initializer
/home/houk/dls/vloopback-1.0/vloopback.c:938: warning: excess elements in struct initializer
/home/houk/dls/vloopback-1.0/vloopback.c:938: warning: (near initialization for ‘vloopback_template’)
/home/houk/dls/vloopback-1.0/vloopback.c:939: error: unknown field ‘fops’ specified in initializer
/home/houk/dls/vloopback-1.0/vloopback.c:939: warning: excess elements in struct initializer
/home/houk/dls/vloopback-1.0/vloopback.c:939: warning: (near initialization for ‘vloopback_template’)
/home/houk/dls/vloopback-1.0/vloopback.c:941: error: unknown field ‘release’ specified in initializer
/home/houk/dls/vloopback-1.0/vloopback.c:941: error: ‘video_device_release’ undeclared here (not in a function)
/home/houk/dls/vloopback-1.0/vloopback.c:941: warning: excess elements in struct initializer
/home/houk/dls/vloopback-1.0/vloopback.c:941: warning: (near initialization for ‘vloopback_template’)
/home/houk/dls/vloopback-1.0/vloopback.c: In function ‘create_pipe’:
/home/houk/dls/vloopback-1.0/vloopback.c:961: warning: implicit declaration of function ‘video_device_alloc’
/home/houk/dls/vloopback-1.0/vloopback.c:961: warning: assignment makes pointer from integer without a cast
/home/houk/dls/vloopback-1.0/vloopback.c:964: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:965: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:967: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:972: warning: assignment makes pointer from integer without a cast
/home/houk/dls/vloopback-1.0/vloopback.c:974: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:978: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:979: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:981: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:982: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:988: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:989: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:1002: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:1003: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:1004: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:1005: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:1006: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:1007: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:1011: warning: implicit declaration of function ‘video_register_device’
/home/houk/dls/vloopback-1.0/vloopback.c:1011: error: ‘VFL_TYPE_GRABBER’ undeclared (first use in this function)
/home/houk/dls/vloopback-1.0/vloopback.c:1014: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:1015: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:1017: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:1027: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:1028: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:1029: warning: implicit declaration of function ‘video_unregister_device’
/home/houk/dls/vloopback-1.0/vloopback.c:1030: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c: In function ‘vloopback_init’:
/home/houk/dls/vloopback-1.0/vloopback.c:1094: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:1094: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c: In function ‘cleanup_vloopback_module’:
/home/houk/dls/vloopback-1.0/vloopback.c:1112: error: dereferencing pointer to incomplete type
/home/houk/dls/vloopback-1.0/vloopback.c:1114: error: dereferencing pointer to incomplete type
make[2]: *** [/home/houk/dls/vloopback-1.0/vloopback.o] Error 1
make[1]: *** [_module_/home/houk/dls/vloopback-1.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-386'
make: *** [all] Error 2

```

ty

---

### Post by bewo02 on 2008-02-04
> **Dyst Mingus said:**
> Yikes!
does anybody have a clue? I got this trying to make vloopback.

```
houk@black:~/dls/vloopback-1.0$ make
make -C /lib/modules/2.6.20-15-386/build SUBDIRS=/home/houk/dls/vloopback-1.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-386'
  CC [M]  /home/houk/dls/vloopback-1.0/vloopback.o
/home/houk/dls/vloopback-1.0/vloopback.c:136:75: error: linux/config.h: No such file or directory


```

ty

If you have kernel >= 2.6.19, you should use **[vloopback-1.1](http://www.lavrsen.dk/twiki/pub/Motion/VideoFourLinuxLoopbackDevice/vloopback-1.1-rc1.tar.gz)**

Or you use the brand new version 0.99 of dv4l, which no longer requires vloopback for most applications (install, man dv4lstart).

---

### Post by Dyst Mingus on 2008-02-05
sho u right

cheers

---

### Post by lvp on 2008-02-05
hi.

DV cam: SONY DCR-PC100
Driver: NVIDIA

```
% v4l-info /dev/video1

### video4linux device info [/dev/video1] ###
general info
    VIDIOCGCAP
        name                    : "DV4Linux dv1394 to V4L"
        type                    : 0x1 [CAPTURE]
        channels                : 1
        audios                  : 0
        maxwidth                : 720
        maxheight               : 480
        minwidth                : 128
        minheight               : 96

channels
    VIDIOCGCHAN(0)
        channel                 : 0
        name                    : "DVCam"
        tuners                  : 0
        flags                   : 0x0 []
        type                    : CAMERA
        norm                    : 3

tuner
ioctl VIDIOCGTUNER: Inappropriate ioctl for device

audio
ioctl VIDIOCGAUDIO: Inappropriate ioctl for device

picture
    VIDIOCGPICT
        brightness              : 32768
        hue                     : 32768
        colour                  : 32768
        contrast                : 32768
        whiteness               : 32768
        depth                   : 24
        palette                 : RGB24

buffer
ioctl VIDIOCGFBUF: Inappropriate ioctl for device

window
    VIDIOCGWIN
        x                       : 0
        y                       : 0
        width                   : 320
        height                  : 240
        chromakey               : 0
        flags                   : 1

```


```
% effectv -device /dev/video1
...
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
v4lsync:VIDIOCSYNC: Inappropriate ioctl for device
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
...

```

any ideas?

---

### Post by bewo02 on 2008-02-06
the v4l-info output looks good.

what dv4l version are you using?
what command line options did you use with dv4l?

can you start dv4l with -v 3 and run effectv again?

---

### Post by lvp on 2008-02-06
effectv version 0.3.10(cli print) 0.3.11(deb print)
dv4l version 0.98 (0.99 interdv4l.c:32:24: error: attr/xattr.h: No such file or directory.)
vloopback version 1.1-rc1
kernel version 2.6.23

```
% dv4l -v3
use /dev/video1 in your webcam application
dv4l.c +757: mmap_mode
dv4l.c +498: w 720 h 480
...
dv4l.c +319: VIDIOCSYNC 1
dv4l.c +339: double VIDIOCSYNC 1
dv4l.c +319: VIDIOCSYNC 1
dv4l.c +339: double VIDIOCSYNC 1
...
... (now stop effectv)
dv4l.c +528: do SYNC 1
dv4l.c +353: unsupported ioctl 0xffffffff
dv4l.c +793: stopped

```

```
% effectv -device /dev/video1
...
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
v4lgrabstart: frame 0 is already used to grab.
v4lgetpicture:VIDIOCGPICT: Inappropriate ioctl for device
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
...
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
v4lgetpicture:VIDIOCGPICT: Inappropriate ioctl for device
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
v4lgrabstart:VIDIOCMCAPTURE: Inappropriate ioctl for device
...

```

```
% lsmod | grep 1394
raw1394                24964  2
ohci1394               29776  1
ieee1394               83964  2 raw1394,ohci1394
% lsmod | grep video
videodev               26400  2 vloopback
v4l2_common            16640  1 videodev
v4l1_compat            12324  1 videodev
video                  18352  14
output                  3776  1 video

```

following commands seems be ok:

[LIST]
[*]% dvgrab
[*]% mplayer tv:// -tv device=/dev/video1:driver=v4l:width=720:height=480 -vo gl2 -fps 24
[*]%vgrabbj -d /dev/video1 -f foo.jpg
[/LIST]

 uhm....

---

### Post by bewo02 on 2008-02-07
[0.99 compile error]
a kind soul has already provided a patch.
[http://developer.berlios.de/patch/?group_id=8221](http://developer.berlios.de/patch/?group_id=8221)
(use the patch, or simply replace #include <attr/xattr.h> with #include <sys/xattr.h> )

I can't reproduce your problem with effectv.
I've just downloaded version 0.3.10 and tried it with dv4l v0.98.
Works here (attached pic shows dv4l+effectv/agingTV)

If you move the camera around, the firewire cable easily
looses contact for a short time. That tends screws things up.
stop app, dv4, and camera; unload/reload vloopback  to be on
the safe side.

Sorry, I'm running out of ideas what could cause your troubles.

---

### Post by theacoustician on 2008-02-07
What's the advantage to using this over dvgrab and piping that to some other program?

Also, why v4l and not ffmpeg or gstreamer?

Just curious, not critizing your work.  

As to the person who's having issues, are you sure the permissions are set properly for the /dev you're using?  I know by default, Ubuntu has broken permissions on /dev/raw1394.  A quick "sudo chmod 777 /dev/raw1934" fixes that for the current session.

---

### Post by lvp on 2008-02-07
Ok. I'll check my environment and try some.
Thanks a lot for your kindness.

---

### Post by lvp on 2008-02-07
I want to stream live video from DV cam to stickam or ustream,tv with video effects.

---

### Post by bewo02 on 2008-02-08
> **theacoustician said:**
> What's the advantage to using this over dvgrab and piping that to some other program?

Also, why v4l and not ffmpeg or gstreamer?


Many applications only support the v4l api, like effectv, camorama, skype,
kopete, amsn, gyachi. They can't just read from a pipe. They need to set
and query some parameters. And the messenger applications require low
latency.

There's a tool named [dv2loopback](https://sourceforge.net/projects/dv2vloopback/) which starts dvgrab, reads its output from a pipe, and
forwards the received frames to vloopback. This has some drawbacks:
the application can't change the picture size, and the system load is higher.

The first (unpublished) versions of dv4l used gstreamer to capture video.
But under load, gstreamer lost memory,  and the required threading model
made dv4l overly complex. The description "poorly documented
overengineered crap" is undeserved, but it came to my mind.

If you simply want to fetch frames from a camcorder. it's better to use
libraw1394/libiec61883/libdv directly,

---

### Post by bewo02 on 2008-02-08
> **lvp said:**
> I want to stream live video from DV cam to stickam or ustream,tv with video effects.

i tried to do this, it works locally, after running
dv4lstart effectv -vloopback /dev/video1 -device /dev/video0
camstream could attach to /dev/video2, and displayed the effectv output
(camorama didn't work). 

ustream.tv: firefox crashes every time the flash plugin is loaded.
stickam.com: vloopback device is not detected, firefox can't be started with dv4lstart 

so, flash plugin compatibility is TODO.

---

### Post by theacoustician on 2008-02-08
> **bewo02 said:**
> Many applications only support the v4l api, like effectv, camorama, skype,
kopete, amsn, gyachi. They can't just read from a pipe. They need to set
and query some parameters. And the messenger applications require low
latency.

There's a tool named [dv2loopback](https://sourceforge.net/projects/dv2vloopback/) which starts dvgrab, reads its output from a pipe, and
forwards the received frames to vloopback. This has some drawbacks:
the application can't change the picture size, and the system load is higher.

The first (unpublished) versions of dv4l used gstreamer to capture video.
But under load, gstreamer lost memory,  and the required threading model
made dv4l overly complex. The description "poorly documented
overengineered crap" is undeserved, but it came to my mind.

If you simply want to fetch frames from a camcorder. it's better to use
libraw1394/libiec61883/libdv directly,
Hmm, very interesting.  Thanks for the answer.  I might have to look further into this.

---

### Post by bewo02 on 2008-02-09
> **bewo02 said:**
> 
stickam.com: vloopback device is not detected, firefox can't be started with dv4lstart 

so, flash plugin compatibility is TODO.

after further investigation, it turned out that
  
  dv4lstart firefox

actually works. You might have to press the zoom button in stickam's
player window. Firefox doesn't work with dv4lstart debugging enabled, though.
vloopback devices are not recognized by the flash player at all.

In conclusion, you can use stickam with a camcorder, but adding effects
with effectv does not work.

---

### Post by lvp on 2008-02-11
I regret that I still can't make use of effectv,

```
% dv4lstart effectv -vloopback /dev/video1 -device /dev/video0
v4lgetmbuf:VIDIOCGMBUF: Success
video_init: mmap interface is not supported by this driver.
Video initialization failed.
```

but,

```

% dv4lstart iceweasel &
```

works! 

and I attainment of live streaming with the use of DV cam.

thanks again.

---

### Post by GravityWell on 2008-02-17
This suddenly quit working for me. 

This was working for me just fine, in VLC. I'd 


sudo modprobe videodev
sudo modprobe vloopback

And then 

sudo dv4l

sudo vlc


And it all worked perfectly.
Now, when I get to the sudo dv4l, the CPU usage spikes at 100% and stays there until i kill the dv4l

This was working as of this past monday. Now, suddenly, I'm screwed. 

I'm using the latest Gutsy Gibbon,  vloopback 1.1 and dv4l .99 (I was using .99, this issue suddenly started, I reload the whole OS I ended up installing 1.0, same issue. Uninstalled 1.0, switched back to .99, no dice. Same exact issue)

---

### Post by bewo02 on 2008-02-18
> And it all worked perfectly.
> Now, when I get to the sudo dv4l, the CPU usage spikes at 100% and stays there until i kill the dv4l

> This was working as of this past monday. Now, suddenly, I'm screwed.

That's strange. What has changed between the last time it worked and now?
A kernel update? Any driver module update? New vlc version? Upgrades of libraw1394, libiec61883?

Can you paste the command line, from File -> Open Capture Device -> Customize ?

Did you try "dv4lstart vlc", using /dev/video0 ?

---

### Post by mr_ed on 2008-02-18
Here's what I get when I try and compile dv4l 1.0.  I'm using 1.1rc1 of vloopback.
```
jeramy@jester:~/Desktop/dv4l-1.0$ make
cc -Wall -O3 -MMD    -c -o normfile.o normfile.c
cc -Wall -O3 -MMD    -c -o palettes.o palettes.c
/usr/include/linux/videodev2.h:482: error: field &#8216;timestamp&#8217; has incomplete type
make: *** [palettes.o] Error 1
jeramy@jester:~/Desktop/dv4l-1.0$
```

I added #include <sys/time.h> to the top of palettes.c, and it now compiles fine.
Now dv4l.c is failing.

---

### Post by bewo02 on 2008-02-18
> **mr_ed said:**
> Here's what I get when I try and compile dv4l 1.0.  I'm using 1.1rc1 of vloopback.
```
jeramy@jester:~/Desktop/dv4l-1.0$ make
cc -Wall -O3 -MMD    -c -o normfile.o normfile.c
cc -Wall -O3 -MMD    -c -o palettes.o palettes.c
/usr/include/linux/videodev2.h:482: error: field ‘timestamp’ has incomplete type
make: *** [palettes.o] Error 1
jeramy@jester:~/Desktop/dv4l-1.0$
```

I added #include <sys/time.h> to the top of palettes.c, and it now compiles fine.
Now dv4l.c is failing.

If you google for "videodev2.h sys/time.h" you'll see that linux distributions have real trouble to get that sys/time.h vs linux/time.h user space/kernel space issue right. As that problem does not occur with my Gentoo, it's hard to make a fix that doesn't break things.

---

### Post by mr_ed on 2008-02-18
Did it stop working for everyone?  Was there a gcc or kernel update or something?  Did I miss a parameter in configure?  It appears that my whole /usr/include seems to be messed up or something.  I was hunting around looking to see where that was symlinked, but it doesn't appear to be at all... so I was wondering where /usr/include/linux even came from. :confused:

When I try to build it, I get a whole slough of errors.

I'm using gcc 4.1.3, my kernel is 2.6.22-14-generic

```

jeramy@jester:~/Desktop/dv/dv4l-1.0$ make
cc -Wall -O3 -MMD    -c -o dv4l.o dv4l.c
dv4l.c:75: error: conflicting declaration &#8216;typedef enum mode_t mode_t&#8217;
/usr/include/sys/mman.h:38: error: &#8216;mode_t&#8217; has a previous declaration as &#8216;typedef __mode_t mode_t&#8217;
dv4l.c: In function &#8216;void init_ctx(vid_context_t*, int, int)&#8217;:
dv4l.c:169: warning: comparison between signed and unsigned integer expressions
dv4l.c:170: warning: comparison between signed and unsigned integer expressions
dv4l.c: In function &#8216;unsigned char* init_vmbuf(vid_context_t*, int)&#8217;:
dv4l.c:195: error: invalid conversion from &#8216;void*&#8217; to &#8216;unsigned char*&#8217;
dv4l.c: In function &#8216;int do_ioctl(int, long unsigned int, const char*, vid_context_t*)&#8217;:
dv4l.c:246: error: &#8216;__invalid_size_argument_for_IOC&#8217; cannot appear in a constant-expression
dv4l.c:250: error: &#8216;__invalid_size_argument_for_IOC&#8217; cannot appear in a constant-expression
dv4l.c:254: error: &#8216;__invalid_size_argument_for_IOC&#8217; cannot appear in a constant-expression
dv4l.c:258: error: &#8216;__invalid_size_argument_for_IOC&#8217; cannot appear in a constant-expression
dv4l.c:262: error: &#8216;__invalid_size_argument_for_IOC&#8217; cannot appear in a constant-expression
dv4l.c:266: error: &#8216;__invalid_size_argument_for_IOC&#8217; cannot appear in a constant-expression
dv4l.c:270: error: &#8216;__invalid_size_argument_for_IOC&#8217; cannot appear in a constant-expression
dv4l.c:282: error: &#8216;__invalid_size_argument_for_IOC&#8217; cannot appear in a constant-expression
dv4l.c:305: error: &#8216;__invalid_size_argument_for_IOC&#8217; cannot appear in a constant-expression
dv4l.c:318: error: &#8216;__invalid_size_argument_for_IOC&#8217; cannot appear in a constant-expression
dv4l.c: In function &#8216;int frame_process(fcb_arg_t*, const unsigned char*, unsigned char*)&#8217;:
dv4l.c:452: error: invalid conversion from &#8216;void*&#8217; to &#8216;unsigned char*&#8217;
dv4l.c: In function &#8216;int frame_recv(unsigned char*, int, int, void*)&#8217;:
dv4l.c:500: error: invalid conversion from &#8216;void*&#8217; to &#8216;uint8_t*&#8217;
dv4l.c:501: error: invalid conversion from &#8216;void*&#8217; to &#8216;unsigned char*&#8217;
dv4l.c: In function &#8216;void write_mode(raw1394_handle*, fcb_arg_t*, int, int)&#8217;:
dv4l.c:853: error: invalid conversion from &#8216;void*&#8217; to &#8216;unsigned char*&#8217;
dv4l.c:858: error: invalid conversion from &#8216;void*&#8217; to &#8216;unsigned char*&#8217;
make: *** [dv4l.o] Error 1


```

---

### Post by bewo02 on 2008-02-19
> **mr_ed said:**
> 

When I try to build it, I get a whole slough of errors.

I'm using gcc 4.1.3, my kernel is 2.6.22-14-generic



Try gcc 4.1.2

I don't quite understand what Ubuntu is shipping as gcc 4.1.3.
gcc.gnu.org has released gcc 4.1.2 and 4.2.0, but never a gcc 4.1.3.

Most of the error messages make no sense. If gcc "4.1.3" is that picky,
it won't be able to compile many C programs.

I am using gcc 4.1.2, with all warnings enabled, and dv4l compiles without
warning here.

---

### Post by mr_ed on 2008-02-20
Ok, I'll try installing gcc 4.1.2 later on tonight.

---

### Post by GravityWell on 2008-02-20
> **bewo02 said:**
> > And it all worked perfectly.
> Now, when I get to the sudo dv4l, the CPU usage spikes at 100% and stays there until i kill the dv4l

> This was working as of this past monday. Now, suddenly, I'm screwed.

That's strange. What has changed between the last time it worked and now?
A kernel update? Any driver module update? New vlc version? Upgrades of libraw1394, libiec61883?

Can you paste the command line, from File -> Open Capture Device -> Customize ?

Did you try "dv4lstart vlc", using /dev/video0 ?


I'd paste the code, but the 100% utilization thing happens the moment I hit enter on "sudo dv4l"



I tried doing the sudo dv4lstart VLC but I get an error on load...which I totally forgot to write down because I'm an idiot.




On compiling:

I too had to add the /sys/time.h line to my palettes.c file for this to compile, if that's relevant.
Also on a previous version I had to add the #include </usr/include/sys/xattr.h> bit into one of the files.

---

### Post by mr_ed on 2008-02-21
I get the same warnings and errors on every gcc/g++ version I've tried.  3.4.6, 4.1.3 pre, and 4.2.1.

:(

---

### Post by bewo02 on 2008-02-23
> **GravityWell said:**
> I'd paste the code, but the 100% utilization thing happens the moment I hit enter on "sudo dv4l"



I tried doing the sudo dv4lstart VLC but I get an error on load...which I totally forgot to write down because I'm an idiot.




On compiling:

I too had to add the /sys/time.h line to my palettes.c file for this to compile, if that's relevant.
Also on a previous version I had to add the #include </usr/include/sys/xattr.h> bit into one of the files.

Well, there must be something that has changed. Do other firewire video applications
work, like kino or the gst-launch pipe (see dv4l man page) work?

Did you check the cable (yes, sounds stupid, but I once started debugging only
to find out that by moving the camera around, the cable came loose).

---

### Post by bewo02 on 2008-02-23
> **mr_ed said:**
> I get the same warnings and errors on every gcc/g++ version I've tried.  3.4.6, 4.1.3 pre, and 4.2.1.

:(
can you compile any other v4l program from source?

---

### Post by bewo02 on 2008-02-24
> **mr_ed said:**
> I get the same warnings and errors on every gcc/g++ version I've tried.  3.4.6, 4.1.3 pre, and 4.2.1.

:(

yet another idea, can you add the line

CC=gcc

at the beginning of the Makefile (don't run ./configure again, as it will
overwrite the line you added).

My suspicion is that there is a non-gnu c compiler on your machine.
On linux machines cc was usually gcc, but with intel cc and llvm clang
this might not always be the case. can you give me the output of
cc --version ?

---

### Post by dlstyley on 2008-02-27
First, thanks for this great tool.  It has gotten me much closer to using my DV camera as a web cam.  

The problem is that I can't get Flash Player to recognize my camera.  I can see the video properly in effectv and VLC on video1, but when I look at Flash settings, it always says "cannot find camera".

I've tried launching firefox with dv4lstart - same result.

I think I'm missing something really simple at this point (surely all the hard stuff is behind me:)

Any hints would be greatly appreciated.

---

### Post by dlstyley on 2008-02-27
Not sure what changed, but now the Flash Player settings shows a drop down to select a video device, but the list is empty.  

update:  I'm getting the following errors when trying to use dv4lstart to launch Firefox:

"ERROR: ld.so: object '/libdv4l.so' from LD_PRELOAD cannot be preloaded: ignored."

---

### Post by bewo02 on 2008-02-27
> **dlstyley said:**
> 
"ERROR: ld.so: object '/libdv4l.so' from LD_PRELOAD cannot be preloaded: ignored."

This looks fishy. Go to the dv4l source directory, retry a 'make clean && ./configure && 
make', followed by 'make install' as root. 

dv4lstart is a generated shell script, which sets the variable LD_PRELOAD to
libdv4l.so. For some unknown reason, it uses the wrong path /libdv4l.so
instead of something like /usr/local/lib/libdv4l.so. Do you recall how you
compiled the software in the first place? 

If re-installing doesn't help, you can edit dv4lstart by hand and set LD_PRELOAD
to the location of libdv4l.so

---

### Post by dlstyley on 2008-02-27
Thanks!  Your suggestion got me past the LD_PRELOAD problem (not sure what I did wrong, but I suspect I forgot to run make install as root. )

Next problem - when I run this:

dv4lstart firefox

I get this:

sh: dv.c:379: iec61883_dv_fb_stop: Assertion `fb != ((void *)0)' failed.


Firefox still launches, but when I try to use Yahoo!Live, all sorts of errors start popping up on the console and firefox never actually loads the flash player on the page.

---

### Post by bewo02 on 2008-02-28
> **dlstyley said:**
> Thanks!  Your suggestion got me past the LD_PRELOAD problem (not sure what I did wrong, but I suspect I forgot to run make install as root. )

Next problem - when I run this:

dv4lstart firefox

I get this:

sh: dv.c:379: iec61883_dv_fb_stop: Assertion `fb != ((void *)0)' failed.


Firefox still launches, but when I try to use Yahoo!Live, all sorts of errors start popping up on the console and firefox never actually loads the flash player on the page.

This is an error message of an underlying library. It's not critical.
I have Shockwave Flash 9.0 r115, Firefox 2.0.0.12, dv4linux 1.0.
YAhoo live works without any issues.

---

### Post by aperomsik on 2008-03-02
Anybody have this working with skype? I have camorama working and skype detects the device but it doesn't actually show video.

---

### Post by z0mbie on 2008-03-08
If you get the timestamp error.

Add the header "**#include <sys/time.h>**" to the top of the following 2 files:

**1. palettes.c ** (located in the *trunk* folder)
**2. /usr/include/linux/videodev2.h**

Just add it right after the other #include headers. Now you can compile with make. It worked for me on aMSN. Will try other applications. 

Thanks for writing this tutorial.

---

### Post by Plasma_NZ on 2008-03-11
Ok 

I'm running Hardy heron 64...

I can get my dv1394 cam running in kino is i do 

sudo kino - otherwise is doesnt see it..

I tried following the direction on first page... heres the following errors.. from vloopback make etc..

Only choosing this method because none of my actual webcams work at all ...

Please help..! dont wanna use windows for video/voice 

```
make -C /lib/modules/2.6.24-12-generic/build SUBDIRS=/home/physics/Downloads/vloopback-1.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-12-generic'
  CC [M]  /home/physics/Downloads/vloopback-1.0/vloopback.o
/home/physics/Downloads/vloopback-1.0/vloopback.c:136:75: error: linux/config.h: No such file or directory
/home/physics/Downloads/vloopback-1.0/vloopback.c: In function ‘vloopback_open’:
/home/physics/Downloads/vloopback-1.0/vloopback.c:313: error: implicit declaration of function ‘video_devdata’
/home/physics/Downloads/vloopback-1.0/vloopback.c:313: warning: initialization makes pointer from integer without a cast
/home/physics/Downloads/vloopback-1.0/vloopback.c:314: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:339: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:339: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c: In function ‘vloopback_release’:
/home/physics/Downloads/vloopback-1.0/vloopback.c:355: warning: initialization makes pointer from integer without a cast
/home/physics/Downloads/vloopback-1.0/vloopback.c:356: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c: In function ‘vloopback_write’:
/home/physics/Downloads/vloopback-1.0/vloopback.c:398: warning: initialization makes pointer from integer without a cast
/home/physics/Downloads/vloopback-1.0/vloopback.c:399: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c: In function ‘vloopback_read’:
/home/physics/Downloads/vloopback-1.0/vloopback.c:444: warning: initialization makes pointer from integer without a cast
/home/physics/Downloads/vloopback-1.0/vloopback.c:445: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c: In function ‘vloopback_mmap’:
/home/physics/Downloads/vloopback-1.0/vloopback.c:513: warning: initialization makes pointer from integer without a cast
/home/physics/Downloads/vloopback-1.0/vloopback.c:514: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c: In function ‘vloopback_ioctl’:
/home/physics/Downloads/vloopback-1.0/vloopback.c:571: warning: initialization makes pointer from integer without a cast
/home/physics/Downloads/vloopback-1.0/vloopback.c:572: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:852: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:854: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c: In function ‘vloopback_poll’:
/home/physics/Downloads/vloopback-1.0/vloopback.c:903: warning: initialization makes pointer from integer without a cast
/home/physics/Downloads/vloopback-1.0/vloopback.c:904: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:914: error: ‘POLLIN’ undeclared (first use in this function)
/home/physics/Downloads/vloopback-1.0/vloopback.c:914: error: (Each undeclared identifier is reported only once
/home/physics/Downloads/vloopback-1.0/vloopback.c:914: error: for each function it appears in.)
/home/physics/Downloads/vloopback-1.0/vloopback.c:914: error: ‘POLLPRI’ undeclared (first use in this function)
/home/physics/Downloads/vloopback-1.0/vloopback.c:914: error: ‘POLLOUT’ undeclared (first use in this function)
/home/physics/Downloads/vloopback-1.0/vloopback.c:914: error: ‘POLLRDNORM’ undeclared (first use in this function)
/home/physics/Downloads/vloopback-1.0/vloopback.c: At top level:
/home/physics/Downloads/vloopback-1.0/vloopback.c:934: error: variable ‘vloopback_template’ has initializer but incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:936: error: unknown field ‘owner’ specified in initializer
/home/physics/Downloads/vloopback-1.0/vloopback.c:936: warning: excess elements in struct initializer
/home/physics/Downloads/vloopback-1.0/vloopback.c:936: warning: (near initialization for ‘vloopback_template’)
/home/physics/Downloads/vloopback-1.0/vloopback.c:937: error: unknown field ‘name’ specified in initializer
/home/physics/Downloads/vloopback-1.0/vloopback.c:937: warning: excess elements in struct initializer
/home/physics/Downloads/vloopback-1.0/vloopback.c:937: warning: (near initialization for ‘vloopback_template’)
/home/physics/Downloads/vloopback-1.0/vloopback.c:938: error: unknown field ‘type’ specified in initializer
/home/physics/Downloads/vloopback-1.0/vloopback.c:938: warning: excess elements in struct initializer
/home/physics/Downloads/vloopback-1.0/vloopback.c:938: warning: (near initialization for ‘vloopback_template’)
/home/physics/Downloads/vloopback-1.0/vloopback.c:939: error: unknown field ‘fops’ specified in initializer
/home/physics/Downloads/vloopback-1.0/vloopback.c:939: warning: excess elements in struct initializer
/home/physics/Downloads/vloopback-1.0/vloopback.c:939: warning: (near initialization for ‘vloopback_template’)
/home/physics/Downloads/vloopback-1.0/vloopback.c:941: error: unknown field ‘release’ specified in initializer
/home/physics/Downloads/vloopback-1.0/vloopback.c:941: error: ‘video_device_release’ undeclared here (not in a function)
/home/physics/Downloads/vloopback-1.0/vloopback.c:941: warning: excess elements in struct initializer
/home/physics/Downloads/vloopback-1.0/vloopback.c:941: warning: (near initialization for ‘vloopback_template’)
/home/physics/Downloads/vloopback-1.0/vloopback.c: In function ‘create_pipe’:
/home/physics/Downloads/vloopback-1.0/vloopback.c:961: error: implicit declaration of function ‘video_device_alloc’
/home/physics/Downloads/vloopback-1.0/vloopback.c:961: warning: assignment makes pointer from integer without a cast
/home/physics/Downloads/vloopback-1.0/vloopback.c:964: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:965: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:967: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:972: warning: assignment makes pointer from integer without a cast
/home/physics/Downloads/vloopback-1.0/vloopback.c:974: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:978: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:979: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:981: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:982: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:988: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:989: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:1002: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:1003: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:1004: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:1005: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:1006: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:1007: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:1011: error: implicit declaration of function ‘video_register_device’
/home/physics/Downloads/vloopback-1.0/vloopback.c:1011: error: ‘VFL_TYPE_GRABBER’ undeclared (first use in this function)
/home/physics/Downloads/vloopback-1.0/vloopback.c:1014: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:1015: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:1017: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:1027: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:1028: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:1029: error: implicit declaration of function ‘video_unregister_device’
/home/physics/Downloads/vloopback-1.0/vloopback.c:1030: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c: In function ‘vloopback_init’:
/home/physics/Downloads/vloopback-1.0/vloopback.c:1094: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:1094: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c: In function ‘cleanup_vloopback_module’:
/home/physics/Downloads/vloopback-1.0/vloopback.c:1112: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c:1114: error: dereferencing pointer to incomplete type
/home/physics/Downloads/vloopback-1.0/vloopback.c: At top level:
/home/physics/Downloads/vloopback-1.0/vloopback.c:1124: fatal error: opening dependency file /home/physics/Downloads/vloopback-1.0/.vloopback.o.d: Permission denied
compilation terminated.
make[2]: *** [/home/physics/Downloads/vloopback-1.0/vloopback.o] Error 1
make[1]: *** [_module_/home/physics/Downloads/vloopback-1.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-12-generic'
make: *** [all] Error 2

```

---

### Post by Plasma_NZ on 2008-03-12
Never mind, got it working.. thns for the help... :(

---

### Post by dunno on 2008-03-19
Hey Y'all,
great posts, thanks everyone.  i'm hoping to get this to work with skype and on my website.

I've gone through pretty much every issue listed so far and need a bit more help. these are the issues I had and how they were fixed.  hopefully this addendum will help someone else:

the first problem i had was my main user didn't have permissions on the /dev/raw1394 block.  rather then change the permissions, i added my main user to the video and disk groups in /etc/group: i think this is safer than opening /dev/raw1394 up to everyone and cleaner than running kino as root with gksudo.  after this kino could access the device and worked with my main user.

then I had the crazy ./configure error as in post #2.  I saw that the script was trying to use gcc-4.0: I don't have a gcc-4.0 so I aliased gcc-4.0 to gcc-4.1.  ./configure worked

next problem: dv4l and vloopback didn't compile raising the #include <sys/time.h> error.
I was able get dv4l and vloopback to compile and install using z0mbie's post: thanks for that... u :guitar:

then camorama couldn't find my device on /dev/video0.  well the device was on /dev/video1, so i added the -d /dev/video1 commandline option to the menu item.

now camorama finds the device and can apparently capture 1 image, but then raises the error "unable to capture image".  so that's my current issue.  any ideas on that one?

grazie i ciao

---

### Post by Plasma_NZ on 2008-03-19
ok..

i had to restart pc... bugga dv4l doesnt wish to work anymore...

I do 

```
sudo modprobe vloopback
sudo modprobe dv4l
```

i get the following error

```
FATAL: Module dv4l not found.

```

So i do a 

```
./configure
make
sudo make install
```

and i still get the above fatal error..

```
 dv4l
use /dev/video1 in your webcam application
raw1394_new_handle failed
```

---

### Post by Lokine on 2008-03-24
I got everything working but when I do camorama -d /dev/video1 I get the error "Unable to capture image." My camera is on and connected and working because it comes up fine in Kino. Any way to resolve this?

---

### Post by bewo02 on 2008-03-25
```
sudo modprobe dv4l
FATAL: Module dv4l not found.
```
dv4l is not a kernel module. dv4l needs the vloopback kernel module and
a working firewire configuration. 

```

 dv4l
use /dev/video1 in your webcam application
raw1394_new_handle failed

```
looks as if you don't have firewire support in your kernel
try
```

sudo modprobe raw1394
sudo modprobe dv1394

```

---

### Post by bewo02 on 2008-03-25
> **Lokine said:**
> I got everything working but when I do camorama -d /dev/video1 I get the error "Unable to capture image." My camera is on and connected and working because it comes up fine in Kino. Any way to resolve this?

can you start dv4l with some debugging enabled?
```
dv4l -v 2
```

---

### Post by Lokine on 2008-03-28
Here's the output of dv4l debug (-v 3):
```
dv4l.c +320: VIDIOCSYNC 0
dv4l.c +340: double VIDIOCSYNC 0
dv4l.c +529: do SYNC 0
dv4l.c +354: unsupported ioctl 0xffffffff
dv4l.c +313: VIDIOCMCAPTURE ioctl 0
dv4l.c +793: stopped

```

dv4l -v 2:
```
dv4l -v 2
use /dev/video1 in your webcam application
dv4l.c +757: mmap_mode
dv4l.c +247: VIDIOCGCAP
dv4l.c +267: VIDIOCGWIN
dv4l.c +284: VIDIOCSWIN 360x240
dv4l.c +267: VIDIOCGWIN
dv4l.c +259: VIDIOCGPICT
dv4l.c +263: VIDIOCGMBUF
dv4l.c +272: VIDIOCSPICT depth 24 palette 4
dv4l.c +272: VIDIOCSPICT depth 24 palette 4
dv4l.c +272: VIDIOCSPICT depth 24 palette 4
dv4l.c +272: VIDIOCSPICT depth 24 palette 4
dv4l.c +272: VIDIOCSPICT depth 24 palette 4
dv4l.c +354: unsupported ioctl 0xffffffff
dv4l.c +793: stopped

```

And camorama debug:
```
camorama -Dd /dev/video1

VIDIOCGCAP
device name = DV4Linux dv1394 to V4L
device type = 1
can use mmap()
# of channels = 1
# of audio devices = 0
max width = 720
max height = 480
min width = 128
min height = 96

VIDIOCGWIN
x = 0
y = 0
width = 360
height = 240
chromakey = 0
flags = 0

VIDIOCGWIN
x = 0
y = 0
width = 360
height = 240
chromakey = 0
flags = 0

VIDIOCGPICT:
bright = 32768
hue = 32768
colour = 32768
contrast = 32768
whiteness = 32768
colour depth = 24
24bit RGB

VIDIOCGMBUF
mb.size = 9953280
mb.frames = 2
mb.offset = 4976640
update_tooltip called
tip - acap off
** Message: SET PIC
** Message: SET PIC
** Message: SET PIC
** Message: SET PIC
** Message: SET PIC
update_tooltip called
tip - acap off
Unable to capture image (VIDIOCMCAPTURE)
```

---

### Post by Lokine on 2008-03-29
Any ideas?

---

### Post by Noiano on 2008-03-30
> **Lokine said:**
> Any ideas?

try chmod 777 /dev/raw1394....worked for me....

I still cannot have skype working: i only see a black screen when clicking on "test webcam". If I use dv4lstart skype doesn't detect any webcams...:confused:

---

### Post by Lokine on 2008-03-30
> **Noiano said:**
> try chmod 777 /dev/raw1394....worked for me....
No, that's not the problem... Camorama still says "Unable to capture image" even though it can get at least one frame.

---

### Post by lwhitmore on 2008-05-06
I'm trying to use my digital camcorder as a webcam with processing ([http://processing.org](http://processing.org)), under Hardy.

I'm stuck, and not really sure how to progress, so I thought I'd spell out my experience so far.

** Processing need the v4l device to be '/dev/video0' **

I've tried using dv4l in two different ways;

1. via 'dv4lstart'
2. via 'dv4l' + 'vloopback'

Method 1;
---------

	```
run 'dv4lstart ./processing' 
```

I'm assuming dv4lstart will create a v4l device at '/dev/video0'; and then load processing, allowing it to make use of the new device... but, I get an error when I run the command..

```
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGBUS (0x7) at pc=0xb78b0b0a, pid=15828, tid=3084363440
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_12-b04 mixed mode, sharing)
# Problematic frame:
# V  [libjvm.so+0x313b0a]
#
# An error report file with more information is saved as hs_err_pid15828.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
```

.. so I've had to abandon this idea.  I've successfully managed to load other programs (vlc and camorama) using dv4lstart... so the problem is something specific to processing and/or java.


Method 2;
---------

i)	```
sudo modprobe vloopback dev_offset=1
```
	This will create two devices at /dev/video1 and /dev/video2 (crucially, leaving '/dev/video0' unused). 

ii)	```
dv4l
```
	This is just the same as before .. only now the v4l device will be '/dev/video2'.  
	I assumed that I would then be able to finish off the *******, with a symbolic link;

iii)	```
sudo ln -s /dev/video2 /dev/video0
```

I've tried loading camorama to check the new setup (camorama looks to '/dev/video0' by default); the video appears for a few seconds then drops out... with the error 'unable to capture image'.

Is the connection failing because of the symbolic link?  Is there another way to achieve the same?

If anyone has any ideas, I'd be really grateful.

Cheers

---

### Post by dunno on 2008-05-08
> **Lokine said:**
> No, that's not the problem... Camorama still says "Unable to capture image" even though it can get at least one frame.

So after couple months of not messing with this, I'm fiddling again.

by using "dv4lstart camorama -d /dev/video1" at the command line, all is working.

by using "dv4lstart effectv [any of the options from --help]" at the command line, all is working.

by using "dv4lstart skype" at the command line, all is working.

thanks everyone:guitar::lolflag::KS

---

### Post by DaeronTinúviel on 2008-05-18
can anyone help?

when trying to install dv4l i get this error:

lordtinuviel@praetorian:~$ cd Desktop
lordtinuviel@praetorian:~/Desktop$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
lordtinuviel@praetorian:~/Desktop$

any ideas????

---

### Post by dunno on 2008-05-18
> **DaeronTinúviel said:**
> 
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.


Do you have the proper compiler version?  there are some posts earlier in this thread that will help find the proper compiler version.
  
lordtinuviel@praetorian:~$ gcc -v

Does your user have permissions to create executables in that directory?

Does 'config.log' give any more details?

---

### Post by DaeronTinúviel on 2008-05-18
hey thkz! i manage to make it work!! i was missing some dependencies, shame it wont work on skype....I was missing gcc++, libdv-dev

---

### Post by DaeronTinúviel on 2008-05-18
ok, if I open amsn and go to the video device I can see myself but I get a message that said: can not capture video from this device

I try to a wecam conversation and the other end can see me, any ideas???

if I go to terminal and type: dv4l I get:

lordtinuviel@praetorian:~$ dv4l
no vloopback input device found. vloopback module in kernel?

---

### Post by dunno on 2008-05-18
> **DaeronTinúviel said:**
> hey thkz! i manage to make it work!! i was missing some dependencies,

Glad you were able to get it to compile.

> **DaeronTinúviel said:**
> shame it wont work on skype....I was missing gcc++, libdv-dev
...and why won't it work with skype?  mine does.

> **DaeronTinúviel said:**
> lordtinuviel@praetorian:~$ dv4l
no vloopback input device found. vloopback module in kernel?
try: dv4lstart <your program bin here> <any options here>
por ejemplo:
dv4lstart camorama -d /dev/video1
dv4lstart firefox (to get your msn working, see earlier post)
dv4lstart skype

---

### Post by DaeronTinúviel on 2008-05-18
ok

skype works

camorama works

amsn gave me error when i start the webcam session:

lordtinuviel@praetorian:~$ dv4lstart amsn
ioctl: VIDIOCGFBUF(base=(nil);height=0;width=0;depth=0;bytesperline=0): Invalid argument
ioctl: VIDIOCGFBUF(base=(nil);height=0;width=0;depth=0;bytesperline=0): Invalid argument
ioctl: VIDIOCGFBUF(base=(nil);height=0;width=0;depth=0;bytesperline=0): Invalid argument
ioctl: VIDIOCGFBUF(base=(nil);height=0;width=0;depth=0;bytesperline=0): Invalid argument


GRACIAS!!!!

one question can I close the terminal window once I start the webcam?

---

### Post by GISLUser on 2008-06-20
Ubuntu Hardy 2.6.24-19-server
cc (GCC) 4.2.3
vloopback 1.1

Can anyone assist?

I got the following error with make for vloopback:

make -C /lib/modules/2.6.24-19-server/build SUBDIRS=/home/gisluser/vloopback modules
make: *** /lib/modules/2.6.24-19-server/build: No such file or directory.  Stop.
make: *** [all] Error 2
:confused:

---

### Post by GISLUser on 2008-06-20
Found solution to my make vloopback error.

Did not get the headers when I executed 
sudo apt-get install libdv-dev libiec61883-dev libraw1394-dev subversion build-essential camorama linux-headers-$(uname -r)

Will be doing testing and report further.

---

### Post by secludedsfx on 2008-06-20
Hmm... lets say i'm having a bit of trouble... managed to sort the installation out and all that fine but now it comes to using camorama its comes up with a message saying "could not connect to video device (/dev/video0) please check connection."

I've tried quite a few things like checking the cable, checking if my camcorder was switched on.
What else could work?

---

### Post by kruthers on 2008-06-22
I've followed the whole discussion but seem to have a different sort of problem; I run dv4l and when I try to run camorama it fails.  Look at the crazy window size in the output:

$ dv4l -v 2
use /dev/video1 in your webcam application
dv4l.c +757: mmap_mode
dv4l.c +247: VIDIOCGCAP
dv4l.c +267: VIDIOCGWIN
dv4l.c +284: VIDIOCSWIN -604212128x-604212912
dv4l.c +293: VIDIOCSWIN invalid size
dv4l.c +793: stopped

Any ideas?  I've also tried the dv4lstart <program> method and can't get anywhere (it seems the /dev/video0 device doesn't get created or immediately disappears or something...)   Yes, the camera works in kino.  Thanks for any info...

-sk

---

### Post by GISLUser on 2008-06-27
secludedsfx:

dv4lstart camorama -d /dev/*video1*

should work.

Please note *video1* is to be replaced by the *videox* generated by dv4l.

For example if you get the message: 
   use /dev/video2 in your webcam application

then the command will be:
   dv4lstart camorama -d /dev/video2

Hope everything goes well.

---

### Post by Plasma_NZ on 2008-06-30
Ok 2 problems.. kino can see the cam fine...

First one - camorama cant... as follows

```
dv4lstart camorama -d /dev/video1 
using read()

(camorama:28848): Gdk-CRITICAL **: gdk_pixmap_new: assertion `(width != 0) && (height != 0)' failed

(camorama:28848): Gdk-CRITICAL **: gdk_gc_new: assertion `drawable != NULL' failed

(camorama:28848): Gdk-CRITICAL **: gdk_drawable_get_colormap: assertion `GDK_IS_DRAWABLE (drawable)' failed

(camorama:28848): Gdk-CRITICAL **: gdk_drawable_get_screen: assertion `GDK_IS_DRAWABLE (drawable)' failed

(camorama:28848): Gdk-CRITICAL **: gdk_drawable_get_depth: assertion `GDK_IS_DRAWABLE (drawable)' failed

(camorama:28848): Gdk-CRITICAL **: gdk_screen_get_rgb_colormap: assertion `GDK_IS_SCREEN (screen)' failed

(camorama:28848): Gdk-CRITICAL **: gdk_colormap_get_visual: assertion `GDK_IS_COLORMAP (colormap)' failed
Segmentation fault

```

Second is skype - cant see it either

```
 Home@home:~$dv4lstart skype 
ERROR: ld.so: object '/usr/local/lib/libdv4l.so' from LD_PRELOAD cannot be preloaded: ignored.

```

any ideas..? prefer to have it working in Skype, that way i dont have to fork-out for a new webcam..

I also tried the previous post of going to dv4l src folder, and doing "make clean && ./configure && make" followed by "sudo make install" still get the same issues..

video0 is my webcam, video1 is nothing, video2 is ment to be the dvcam according to dv4l

sudo dv4lstart camorama works and it's using video0 - wont work with video 2

But im tryin to get it to run with skype.. and it's still doing the preload issue, despite it being where it should be as u can see..

---

### Post by Plasma_NZ on 2008-06-30
Ok here's where im at..

sudo dv4lstart camorama - works

dv4lstart vlc - works

xawtv - works

dv4lstart amsn - works

dv4lstart skype - doesnt.. error as follows..

```
ERROR: ld.so: object '/usr/local/lib/libdv4l.so' from LD_PRELOAD cannot be preloaded: ignored.
```

Tried it with sudo dv4lstart skype - same thing..

Have uninstalled dv4l - reinstalled etc.. the path to libdv4l is correct..

I am aware that skype doesnt support rgb - could this be the problem.?

stumped..

---

### Post by wellynz on 2008-07-02
> **Plasma_NZ said:**
> 
dv4lstart skype - doesnt.. error as follows..

```
ERROR: ld.so: object '/usr/local/lib/libdv4l.so' from LD_PRELOAD cannot be preloaded: ignored.
```

Tried it with sudo dv4lstart skype - same thing..

Have uninstalled dv4l - reinstalled etc.. the path to libdv4l is correct..

I am aware that skype doesnt support rgb - could this be the problem.?

stumped..

I had the same problem but figured that because I am using a 32-bit version of Skype on Hardy 64-bit that maybe I should compile a 32-bit version of the library.

I'm sure there are easier ways but I ended up installing Hardy 32-bit in Virtualbox, compiling on that and then copying the libraries over to my 64-bit install (into /lib32/). I amended the location of the main library in the dv4lstart script and all worked a treat!

HTH

Welly

---

### Post by Plasma_NZ on 2008-07-02
> **wellynz said:**
> I had the same problem but figured that because I am using a 32-bit version of Skype on Hardy 64-bit that maybe I should compile a 32-bit version of the library.

I'm sure there are easier ways but I ended up installing Hardy 32-bit in Virtualbox, compiling on that and then copying the libraries over to my 64-bit install (into /lib32/). I amended the location of the main library in the dv4lstart script and all worked a treat!

HTH

Welly

Not entirely sure what u mean, as there is no 64bit version of skype..

---

### Post by wellynz on 2008-07-02
> **Plasma_NZ said:**
> Not entirely sure what u mean, as there is no 64bit version of skype..

Sorry!

I'm running Hardy 64-bit and so had to install various 32-bit libraries to get Skype to work. When I installed dv4l I just compiled on my 64-bit machine and tried to run Skype with no success. I then figured that because Skype is 32-bit I would need a 32-bit version of dv4l. I used a 32-bit install of Hardy (via Virtualbox) to compile the various libraries and copy them back to my 64-bit machine.

Hope that's clearer.

Cheers

Welly

---

### Post by dmoufarrege on 2008-07-02
> **bewo02 said:**
> can you start dv4l with some debugging enabled?
```
dv4l -v 2
```

I am getting this:

dv4l -v 2

dv4l.c +930: no vloopback input device found. vloopback module in kernel?

I installed vloopback based on the original instruction given in the how-to.

---

