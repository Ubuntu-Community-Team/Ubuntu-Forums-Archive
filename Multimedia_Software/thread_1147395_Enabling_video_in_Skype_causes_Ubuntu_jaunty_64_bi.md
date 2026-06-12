---
title: "Enabling video in Skype causes Ubuntu jaunty 64 bit to crash"
date: 2009-05-03
forum: Multimedia Software
---

### Post by krippa on 2009-05-03
I'm trying to get skype to work on 64-bit Jaunty and after adding the medibuntu repository I got it installed. However, as soon as I activate my webcam, ubuntu crashes. Any ideas on resolving this? I really don't want to go back to 32-bit and lose 1GB of ram etc. but I need a video conferencing application. I wouldn't mind switching to something open like Ekiga but it does not seem to support encryption as well as a seemingly bad video quality and without ability to zoom with the webcam.

Here are the last kernel log entries before crash (and first after):

May  3 14:08:11 sueco kernel: [11241.745234] process `skype.real' is using obsolete setsockopt SO_BSDCOMPAT
May  3 14:09:02 sueco kernel: [11292.874671] CE: hpet increasing min_delta_ns to 75936 nsec
May  3 14:11:58 sueco kernel: [11468.585167] CE: hpet increasing min_delta_ns to 113904 nsec
May  3 17:28:55 sueco kernel: Inspecting /boot/System.map-2.6.28-11-generic
May  3 17:28:56 sueco kernel: Cannot find map file.
May  3 17:28:56 sueco kernel: Loaded 64645 symbols from 164 modules.

Oh, and running from command line gives me the following output when starting and running a test of the webcam (which works fine). I can't get the output from when I am in the call since the OS crashes...

Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
Starting the process...
Skype Xv: Xv ports available: 4
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 131
libv4l2: error converting / decoding frame data: v4l-convert: error parsing JPEG header: Not a JPG file ?


libv4l2: error converting / decoding frame data: v4l-convert: error parsing JPEG header: Not a JPG file ?


libv4l2: error converting / decoding frame data: v4l-convert: error parsing JPEG header: Not a JPG file ?


libv4l2: error converting / decoding frame data: v4l-convert: error parsing JPEG header: Not a JPG file ?


libv4l2: error converting / decoding frame data: v4l-convert: error parsing JPEG header: Not a JPG file ?


libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4l2: error converting / decoding frame data: v4l-convert: error parsing JPEG header: Not a JPG file ?

---

### Post by dtsmith1984 on 2009-06-15
Any updates on this?  I have the same problem however I'm using intrepid 64 bit.

---

### Post by krippa on 2009-06-16
Well, I now think this has to do with the camera itself because XSane scan software also crashes upon startup (in 32-bit I was able to scan using XSane without problems) before I even get to choose input device.

---

### Post by dtsmith1984 on 2009-06-16
My webcam seems to work fine with xawtv.

---

### Post by frederik.nnaji on 2009-07-08
> **dtsmith1984 said:**
> Any updates on this?  I have the same problem however I'm using intrepid 64 bit.

same here.. video is totally crappy and usually crashes X and freezes the computer .

user switching also doesn't work

using jaunty 64bit over here..

anyone got the launchpad bug page to this?

---

### Post by radiobuzzer on 2009-09-23
Same problems here, but not a 64bit system. Computer crashes when I turn on sending my video.

---

### Post by Rubadubdub on 2009-10-22
My skype works fine in when I start it the following way:
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

hope it helps you

---

