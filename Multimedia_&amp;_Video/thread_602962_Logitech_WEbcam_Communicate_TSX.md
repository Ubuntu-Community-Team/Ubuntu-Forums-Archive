---
title: "Logitech WEbcam Communicate TSX"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by aedwards on 2007-11-04
Hey all, I have been running Ubuntu now for 60+ days, really glad to not be giving Mr. Gates any money. ;-)

Anyways, I have everything working except for my webcam.   

I have tried to install the drivers from here: [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

I try using camstream or camorama, both programs give me a device error:  they say: "could not connect to the video device (/dev/video0). Please check connection".

my webcam works fine on Windows.

I am wondering if the device just isn't mountain automatically when I plug it in?  Any suggestions?

---

### Post by daengbo on 2007-11-04
I don't use this webcam, but according to the mxhaard site, you shouldn't need to download any driver at all (I'm assuming the TSX in the title is a typo for STX). The module you need is gspca.

You can also use "module-assistant" to install the spca5xx driver module.

Either one will allow you to access your webcam through V4L.

Good luck.

---

### Post by mrclorets on 2007-11-04
will it work for V4L2? i seem to have problems with V4L in ekiga but once i switched it to V4L2 then my webcam is working. (only thing is its inverted) :(

---

### Post by aedwards on 2007-11-05
The problem is that it doesn't show up in the devide list...  I tried using ikega, nothing comes up using v2l or v2l2.    My computer isn't detecting that my webcam even exists.....

when I connect the device on my usb port, I get the following info written to /var/log/messages:
Nov  5 20:04:57 exto-ub kernel: [105287.552000] usb 1-10: new full speed USB device using ohci_hcd and address 6
Nov  5 20:04:57 exto-ub kernel: [105287.768000] usb 1-10: configuration #1 chosen from 1 choice

Looks like it's picking it up....    however it doesn't appear to be auto-mounting to /dev/video0 (not sure if it's supposed to).   Does anyone know how to mount/unmount the device?

Anyone have any ideas?

Also, I tried installing spca5xx via the module-assistant program and got the following error.....

 &#9474;   CC [M]  /usr/src/modules/spca5xx/drivers/usb/spca5xx.o                   &#8593; 
 &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c:39:26: error:               &#9618; 
 &#9474; linux/config.h: No such file or directory                                  &#9618; 
 &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c: In function                &#9618; 
 &#9474; ‘spca50x_init_isoc’:                                                       &#9618; 
 &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c:1681: warning: assignment   &#9618; 
 &#9474; from incompatible pointer type                                             &#9618; 
 &#9474; make[4]: *** [/usr/src/modules/spca5xx/drivers/usb/spca5xx.o] Error 1      &#9618; 
 &#9474; make[3]: *** [_module_/usr/src/modules/spca5xx] Error 2                    &#9618; 
 &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'      &#9618; 
 &#9474; make[2]: *** [default] Error 2                                             &#9618; 
 &#9474; make[2]: Leaving directory `/usr/src/modules/spca5xx'                      &#9618; 
 &#9474; make[1]: *** [binary-modules] Error 2                                      &#9618; 
 &#9474; make[1]: Leaving directory `/usr/src/modules/spca5xx'                      &#9646; 
 &#9474; make: *** [kdist_build] Error 2

---

### Post by Radon on 2007-11-06
There was recently a thread [ here]("http://ubuntuforums.org/showthread.php?p=3715836") with regard to the STX.  See if it works for you.  Most importantly, did you restart after installing the kernel module?  You don't have to worry about mounting anything, it's USB.  Open the folder /dev and see if your webcam gets recognised as video0 upon plugging/unplugging.  Works fine for me.

Spca5xx is good, but it has been outdated by gspca which is V4L2 and has been integrated into Ubuntu since 7.04.  Otherweise try messing about with the [source]("http://packages.ubuntu.com/gutsy/graphics/gspca-source").
Good luck!

---

### Post by frodon on 2007-11-06
I have the same webcam, it is recognized out of the box and is working greatly with ekiga, amsn and kopete.
It just worked out of the box.

---

### Post by aedwards on 2007-11-20
yup, rebooted, upgraded to Gutsy Gibbon and all..

Still doesn't work... argh.   Wish someone knew how to fix this. :-(

---

### Post by frodon on 2007-11-20
I think you should try first to unsinstall the drivers you installed then reinstall the correponding drivers from the repositories because this web cam (i own it too) is recognized out of the box by the gspca drivers which are included by default in ubuntu.

---

### Post by saxmanwwjd on 2008-05-20
Have you tried to do an lsusb to see if your webcam is recognized by the OS.I am using a Logitech, Inc. QuickCam Connect which does work in Ikega.  I don't know if I can use it with MSN yet but I am going to try to get it working.  lsusb ouput

Bus 002 Device 002: ID 046d:08d9 Logitech, Inc. QuickCam Connect
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000

---

### Post by meinv on 2008-06-01
Hi,

I have the same camera, it works out of the box with ubuntu 8.04 (and at least 7.10 if my memory serves me well).

There is a catch though!

The driver has an extreme distaste for USB hubs. Connect the camera to a usb port directly on your computer and you should be good to go.

My set-up includes a Dell monitor with integral USB hub and my Quickcam STX will work without a problem with Windows, but will not work with Linux, when connected to that hub. If I connect it directly to the PC USB ports, the problem is instantly solved. It is an annoyance, that I hope will be fixed, but at least there is a workaround.

Hope that helps...

---

### Post by rob09 on 2008-06-13
i have the same camera and 8.04. I can't get the mic to work, don't have a clue found out going through setup for aMSN. then i went to sound recorder and it wont record either.

---

