---
title: "HOWTO: ov51x-jpeg webcam in Skype 2.0 beta"
date: 2008-02-07
forum: Multimedia &amp; Video
---

### Post by snyperof1 on 2008-02-07
Howto: Make a ov51x-jpeg webcam work with skype 2.0 beta

First off: I'm in no way a developer, or programmer. I've been using Linux for only about a year now, and this is my first howto. I'm writing this because of wide-spread problems with this webcam driver and skype and how I was unable to find a guide in English. With that said I hope this works for you, please comment on your successes/failures and I'll try to help where I can. Thank you.

After much searching and little success trying to get my webcam to work with skype, I finally sumbled across this thread in the Polish forums 
[http://forum.ubuntu.pl/showthread.php?t=62233&highlight=skype]("http://forum.ubuntu.pl/showthread.php?t=62233&highlight=skype") 
 and this blog post.
[http://italyanker.wordpress.com/2007/12/02/creative-live-cam-vista-im-e-skype-workaround/]("http://italyanker.wordpress.com/2007/12/02/creative-live-cam-vista-im-e-skype-workaround/")
 I find the first link to be much more complete than the second and would recommend you refer to it. However it contains the came commands found here.

First thing is Does this guide apply to you?
In a terminal type:
```
lsusb
```
and look and the vendor and product ID's of your webcam, if it matches one of these:
```
05A9:0511
05A9:A511
05A9:0518
05A9:A518
05A9:0530
05A9:0519
05A9:1519
05A9:2519
05A9:3519
05A9:4519
05A9:5519
05A9:6519
05A9:7519
05A9:8519
05A9:9519
05A9:A519
05A9:B519
05A9:C519
05A9:D519
05A9:E519
05A9:F519
0813:0002
054c:0154
054c:0155
054c:0156
054c:0157
45e:28c
041e:4052
041e:405f
```
This guide should work for your webcam.

Next unplug your webcam, and download this patched driver (its also attached to this thread)
```
wget http://web.tiscali.it/lele85_home/ov51x-jpeg-1.5.3~skype_patch.tar.gz
```
untar it
```
tar xzvf ov51x-jpeg-1.5.3~skype_patch.tar.gz
```
change to that directory
```
cd ov51x-jpeg-1.5.3~skype_patch
```
patch the file
```
patch -p1 < ov51x_jpeg_core.noblock.patch.txt
```
NOTICE! if this command returns an error (as it did for me), use this command instead
```
patch -p0 < ov51x_jpeg_core.noblock.patch.txt
```
now compile the driver
```
make clean
```
```
make
```
```
sudo make install
```
remove the old driver
```
sudo depmod
```
```
sudo rmmod ov51x-jpeg
```
load the new one
```
sudo modprobe ov51x-jpeg forceblock=1
```

now add this line:
```
options ov51x-jpeg forceblock=1
```
to these to files:
```
sudo gedit /etc/modprobe.d/options
```
```
sudo gedit /etc/modprobe.conf
```

Now lets use mplayer to test it:
```
mplayer tv:// -tv driver=v4l:width=640:height=480:device=/dev/video0
```

Now, for me the mplayer test worked great, but in skype my video was all pink and green. So to fix that, just do this:
```
sudo gedit /etc/modprobe.d/options
```
and and this line to it:
```
options ov51x-jpeg force_palette=1
```
and that fixed it for me.

Enjoy!

If you encounter difficulties, post them here. I'll help where I can, and I'm sure others will jump in to help as well. Thank you.

---

### Post by mooha on 2008-02-07
Many thanx to you, nice one

---

### Post by snyperof1 on 2008-02-07
No problem, glad to help

---

### Post by dynamethod on 2008-02-09
hmm, still didnt work for me

i have:

Bus 002 Device 003: ID 05a9:a518 OmniVision Technologies, Inc.


and the part where you add

options ov51x-jpeg forceblock=1

to:

/etc/modprobe.conf

ell, modprobe.conf doesnt exist on my Kubuntu 7.10, but i made the file anyhow, though skype nor kopete still dont recognise my device :S

---

### Post by dynamethod on 2008-02-09
also after trying mplayer tv:// -tv driver=v4l:width=640:height=480:device=/dev/video0

i got:

MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 3, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Creating config file: /home/xen/.mplayer/config
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l
 name: Video 4 Linux input
 author: Alex Beregszaszi
 comment: under development
unable to open '/dev/video0': Function not implemented


MPlayer interrupted by signal 11 in module: demux_open
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

---

### Post by snyperof1 on 2008-02-11
Ok, bad news.

This fix has now stopped working for me. 
I cant confirm this, but I believe a recent update to Gusty is causing it, because this process works when I boot from a fiesty Live-CD, and creating a new user doesn't fix it, so the break is at the system level.

I downloaded the latest ov51x-jpeg driver (ver 1.5.5) and applied the patch to it, but no luck.

Here's the what dmesg prints:

```
[14117.336000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[14117.540000] usb 2-2: configuration #1 chosen from 1 choice
[14117.872000] usbcore: registered new interface driver snd-usb-audio
[14117.888000] Linux video capture interface: v2.00
[14117.940000] /home/dev/ov51x-jpeg-1.5.5/ov51x-jpeg-core.c: USB OV519 video device found
[14118.336000] /home/dev/ov51x-jpeg-1.5.5/ov51x-jpeg-core.c: Sensor is an OV7648
[14118.396000] /home/dev/ov51x-jpeg-1.5.5/ov51x-jpeg-core.c: Camera initialization failed
[14118.396000] ov51x: probe of 2-2:1.0 failed with error -5
```

I assume "failed with error -5" is the specific error code but I cant find anything that tells me what that error code translates into.

Well, at least it worked for about two days for me. From here I'm going to see if any driver options help, but it'd be really nice to know what that error means.

---

### Post by genjosanzo on 2008-04-23
I have the following problem. I think the guide is perfect but,since I'm already using Hardy Heron there's a bug ([https://bugs.launchpad.net/bugs/190450](https://bugs.launchpad.net/bugs/190450)) that doesn't allow the success of make. Thi is is due to an uncorrect declaration of a function(see the bug page for more details). The point is that in the bug page there's a deb fixing the bug(but of course still doesn't work with skype). Is possible to patch that deb to obtain the same result also for hardy? If the answer is yes,how to do that? Thanks in advance

---

### Post by kumarnarain on 2008-06-27
Hai
This is the error I got after I ran 'make'...Any ideas??

kumar@kumar-laptop:~$ tar xzvf ov51x-jpeg-1.5.3~skype_patch.tar.gz
ov51x-jpeg-1.5.3~skype_patch/
ov51x-jpeg-1.5.3~skype_patch/test/
ov51x-jpeg-1.5.3~skype_patch/test/Makefile
ov51x-jpeg-1.5.3~skype_patch/test/getjpeg.c
ov51x-jpeg-1.5.3~skype_patch/ov51x_jpeg_core.noblock.patch.txt
ov51x-jpeg-1.5.3~skype_patch/ChangeLog
ov51x-jpeg-1.5.3~skype_patch/ov7670.h
ov51x-jpeg-1.5.3~skype_patch/ov519-decomp.c
ov51x-jpeg-1.5.3~skype_patch/ov518-decomp.c
ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg.h
ov51x-jpeg-1.5.3~skype_patch/Makefile
ov51x-jpeg-1.5.3~skype_patch/ov511-decomp.c
ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.c
kumar@kumar-laptop:~$ cd ov51x-jpeg-1.5.3~skype_patch/
kumar@kumar-laptop:~/ov51x-jpeg-1.5.3~skype_patch$ patch -p0 < ov51x_jpeg_core.noblock.patch.txt
patching file ov51x-jpeg-core.c
kumar@kumar-laptop:~/ov51x-jpeg-1.5.3~skype_patch$ make clean
rm -rf .*.cmd  *.mod.c *.ko *.o .tmp_versions Module.symvers *~ core *.i *.cmd .ov51x-jpeg-core.o.d
kumar@kumar-laptop:~/ov51x-jpeg-1.5.3~skype_patch$ make
make -C /lib/modules/2.6.24-16-generic/build M=/home/kumar/ov51x-jpeg-1.5.3~skype_patch modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/kumar/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.o
/home/kumar/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.c:6618: error: unknown field ‘hardware’ specified in initializer
/home/kumar/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.c:6618: error: ‘VID_HARDWARE_OV511’ undeclared here (not in a function)
make[2]: *** [/home/kumar/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.o] Error 1
make[1]: *** [_module_/home/kumar/ov51x-jpeg-1.5.3~skype_patch] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [all] Error 2

---

### Post by QkEterror on 2008-07-03
> **genjosanzo said:**
> I have the following problem. I think the guide is perfect but,since I'm already using Hardy Heron there's a bug ([https://bugs.launchpad.net/bugs/190450](https://bugs.launchpad.net/bugs/190450)) that doesn't allow the success of make. Thi is is due to an uncorrect declaration of a function(see the bug page for more details). The point is that in the bug page there's a deb fixing the bug(but of course still doesn't work with skype). Is possible to patch that deb to obtain the same result also for hardy? If the answer is yes,how to do that? Thanks in advance

Just take the newest version from rastageeks.org ([http://www.rastageeks.org/downloads/ov51x-jpeg/](http://www.rastageeks.org/downloads/ov51x-jpeg/)). This already seems to contain the patch. When I tried to patch it, patch told me it was probably already patched. I get video with it, but it is a waterfall of red yellow and green. That's probably specific for my device though. You could give it a try.

---

