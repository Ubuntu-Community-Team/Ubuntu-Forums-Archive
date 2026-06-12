---
title: "Cameras Don't Show Up In Zoneminder"
date: 2009-10-05
forum: Multimedia Software
---

### Post by zdunham on 2009-10-05
Hi all.

Trying to set up a video surveillance system with Zoneminder. I am using a Logitech Quickcam for this. The camera works with Ubuntu, when I run XawTV I can see everything clear as day. When I try to get the camera to show up in Zoneminder I get no picture. I have tried a bunch of different device format and color combinations and still cannot get it to show up. If anyone has any experience with Zoneminder or has had this problem please help! Thanks in advance.

(This is the newest Ubuntu)

---

### Post by zdunham on 2009-10-05
Could a moderator please move this to the general forum? I believe it could fall under several categories and it would be better if more people could see it. Thanks.

---

### Post by zdunham on 2009-10-06
bump

---

### Post by zdunham on 2009-10-06
OK, my setup is local, I do have the camera plugged directly into the computer at the moment.

The log file that caught my attention the most was zmdc.log which revealed this:

10/05/2009 16:22:32.055844 zmdc[22302].INF [Starting pending process, zmc -d /dev/video0]
10/05/2009 16:22:32.057722 zmdc[22302].INF ['zmc -d /dev/video0' starting at 09/10/05 16:22:32, pid = 19336]
10/05/2009 16:22:32.099510 zmdc[22302].ERR ['zmc -d /dev/video0' exited abnormally, exit status 6]

To me, at least, it looks like it tried to start the camera and failed but I couldn't find much on what exit status 6 is yet. I shall continue hunting. Thanks for whatever information you can give and have given.

After googling exit status 6, every forum topic I could find on it was inconclusive as to the problem.

I tried changing the device format and color multiple times, even tried gray as was recommended somewhere else and that did not work either.

---

### Post by kpholmes on 2011-06-08
does anyone know a solution to this? having the same problem.

```
Jun  8 19:05:03 MasterKush zmc_dvideo1[2504]: INF [Starting Capture]
Jun  8 19:05:03 MasterKush zmc_dvideo1[2504]: INF [Got signal 6 (Aborted), exiting and forcing backtrace]
```


found this on the apache error log

```
[Wed Jun 08 18:55:03 2011] [error] [client 192.168.1.101] PHP Deprecated:  Function split() is deprecated in /usr/share/zoneminder/skins/classic/views/options.php on line 193, re$
[Wed Jun 08 19:04:20 2011] [notice] caught SIGTERM, shutting down
[Wed Jun 08 19:04:21 2011] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.9 with Suhosin-Patch configured -- resuming normal operations


```

i have two cams, and they are both seen and available, works with cheese.

```
[   13.594222] input: USB2.0 HD UVC AF Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/input/input6
[   13.594270] uvcvideo: Found UVC 1.00 device USB2.0 HD UVC AF Camera (04f2:a146)
[   13.602785] input: USB2.0 HD UVC AF Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input7

```

in my syslog when i restart zoneminder it says the path to the webcam is broken

```
n  8 19:21:27 MasterKush zmdc[2820]: INF [Starting pending process, zmc -d /dev/video]
Jun  8 19:21:27 MasterKush zmdc[2820]: INF ['zmc -d /dev/video' starting at 11/06/08 19:21:27, pid = 2853]
Jun  8 19:21:27 MasterKush zmdc[2853]: INF ['zmc -d /dev/video' started at 11/06/08 19:21:27]
Jun  8 19:21:27 MasterKush zmc_dvideo[2853]: INF [Debug Level = 0, Debug Log = <none>]
Jun  8 19:21:27 MasterKush zmc_dvideo[2853]: INF [Starting Capture]
Jun  8 19:21:27 MasterKush zmc_dvideo[2853]: FAT [Failed to stat video device /dev/video: No such file or directory]

```

where can i edit the camera config?

---

### Post by no2498 on 2011-06-09
does your cam come on xawtv
it loads a cam grabber as you have no dev video 0

---

### Post by hornetster on 2011-07-14
Yep, same prob. Camera works in Cheese OK (once you chmod /dev/video0).
zmu -d /dev/video0 -q -v gives:
john@Linux-250:/dev$ zmu -d /dev/video0 -q -v
Video Device: /dev/video0
General Capabilities
  Driver: uvcvideo
  Card: USB2.0 Camera
  Bus: usb-0000:00:1d.0-1
  Version: 1.0.0
  Type: 0x4000001
    Supports video capture (X)
    Does not support video output
    Does not support frame buffer overlay
    Does not support VBI capture
    Does not support VBI output
    Does not support sliced VBI capture
    Does not support sliced VBI output
    Does not support video output overlay
    Does not have tuner
    Does not have audio in and/or out
    Does not have radio
    Does not support read/write i/o (X)
    Does not support async i/o
    Supports streaming i/o (X)
    Standards:
  Formats:
    YUV 4:2:2 (YUYV) (YUYV)
Crop Capabilities
  Bounds: 640 x 480
  Default: 640 x 480
  Current: Cropping is not supported
Inputs: 1
  Input 0
    Name: Camera 1
    Type: Camera
    Audioset: 00000000
    Standards: 0x0
    Power on  (X)
    Signal detected  (X)
    Colour Signal detected 
    Horizontal Lock detected 
john@Linux-250:/dev$ 

but can't seem to get Zoneminder to pick it up. Have tried all sorts of settings for the Monitor, with no luck. Anyone have any ideas?
Thanks, John

---

### Post by haqking on 2011-07-14
i suspect you will get more joy here [http://www.zoneminder.com/forums/](http://www.zoneminder.com/forums/)

also have you checked the HCL for your particualr camera

[http://www.zoneminder.com/wiki/index.php/Hardware_Compatibility_List](http://www.zoneminder.com/wiki/index.php/Hardware_Compatibility_List)

---

### Post by bo.vestergaard on 2011-08-05
I have the exact same problem. It used to work fine in 10.04 but yesterday I installed 11.04 and since then I cannot get it to work. I wonder what they changed in 11.04. It looks like some library or codec is missing. Does anyone know if they took something out of 11.04?

---

