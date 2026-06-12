---
title: "USB Tuner - HDTV110, Won't Work"
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by 4rk3typ3 on 2008-04-14
I recently purchased a Diamond HDTV110 USB TV Tuner and I am unable to get it to work.

Tech Info:
Tuner Dev = 1-1
-lsusb-
Bus 002 Device 003: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 002 Device 002: ID 06a3:8020 Saitek PLC 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 024: ID 07de:0001  
Bus 001 Device 001: ID 0000:0000  

-Relative dmesg-
[30.332393] usb 1-1: new high speed USB device using ehci_hcd and address 2
[30.728481] usb 1-1: configuration #1 chosen from 1 choice
[67676.520743] usb 1-1: USB disconnect, address 19
[67678.846611] usb 1-1: new high speed USB device using ehci_hcd and address 24
[67679.242823] usb 1-1: configuration #1 chosen from 1 choice

I have used xawtv, mplayer, vlc and xine all to no avail. 

Upon attempting to configure the tuner using sudo v4l-conf -c  /dev/1-1 i received this error:
v4l-conf: using X11 display :0.0
dga: version 2.0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13

I tried the -nodga tag within xawtv but it still gave the same error along with everything else succeeding. 

Any help would be greatly appreciated.

P.S. I am still fairly new to linux, if you need any other info let me know.

---

### Post by xc3RnbFO8P on 2008-04-14
Try this: 
> I fixed the problem modifying /etc/initramfs-tools/modules and adding two lines:

/etc/initramfs-tools/modules:
...
ohci_hcd
ehci_hcd
> sudo gedit  /etc/initramfs-tools/modules
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/66115]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/66115")

---

### Post by 4rk3typ3 on 2008-04-14
Well, that did help make it a USB 2.0 device, however I am still getting errors trying to initialize it through those programs.

one thing I did notice was that modprobe is listing a usbvideo entry:

/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/i2c-drivers/saa717x.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/driver/ivtv-fb.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/usbvideo/uvcvideo.ko

I don't know what I can do with that, but it's there.

What I did notice when running the xawtv command [sudo xawtv -nodga -c /dev/2-1] was that It listed a message about an Inappropriate ioctl for device:

[: 12: (opcode:: unexpected operator
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
xinerama 0: 1920x1200+0+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
ioctl: VIDIOC_QUERYCAP(driver="";card="";bus_info="";version=0.0.0;capabilities=0x0 []): Inappropriate ioctl for device
no video grabber device available

I am curious, is that basically saying the software cannot communicate with the hardware specified?

---

### Post by xc3RnbFO8P on 2008-04-15
Try **Tvtime** and **Kaffeine**

---

### Post by xc3RnbFO8P on 2008-04-15
Here is Howto scan  dvb and convert the channels to ATSC, (HdTv)
[http://hftom.free.fr/phpBB2/viewtopic.php?t=115&highlight=hdtv]("http://hftom.free.fr/phpBB2/viewtopic.php?t=115&highlight=hdtv")

---

### Post by 4rk3typ3 on 2008-04-15
I appreciate the suggestions.

I tried tvtime but unfortunately when I specified the device to use it returned an error relating to V4L. 

Error:
[Not a video4linux device - Cannot open capture device /dev/2-1.]


Kaffeine couldn't detect it either unfortunately.

At the moment, I need to somehow get the USB tv tuner detected by V4L and after that then through tvtime or VLC.

Also, I received this error when running [sudo v4l-conf -d /dev/2-1]:
WARNING: remote display `/dev/2-1' not allowed, exiting

This appears to indicate that it is not a compatible v4l device. I will be searching google, but is there a way I can retool the firmware to be compatible?

---

### Post by xc3RnbFO8P on 2008-04-15
Did you install v4l drivers?
In terminal:
> sudo apt-get install mercurial linux-headers-$(uname -r) build-essential
> hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
> cd /home/your folder/v4l-dvb
> make all
> sudo make install

---

### Post by 4rk3typ3 on 2008-04-15
I hadn't but after doing so and attempting the configure again, it still did not allow it. I was hearing mention that this card is very similar to some of the pinnacle devices out there, and linuxtv.org had some experimental drivers to install, but after doing so I have no clue what to do with what I installed. 

[http://mcentral.de/wiki/index.php5/Installation_Guide](http://mcentral.de/wiki/index.php5/Installation_Guide)

That is what I installed.

---

### Post by xc3RnbFO8P on 2008-04-15
1. Do have this driver  /lib/firmware/2.6.???/**xceive_xc_3028.fw** ?
If not:
2. Do you got this package on your computer** userspace-drivers-35f2b20d9abe.tar.gz**
If you do, extract and:
> cd  /home/your folder/userspace-drivers-35f2b20d9abe/userspace/xc3028
> make
> sudo make install

3. Try this:
> sudo modprobe em28xx
> sudo modprobe em2880-dvb
and start Kaffeine, xawtv or Tvtime

4. Download more drivers :
[http://konstantin.filtschew.de/v4l-firmware/firmware_v3.tgz]("http://konstantin.filtschew.de/v4l-firmware/firmware_v3.tgz")
extract and put them in **/lib/firmware/2.6.???/**
and try 3. again

Look at this:  /home/your folder/v4l-dvb/v4l_experimental/xc3028/**README**

---

### Post by 4rk3typ3 on 2008-04-16
still no...the USB device needs to go from 1-1 or 2-1 to video0, that seems to be my prime objective as it would seem 1-1 and 2-1 isn't not being properly recognized as a tuner.

I ran the steps outlined here first:
[http://ubuntuforums.org/showthread.php?t=460214](http://ubuntuforums.org/showthread.php?t=460214)

I then tried yours and neither to any avail. 

Again, I really do appreciate your help on this. Hopefully we can get it working. *continues google research*

I may attempt to break open the drivers meant for windows for that card and see if i can find any specific instructions within.

**P.S. I am making sure to type sudo tvtime -d /dev/1-1 (it's back to 1-1), thought I'd get that out of the way early.

---

### Post by xc3RnbFO8P on 2008-04-17
At this point I would make a fresh install and use this tread that you found:
[http://ubuntuforums.org/showthread.php?t=460214]("http://ubuntuforums.org/showthread.php?t=460214")
Or this:
[http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices]("http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices")

---

### Post by 4rk3typ3 on 2008-04-19
I probably will, it seems that I'm having several other issues with simple compatibility things on this system and cedega has stopped working altogether. I'll probably download a fresh ISO of Ubuntu and actually do an MD5 check like a good little boy.

---

