---
title: "OV51x webcam module load at startup?"
date: 2007-01-14
forum: Multimedia &amp; Video
---

### Post by gentle_turtle on 2007-01-14
Hello everyone,

Having put my hands on a Hercules Classic webcam, I managed to install the ov51x-jpeg-0.5.4 tarballs and compile them on my dapper 6.06 LTS server.

If I do by hand the following:

sudo modprobe videodev
sudo modprobe i2c_core
sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
sudo insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko

the webcam gets recognized, /dev/video0 gets loaded and the cam works fine
(both with xawtv and  camE to upload the webcam images to a server). 
However, if I reboot the machine, even with the webcam plugged in, 
the modules do not get loaded. I tried to force module loading by adding 
in /etc/modules the lines 

ov51x
ov519_decomp

but this resulted into nothing. No /dev/video0, no error messages in /var/log/messages, no mention of ov5x modules in dmesg.

Also plugging out/in again the cam generates no driver loading....

How do I load a module so that every time the device is present in the USB bus
it loads automatically? Or how can I add a module so that it loads at boot time?

I know, I must be missing something silly. Many thanks in advance for any help

---

### Post by gentle_turtle on 2007-01-15
A few more attempts sow that if the cam is plugged in at bootup, or if it is plugged in after bootup, then it loads only the ov51x module but does not generate video0, nor load directly the ov519_decomp module. 

Any ideas how to make it load also the other two drivers automagically?

---

