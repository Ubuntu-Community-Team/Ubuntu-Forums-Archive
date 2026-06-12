---
title: "USB Tuners 9.04 &amp; Mythtvbackend"
date: 2009-05-04
forum: Multimedia Software
---

### Post by BjBlaster on 2009-05-04
Hi Guys,

I've got a 9.04 box running MythTV installed using apt-get. It works fine, but after being left over night the 4 USB tuners I have just lock up. This hardware system works fine on 8.10 mythbuntu, so it's not the hardware.

The question I have is how can I check or verify the V4Linux drivers are working properly? The mythbackend doesn't lock up, it's just the access to the drivers. I can pull the USB and plug them back in again, at which point the dmesg says they are working, but mythtv cannot channel lock with them. The only fix is to restart the whole PC.

I have found a fix involving diff files and recompiling drivers, but is there and easier way?

[http://www.mail-archive.com/linux-dvb@linuxtv.org/msg27354.html](http://www.mail-archive.com/linux-dvb@linuxtv.org/msg27354.html)

Any ideas?

Otherwise can someone please point me in the right direction of how to patch this driver and recompile the kernel on 9.04?

Thanks

Bj

---

### Post by BjBlaster on 2009-05-04
I sussed it using the fix:

RECOMPILE DRIVERS

Install the necessary software:



sudo apt-get install mercurial linux-headers-generic build-essential



Obtain the latest v4l-dvb source code:



hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)



patch file: /home/user/src/v4l-dvb-83712d149893/linux/drivers/media/dvb/dvb-usb/vp7045.c



patch -p0 < /home/user/hannaa/src/vp7045.diff



Compile and install:



cd v4l-dvb-83712d149893

make

sudo make install

---

