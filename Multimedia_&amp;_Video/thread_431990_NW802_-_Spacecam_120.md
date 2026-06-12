---
title: "NW802 - Spacecam 120"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by hugolia on 2007-05-03
I am trying to compile the NW802 kernel module without success...

I followed the instructions step by step but I am stuck.

The compiles detects missiong ***usbvideo.c*** and ***usbvideo.h***

I searched and discovered that those files are missing from the kernel source.

----------------------

I'd discovered an ***usbvideo.ko*** file but I don't have the knowledge as how to modify the makefile.


----------------

Can anyone please help me?

---

### Post by bxctn on 2007-07-09
nw802-2.4$ make
ln -sf /lib/modules/`uname -r`/build/drivers/media/video/usbvideo/usbvideo.h .
ln -sf /lib/modules/`uname -r`/build/drivers/media/video/usbvideo/usbvideo.c .

sudo apt-get install linux-source-
get usbvideo.h and usbvideo.c from kernel source.

or

go 
[[COLOR="Red"]here[/COLOR]]("http://lxr.free-electrons.com/source/drivers/media/video/usbvideo/") 
download usbvideo.h and usbvideo.c

my `uname -r` is "2.6.20-16-generic"

so choose Version: 2.6.20 .

put download files in /lib/modules/`uname -r`/build/drivers/media/video/usbvideo/

fix files , they don't need Serial numbers.

then "make" !!

ps:Pardon for my poor English

---

