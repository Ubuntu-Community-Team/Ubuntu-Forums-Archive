---
title: "Video device."
date: 2013-03-02
forum: Multimedia Software
---

### Post by xinemae on 2013-03-02
I have a Lenovo ideapad p500, and the integrated webcam isn't working when I use programs like Cheese or Google+ from my Chrome browser. I've been able to "hangout" in Google+ in the past on this machine, and I do not recall uninstalling anything that had to do with my video. I've searched through the posts here and through a Google Search and I haven't been successful in finding a solution. I did a lsusb to see if I could figure out what manufacture makes my camera and get the drivers for it, but when looking at the results I don't think I see one loaded. 

```
cecilia@cecilia-Lenovo-IdeaPad-P500:~$ lsusbBus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 004: ID 8087:07da Intel Corp. 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. 
```

I installed cheese as well as gstreamer-properties and neither allows me to view the camera. In terminal I get these results...

```
(gstreamer-properties:8846): Gtk-WARNING **: Unknown property: GtkDialog.has-separator


(gstreamer-properties:8846): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
``` 

and I get [ATTACH=CONFIG]239668[/ATTACH] this. It doesn't allow me to select a device, which leads me to believe my camera isn't loaded anymore. 

So my question is, how do I get the camera loaded?

Thanks in advance!

---

### Post by xinemae on 2013-03-04
bump, please :)

---

### Post by Mugatu on 2013-03-06
Try this:

[http://askubuntu.com/a/264461/18665](http://askubuntu.com/a/264461/18665)

If it works for you, please contribute to the bug report mentioned in that link, so we can get as much attention from developers as possible to get this resolved soon.  Thanks!

---

### Post by xinemae on 2013-03-07
Awesome Mugatu, thanks! Will try and post here later.

---

### Post by mörgæs on 2013-03-07
It would also be great if you could test the camera in 13.04.

---

