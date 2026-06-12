---
title: "Hercules webcam not working in feisty anymore (problem with ov51x-jpeg-1.5.2)"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by Hugolp on 2007-07-25
Hi

I have a feisty computer with the hercules webcam installed and working fine with the ov51x-jpeg driver.

But I have tried to install it in another computer that has feisty as well and havent been able to install it. I have compiled the lastest driver version, tried the debian module using module-assistant (as written in the module webpage) and it didnt work. I though it might be that the upadated driver might be broken in feisty so I tried to install the previous version. Didnt work neither.

My guess might be that some updates in feisty broke the driver¿? Its the only thing that it has changed since I installed the cam a couple of months ago.

I have been trying hows to and forum threads but nothing solves it.

I get this errors (and one with some variable missing or not right in the make):

sudo modprobe ov51x-jpeg

FATAL: Error inserting ov51x_jpeg (/lib/modules/2.6.20-16-generic/kernel/drivers/usb/ov51x-jpeg.ko): Unknown symbol in module, or unknown parameter (see dmesg)


dmesg (it repeats this a lot):

[217763.280000] ov51x_jpeg: Unknown symbol video_unregister_device
[217763.280000] ov51x_jpeg: disagrees about version of symbol video_device_alloc
[217763.280000] ov51x_jpeg: Unknown symbol video_device_alloc
[217763.280000] ov51x_jpeg: disagrees about version of symbol video_register_device

Any help apreciated.

Hugo

---

### Post by Offoffoff on 2008-02-03
I have made like this:
1. I compiled driver
2. sudo apt-get install ov51x-jpeg-source
3. module-assistant a-i ov51x-jpeg (many mistakes, but who cares)
4. sudo mknod /dev/video2 c 81 2 (because I already have two video devices, I do not know why - Ubuntu don't want to make it automatically)
5.sudo chmod a+rw /dev/video2
6. plug camera to usb
7. sudo modprobe -f ov51x-jpeg
Camera works. But audio channel of camera catches audio hw1.0 where already tv-tuner sends sound, camera shifts hw1.0 to hw2.0. And sometimes, I did not get - when and why, system loose video2. And every time I need to use camera - I have to use:
sudo modprobe -f ov51x-jpeg

---

