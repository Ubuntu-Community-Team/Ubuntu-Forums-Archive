---
title: "hp inbuilt webcam doesn't turn on"
date: 2013-10-17
forum: Multimedia Software
---

### Post by atul2 on 2013-10-17
My inbuilt HP web cam doesn't turn on (with cheese webcab booth)  after installing ubuntu 12.04 lts on my HP pavilion G42 notebook pc.then i tried it turn on with webcam studio.but it doesn't work.
**webcam detail is as follows:-**
[I]ubuntu@ubuntu-linux:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 052: ID 19d2:1008 ZTE WCDMA Technologies MSM 
[/I]
**system information**
[I]ubuntu@ubuntu-linux:~$ uname -a
Linux ubuntu-linux 3.2.0-34-generic-pae #53-Ubuntu SMP Thu Nov 15 11:11:12 UTC 2012 i686 i686 i386 GNU[/I]/*Linux*

**on running "cheese" command in terminal i got following message:-**
(cheese:9990): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel
libv4l2: error getting pixformat: Invalid argument

** (cheese:9990): CRITICAL **: cheese_camera_device_get_uuid: assertion `CHEESE_IS_CAMERA_DEVICE (device)' failed
Segmentation fault (core dumped)

[B]
plzz... help me [/B]

---

### Post by mörgæs on 2013-10-18
Hi, welcome to the fora.

How does it work in a live boot of 13.10?

---

### Post by atul2 on 2013-10-18
Thanks to reply......

I havn't tried it with 13.10 and i don't want to switch 13.10 right now.
Can't it be fixed with 12.04?? If not then why??

I am novice to computer and ubuntu so plz instruct me in simple way.

---

### Post by mörgæs on 2013-10-19
I don't know if it can be fixed, but first step in troubleshooting should be trying a number of releases. 

The bug might have been found and fixed already (in a later release) without you knowing it.

---

