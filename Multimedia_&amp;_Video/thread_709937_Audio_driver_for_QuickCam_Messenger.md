---
title: "Audio driver for QuickCam Messenger"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by algernon83 on 2008-02-27
I've installed the quickcam module according to the HOWTO on these forums, and I can get video from my QuickCam Messenger. However, I still don't know how to get audio from it. usbmodules suggests snd-usb-audio for the quickcam, but I don't know how "apply", for lack of a better word, that module to the given device (/proc/bus/usb/002/002). One of the few features I miss from Windows is the device manager, where I could see a device without a driver and tell it what driver to use. Is there anything similar for Ubuntu? Either way, how can I tell snd-usb-audio, or whatever module is appropriate, to listen to /proc/bus/usb/002/002?

Further, I can't get the quickcam module to be reinstated at reboot. I tried adding it to /etc/modules, but that doesn't work. In fact, modprobe quickcam doesn't work either. It only registers /dev/video0 when I run rmmod quickcam; insmod quickcam.ko. Any suggestions? I don't understand why this should be possible -- what does insmod do other than copy the module to the appropriate system directory and install it?

---

### Post by algernon83 on 2008-02-28
No thoughts? Is this the appropriate forum?

---

