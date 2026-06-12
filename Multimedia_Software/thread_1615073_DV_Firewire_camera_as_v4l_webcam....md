---
title: "DV Firewire camera as v4l webcam..."
date: 2010-11-06
forum: Multimedia Software
---

### Post by chconnor on 2010-11-06
Hi -

Trying to get my cheap DV firewire camcorder to work as a webcam on skype (version 2.1.0.81). Running kubuntu 10.04 on a Dell laptop (Inspiron 6000).

I may be behind the times and there is an obvious, easy way to do this... let me know. I know some of this stuff isn't exactly supported anymore, and the latest threads are from 2+ years ago... may not work in current kernels, etc etc.

I've gotten skype working with my USB webcams doing:

```
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

But the webcams are cheap, so I'm trying to get the camcorder to work. I'm working off threads such as:

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1006375](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1006375)
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=606790](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=606790)
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=664596](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=664596)

I installed v4l from the repository. I compiled vloopback successfully (afaik).

My understanding is that skype won't work with dv4l so i'm supposed to use dv4lstart. I've tried both methods, no luck.

Video shows up fine in kino. Can't get skype to see anything.

After startup, this is the basic process i'm using:

```
me@mymachine:~$ lsmod | grep video
video                  17375  0 
output                  1871  1 video
me@mymachine:~$ ls /dev/vid*
ls: cannot access /dev/vid*: No such file or directory

```

[turn on camera, connected via firewire to a PCMCIA 3-jack card]

```
me@mymachine:~$ lsmod | grep 1394
dv1394                 15275  0 
raw1394                22271  0 
ohci1394               26950  1 dv1394
ieee1394               81181  4 dv1394,raw1394,sbp2,ohci1394
me@mymachine:~$ sudo chmod 777 /dev/raw1394 
me@mymachine:~$ sudo modprobe videodev
```

Unfortunately:

```
me@mymachine:~$ dv4lstart ls -l /dev/vid*
ls: cannot access /dev/vid*: No such file or directory

```

Doesn't seem to be creating the virtual device?

Debugging output:

```
me@mymachine:~$ dv4lstart -v 3 ls -l /dev/vid*
interdv4l.c +388: set tracelevel to 3
interdv4l.c +140: #1__lxstat64 </dev/vid*>
interdv4l.c +313: is_videovdev devname </dev/video0> devalt </dev/v4l/video0> resolved </dev/vid*>
interdv4l.c +140: #2__lxstat64 </dev/vid*>
interdv4l.c +171: __lxstat64 path </dev/vid*> noredir 0 rv -1
ls: cannot access /dev/vid*: No such file or directory

```

dmesg shows nothing... I try running "dv4lstart skype" (with and without LD_PRELOAD) and no dice.

So I try the v4l method as well (i compiled the module and i guess it's in a weird location so i use insmod instead of modprobe):

```
me@mymachine:~$ sudo insmod /usr/src/modules/vloopback/vloopback.ko 
me@mymachine:~$ dv4l
use /dev/video1 in your webcam application

```
and in other term i run skype (with and without LD_PRELOAD) but append "/dev/video1" to the command line. It sees a device in the skype drop-down menu, but no video comes through.

If i start dv4l and do:

```
me@mymachine:~$ camorama -d /dev/video1
```

...then camorama gives an error about not finding the device and on the dv4l output it says:

```
VIDIOCSWIN invalid clip
```

and dmesg shows:

```
[ 3630.046409] [vloopback_init] : video4linux loopback driver v1.3
[ 3630.047095] [vloopback_init] : Loopback 0 registered, input: video0, output: video1
[ 3630.047098] [vloopback_init] : Loopback 0 , Using 2 buffers
[ 3743.698333] [vloopback_ioctl] : There was an invalid ioctl in Video loopback 0
[ 3746.137660] [vloopback_ioctl] : Wrong IOCTL 0 in Video loopback 0

```

When i'm trying out different combinations, Skype sometimes seems to hang for a while, in case that's a clue.

Any thoughts? Is this stuff basically dead in the water for now or should I keep plugging away?

Thanks!

-c

---

### Post by no2498 on 2010-11-07
im not sure if this program will help you
but you can change the vid 0/2/3 and things
its called wxcam

if you get the cam working in it may let skype see the settings

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)


hope it helps you

---

### Post by chconnor on 2010-11-07
Hi - Thanks for the idea... maybe you're just suggesting it as a general debugging tool? Unless i misunderstand, wxcam works off of v4l devices, e.g. /dev/video0, but i'm stuck at the stage of providing a v4l device from my 1394 device using dv4l, so i'm not sure i can even get the signal to wxcam to begin with... ? Maybe i should play with it...

Thanks,
-c

---

