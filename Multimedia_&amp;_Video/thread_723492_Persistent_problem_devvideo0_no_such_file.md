---
title: "Persistent problem: /dev/video0: no such file"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by EdgardL on 2008-03-13
I don't get a /dev/vid* for my webcam, whatever I try.

I am working on the following platform:
Medion laptop (Intel Pentium M processor) / Ubuntu 7.10
(installed in dual boot with Windows XP)

I bought me a Logitech QuickCam for Notebooks, which is one of the
webcams supposed to work under Ubuntu Linux - see:
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech")

The webcam is okay (verified under Windows).

As the documentation of the webcam mentions that one should
"... not plug in your device until installation is completed",
I decided not to try the webcam without installing the drivers (maybe,
by doing this I corrupted a good functioning driver that was already
present on my system).
Anyway ... I [COLOR="Red"]un[/COLOR]successfully tried to install/compile the
source packages of the driver: gspca and spca5xx (apt-get ...etc).
In the mean time, I bumped into a (Spanish) web page
([http://mmejiav.wordpress.com/2007/06/07/modulo-gspca/]("http://mmejiav.wordpress.com/2007/06/07/modulo-gspca/")
that explaines that the only way proceed correctly is to use the latest
version of the driver, available from the author's website
([http://mxhaard.free.fr/download.html]("http://mxhaard.free.fr/download.html"))

Here is the procedure that I followed:

I cleaned all remainings of my previous experiments by invoking
"sudo make uninstall; sudo make clean;" in
all gspca/spca5xx related installation directories and I
removed the directories and the sources. Also I made
sure that no gspca module is present at start of the experiment:

```
$ sudo rmmod -v  gspca
rmmod gspca, wait=no

```

Experiment to check visibility of the usb connection:
I connected the camera and:

```
$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0a5c:2101 Broadcom Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 010: ID 046d:08dd Logitech, Inc. 
Bus 001 Device 004: ID 0d62:a100 Darfon Electronics Corp. Benq Mouse
Bus 001 Device 001: ID 0000:0000

```

Conclusion: the camera when connected is clearly visible as the "Logitech, Inc." device

I downloaded gspcav1-20071224.tar.gz from website [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html),
transferred this file to /usr/src/modules and executed the following commands:

```
$ cd /usr/src/modules
$ sudo tar xzvf gspcav1-20071224.tar.gz
$ cd gspcav1-20071224

```

There, the READ_AND_INSTALL file tells me to invoke

```
$ sudo ./gspca_build
```

The output of the whole compilation and installation procedure
looks okay to me:

```

REMOVE the old module if present
ERROR: Module gspca does not exist in /proc/modules

 CLEAN gspca source tree
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
        .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
        *.symvers *.err

 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
/sbin/depmod -ae

 LOAD gspca in memory 

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err 
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/modules/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /usr/src/modules/gspcav1-20071224/gspca_core.o
  CC [M]  /usr/src/modules/gspcav1-20071224/decoder/gspcadecoder.o
  LD [M]  /usr/src/modules/gspcav1-20071224/gspca.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/src/modules/gspcav1-20071224/gspca.mod.o
  LD [M]  /usr/src/modules/gspcav1-20071224/gspca.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'



 REMOVE the old module if present
ERROR: Module gspca does not exist in /proc/modules

 CLEAN gspca source tree
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
        .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
        *.symvers *.err

 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
/sbin/depmod -ae

 LOAD gspca in memory 

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err 
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/modules/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /usr/src/modules/gspcav1-20071224/gspca_core.o
  CC [M]  /usr/src/modules/gspcav1-20071224/decoder/gspcadecoder.o
  LD [M]  /usr/src/modules/gspcav1-20071224/gspca.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/src/modules/gspcav1-20071224/gspca.mod.o
  LD [M]  /usr/src/modules/gspcav1-20071224/gspca.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'

```

I verify whether the gspca module is loaded:

```
$  lsmod |grep gspca
gspca                 608336  0 
videodev               29312  1 gspca
usbcore               138632  8 gspca,snd_usb_audio,snd_usb_lib,hci_usb,usbhid,ehci_hcd,uhci_hcd

```

This still looks okay, doesn't it?

... but here we arrive at our problem:
I verify what happens when I plug in me webcam, looking at the kernels's log file, so I
call...

```
$ sudo tail -f -n0 /var/log/messages
```

..., I plug in my webcam and these are the (only) messages I get:

```
Mar 11 21:07:35 edgard-laptop kernel: [22608.488000] usb 2-1: new full speed USB device using uhci_hcd and address 2
Mar 11 21:07:35 edgard-laptop kernel: [22608.732000] usb 2-1: configuration #1 chosen from 1 choice
```

Normally the messages should mention the presence of a video device and an audio input
device (the microphone of the camera)
I look for the /dev/vid* device(s) (with the camera plugged in):
```

$  ls /dev/vid*
ls: /dev/vid*: No such file or directory
```

Atfer that, I have tried to solve the problem by rebooting, with and without the camera
plugged in, I even added gspca to the list of drivers to be loaded at boot time
(file /etc/modules)... etc... but the /dev/vid* device is still invisible, while it seems supposed
to appear whenever the webcam is plugged in

Can someone give me a clue how to solve my problem? (I already spent many hours to it).

---

### Post by stmiller on 2008-04-04
Could need a different driver. Check the exact model number, and revision number of the device and make sure it checks out ok as being supported.

---

