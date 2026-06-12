---
title: "Strange webcam behavior with 9.04"
date: 2009-06-06
forum: Multimedia Software
---

### Post by vichor on 2009-06-06
Hi all,

This is my first post in the forums, but I have read lots of other articles from here and have learned really useful stuff. So first things firts.. thanks to you all for the help given so far... Now I will adventure to ask you for a bit more of help.

Oh, by the way, English is not my native language, so excuse me if something seems funny or innapropriate. 

Let's go to the problem...

My idea is to use a pair of cameras to set up a home video surveillance system using ZoneMinder. I have started with a cheap webcam for testing purposes. This webcam is Trust WB-3320X which seems to consist on a pac7331 chipset. 

The fact is that the linux kernel identifies properly the webcam and loads the needed modules. I have even seen my pretty face (ehem ehem) in Ekiga. So the webcam really works!

Now the funny behavior: when I use any other program than Ekiga, it does not work at all: 
***Update:** Ekiga sometimes give me also an error: "libv4l2: error dequeuing buf: Invalid argument".*
[LIST]
[*]Camorama gives me an "Unable to capture image" error just when opened and exits.
[*]XSane only gets "noise" (not a good image, just rubbish).
[*]the command mplayer tv:// does not work at all giving this output:
```
[FONT="Courier New"]vic@rapture:~$ mplayer tv:// -tv device=/dev/video0
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: USB Camera (093a:2621)
 Capabilites:  video capture  read/write  streaming
 supported norms:
 inputs: 0 = pac7311;
 Current input: 0
 Current format: unknown (0x47504a50)
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
FPS not specified in the header or invalid, use the -fps option.
No stream found.

v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.

Exiting... (End of file)[/FONT]
```
[/LIST]
So, in short, the webcam works but the applications refuse to work with the cam... Any ideas?

Thanks for your time
Victor

---

### Post by LoneSt4r on 2009-06-24
Hello!

I have a problem related with yours.  My webcam worked great until Ubuntu 7.10.  Since 8.04, I was unable to make it work.  I have the exact same symptoms you have.  On top of what you tried, I reinstalled manually the gspca drivers from two different sources.  The only thing that is now changed is that Camorama does not give me an error message, but does not give me a picture either.

This is the webcam I am using:

```
jp@PCJPLMTL:~$ lsusb | grep Z-Star
Bus 004 Device 002: ID 0ac8:0302 Z-Star Microelectronics Corp. ZC0302 WebCam
```

Any help would be highly appreciated.

Thanks!

LoneSt4r

---

### Post by josta7 on 2009-06-24
I'm still searching for a solution - My cam is a Z-Star 307b. All it's giving is this weird green striping.

---

### Post by vichor on 2009-06-25
Hi,

I still haven't got a solution, but I can add a bit more information just in case someone with enough knowledge of the problem stumbles upon here...

When I connect the webcam to the usb port, I get this dmesg output:

```

# dmesg
...
[  714.448025] usb 1-3: new full speed USB device using ohci_hcd and address 6
[  714.652727] usb 1-3: configuration #1 chosen from 1 choice
[  714.655629] gspca: probing 093a:2621
[  714.682900] gspca: probe ok
[  714.683178] gspca: probing 093a:2621

```

And the output from lsusb command is:
```

# lsusb 
...
Bus 001 Device 006: ID 093a:2621 Pixart Imaging, Inc.

```

Perhaps will help getting log traces from the gspca driver... Anyone knows how to enable (if possible) this feature?

LoneSt4r, this is for you... how did you uninstalled/installed manually the driver?

Thanks
Victor

---

### Post by vichor on 2009-06-25
Hi again,

I have found that PAC7311 chip based cams should work with **gspcav1** driver.

Any idea how to configure the kernel to run this gspcav1 driver when the cam is plugged?

Thanks,
Victor

---

### Post by vichor on 2009-07-15
I have found this post: 

[INDENT][http://ubuntuforums.org/showthread.php?t=1212707&highlight=webcam]("http://ubuntuforums.org/showthread.php?t=1212707&highlight=webcam")[/INDENT]

There, they recommend to switch to kernels 2.6.3x. Worth to check... Please update here if anyone updates to 2.6.3x and fix the problem.

---

### Post by LoneSt4r on 2009-12-31
> **vichor said:**
> LoneSt4r, this is for you... how did you uninstalled/installed manually the driver?

Hello!

Sorry for the late reply.  I just got back to trying to fix this in karmic.

This is what I tried today.  From several posts, it is supposed to work. Again, it does not for me. It builds the modules, I can load the modules, but /dev/video0 is never accessible.

Back to trouble shooting...

---

From [http://ubuntuforums.org/showthread.php?p=8537516](http://ubuntuforums.org/showthread.php?p=8537516)

> **g00fy11 said:**
> Hello,

[gauss_gs,]("http://ubuntuforums.org/member.php?u=952341") thanks a lot for these advice:

The resolution for this problem is to recompile gspca drivers from source with some modifications of vc032x source.

Before begin, disconnect camera from your PC and do:
$ modprobe -r gspca_vc032x

First, you will need to get source and some required packages:
```

$ sudo aptitude install mercurial build-essential linux-headers libncurses5-dev
$ hg clone http://linuxtv.org/hg/~jfrancois/gspca/
$ cd gspca
$ sudo make menuconfig 

```Disable DVB subsystem in menuconfig because you need full configured kernel source to compile DVB (I think, you have only kernel headers installed). 

```

$ make all
$ make all install

```Then connect camera to your pc. it must work now.

The DVB is in the submenu item marked as [M] when you open menuconfig.

I hope this will help someone!

LoneSt4r

---

### Post by LoneSt4r on 2009-12-31
Success!  The process works.

Using ```
tail -f /var/logs/messages
```

I was able to see the message saying that there was not enough power on my USB bus to power the web cam.  Silly me, I was trying to use it from my keyboard spare USB port.

I switched the webcam to a direct USB port and *voilà*!

Good luck to everyone as well!

LoneSt4r

---

### Post by vichor on 2010-01-04
Hi,

Lone4Star, this process has not worked for me. 

I have read the original article you copied in your previous reply, and it is for cameras based in another chipset. There is no sense in modifying the file [FONT="Courier New"]vc032x.c[/FONT] when I'm using a pac7302 camera, whose behaviour is described in the file [FONT="Courier New"]pac7302.c[/FONT]. On the other hand, the sources of the drivers have evolved since the article was written and does not apply anymore (no way to find the code that needs to be modified).

Anyway, thanks for the link, I have now the sources of the driver and can take a look at them by myself. I doubt I can fix the problem, as I have no knowledge about the hardware, but it's a step...

This thread keeps opened as there is still no solution.

Regards
Victor

---

### Post by no2498 on 2010-01-23
open a terminal type gstreamer-properties click video
try v4l1 or v4l2

the rest is from cheese




5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

---

### Post by vichor on 2010-01-24
Thanks for the info no2498. 

I have tried both v4l and v4l2 (v4l does not work even when pushing the test button). When using v4l2, the test works properly and I get an image of the camera.

But when I try another application (such as Camorama) it still doesn't work. I get the same effect on the applications as when trying v4l in gstreamer-properties, so it seems that they are using v4l instead of v4l2.

Any ideas?

---

