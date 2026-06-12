---
title: "uvcvideo disappeared"
date: 2013-03-20
forum: Multimedia Software
---

### Post by Chuckaluphagus on 2013-03-20
I was attempting to get a USB television tuner to work with my notebook (Ubuntu 12.04, 64-bit, 3.2.0-39-generic kernel) and followed [the instructions on the LinuxTV.org wiki]("http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers").  That didn't work -  I didn't get any apparent errors (certainly nothing I could recognize as such) during the build process or when running "sudo make install" afterwards, but the tuner still didn't work (it was detected, but I guess it isn't supported yet).  Not a big deal.

However, what is a big deal is that the webcam built into my notebook is suddenly non-functional.  It has always worked, right from installation, without any effort on my part.  It still shows up in lsusb as:

```
04f2:b221 Chicony Electronics Co., Ltd integrated camera
```

but nothing recognizes it anymore.  I don't have /dev/video or /dev/v4l directories, either, "lsmod | grep uvcvideo" returns nothing, and "sudo modprobe -r uvcvideo && sudo modprobe uvcvideo" gets me
```
FATAL: Module uvcvideo not found.
```

Clearly, something went wrong, and I don't know enough to fix it.  If anyone can help me figure this out, it'd be much appreciated.  Feel free to ask any questions, I can always provide more information.

**UPDATE:** If I boot into an older kernel - in this case I tried 3.2.0-38 - everything works fine, and the camera is functional.  So apparently I didn't remove the uvcvideo driver from my system, I just have stopped it from loading when I boot normally.  Still needs fixing, but that might be a clue for someone out there with more knowledge than me.

---

