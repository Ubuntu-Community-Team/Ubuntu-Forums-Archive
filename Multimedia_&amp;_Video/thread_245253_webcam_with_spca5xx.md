---
title: "webcam with spca5xx"
date: 2006-08-27
forum: Multimedia &amp; Video
---

### Post by galvorn on 2006-08-27
Hello, i have a strange problem.

I have a webcam.
```
luca@blackrose ~ $ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 008: ID 0c45:613e Microdia
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000

```

I have downloaded and succefully compiled spca5xx drivers, that is currently  modprobed.

When i attach the camera, dmesg says:
```
[17182604.544000] usb 2-1: new full speed USB device using uhci_hcd and address 2

```
And stop.

I don't have /dev/video or video0, i've tryed to create manually with
```
# mknod /dev/video0 c 81 0
# chmod 666 /dev/video0
# ln -s /dev/video0 /dev/video
```
but the situations is the same.

I don't understand what is the problem :|

I'm running DapperDrake with 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux from the repos on a HP NX8220 Notebook.

Some ideas?

(Sorry for bad english)

---

### Post by berkson on 2007-02-17
hey bro.. are you brazilian? well,  I have the same problem, you can't mount your camera, or better, your linux can't make this for you cause the spca5XX module can't use this type of chipset 0c45 613e, I have this camera too. If you plain to use camera on linux, I think that you have to buy another one, take the list of support of the spca5XX module as base for a new compatible hardware, or wait for someone make a compatible module.

(sorry for the bad english too...)

Berkson (Using Debian Sarge 3.1r4 and Ubuntu 6.10 Edgy):lolflag:

---

### Post by drpaul on 2007-02-17
I have a camera in my laptop that has code 0x62c0. I was able to get ekiga to use the camera by installing the uvcvideo driver.

Search the threads for webcam install and you'll find some detailed instructions. Just remember to add a modprobe uvcvideo after you have done the make install.

HTH

Paul

---

### Post by az on 2007-02-17
> **galvorn said:**
> 
I have a webcam.
...

I have downloaded and succefully compiled spca5xx drivers, that is currently  modprobed.

When i attach the camera, dmesg says:
```
[17182604.544000] usb 2-1: new full speed USB device using uhci_hcd and address 2

```
And stop.


Your webcam is not the spca5xx chipset.

The driver is already included in Ubuntu.  You don't (wouldn't) need to recompile it.

---

### Post by KhaaL on 2007-03-02
> **az said:**
> Your webcam is not the spca5xx chipset.

The driver is already included in Ubuntu.  You don't (wouldn't) need to recompile it.

I got QuickCam Messenger and it does use the spca5xx driver - yet i get the very same message in dmesg...

---

### Post by &gt;&gt;robby on 2007-10-18
i have an 0c45:613e microdia cam the driver for it is sn9c1xx you can download and install it, just unpack it and type:
make
sudo make install 
sudo modprobe sn9c102


The system find camera and put the new device in dev directory. ( /DEV/VIDEO ).

The problem isn't driver , it's the software!! I can obtain something (just an ugly picture) by run one simple application wrote for the v4l2 devices in ANSI C for grab image.

If you want you can compile and run the attached file.
I'm not able to obtain a clean image if you can do it post the solution here, thank you.

---

