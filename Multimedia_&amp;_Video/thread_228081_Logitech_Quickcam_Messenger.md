---
title: "Logitech Quickcam Messenger"
date: 2006-08-02
forum: Multimedia &amp; Video
---

### Post by Nicole on 2006-08-02
Hi,

I'm fairly new to Linux (am currently running dapper), and am really learning what I'm doing as I go along, so please be patient with me! I need some help though, with my webcam. I've managed to install webcam drivers which say they are for logitech cams (on the basis that the more the merrier, I've installed a couple). The problem I have is not, for once, installing things - it's getting my computer to recognise that the webcam exists at all.

When I type lsusb in a terminal, I get:

Bus 003 Device 001: ID 0000:0000
Bus 001 Device 005: ID 046d:08da Logitech, Inc.
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

which would seem to imply that the USB port recognises that it has something in it, but none of the webcam software like camorama or xawtv recognises that my cam exists, and the light on the top of the cam (which I assume is a power light; it's apparently called an 'activity LED') lights up very briefly when I first plug it in, and then never comes on again.

Any ideas? If you need any more information from me, do let me know - like I said, I'm new to all of this!

Thank you very much for any help you can give me!

N

---

### Post by louis_nichols on 2006-08-02
well... what kind of Logitech is it exactly? and what drivers did you install?

what's the output when you type in terminal

```
lsmod | grep spca
```

having the webcam plugged?

---

### Post by Nicole on 2006-08-02
Thanks for replying.

It's a Logitech Quickcam Messenger, and I've installed the Philips USB Webcam driver for Linux from [http://www.saillard.org/linux/pwc/](http://www.saillard.org/linux/pwc/) as well as following the steps in the howto from these forums which I now can't find (typical!), but is essentially the same as:
[http://www.ubuntuforums.org/showthread.php?t=191770](http://www.ubuntuforums.org/showthread.php?t=191770) but for Dapper, not Breezy.

Typing "lsmod | grep spca" doesn't give any output at all, whether the cam is plugged in or not. 

I'm beginning to just think I should give up and live without a webcam - it won't kill me, after all - at least til I learn more about what I'm doing! I tried doing it the easy way, using EasyCam2 from [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam) - but it says I don't have a cam plugged in. I might just assume that the cam doesn't work (at least until I can try it on someone else's computer) and that would make me feel less incompetent!

---

### Post by louis_nichols on 2006-08-03
I don't think you need to change the webcam. I have a Logitech Quickcam Chat and it works just fine under Linux. The driver needed for this is called [spca5xx]("http://mxhaard.free.fr/spca5xx.html") (you'll find your webcam in the supported cameras list), which is already included with Ubuntu, so you really didn't need to install anything else. For some reason, though, it doesn't load.

Try this: with the camera plugged, issue in terminal the commmand

```
sudo modprobe spca5xx
```

and then try to see if the camera is working with some app (I just use ekiga softphone, which is included in the default Ubuntu install). I think you can also uninstall any other driver you installed for this purpose, and it's probably the thing to do, to avoid conflicts.

---

### Post by louis_nichols on 2006-08-03
actually... ... ... ... ... ...

I just read on the spca5xx page and noticed that Logitech QuickCam Messenger was only added in the last release:

Release 0.60.00 Date:1 May 2006

I actually know no way to test which version of a certain module is installed on the machine, but if it doesn't work, you'll just have to compile it, which is a simple enough job and there are howto's for that. But we'll get to that only if we need to.

---

### Post by Nicole on 2006-08-03
Thanks for your patience - sadly, ekiga doesn't recognise that the cam exists, even after typing "sudo modprobe spca5xx" like you suggested. 

Would compiling the module help? If so, do you know where I can find help with doing that? (Also, while I've worked out how to install stuff, I'm less clear on how to uninstall stuff - is it just a matter of deleting the files I installed?)

Thanks again for your help with all this!

N

---

### Post by louis_nichols on 2006-08-04
let's start with uninstalling. it depends on the method you used to install stuff. there are many ways. I suspect you used the "make + make install" way, which just means you have to go back and issue te command "make uninstall" (although it doesn't always work, but most of times). Generally, it is indeed just a matter of deleting installed files and perhaps modifying some configuration files to a previous state. It's not doable by hand, though.

as for compiling the driver, follow the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=75284&highlight=spca5xx"). It says they're for breezy, but they should work.

then, try the webcam again with a software of your choosing. good luck! and please get back to us with the results.

EDIT: correction. it seems arnieboy made 2 separate methods, one of which is for dapper. :)

---

### Post by Nicole on 2006-08-04
Fantastic - compiling it, following that howto, made it work! That's made my week that - it's been a bad week, but still - thank you so much for your help!

N

---

### Post by louis_nichols on 2006-08-04
great! =D>  enjoy! :)

now, in case you didn't know already, kopete will let you use it with yahoo and msn messenger buddies. :)

---

### Post by easyease on 2006-09-24
thanks! this thread helped me to with exactly the same problem.

---

### Post by Gkil on 2006-11-13
I have tried following this thread having similar equiptment but the quickcam messenger is not found in /dev/video0 by camorama, kopote, or aMsn. Please help.

root@Gkil-home:/spca5xx-20060501# lsmod | grep spca
spca5xx               679888  0 
videodev               10752  1 spca5xx
usbcore               134912  8 spca5xx,usb_storage,libusual,snd_usb_audio,snd_usb_lib,ehci_hcd,uhci_hcd
root@Gkil-home:/spca5xx-20060501# lsusb

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:08f6 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
root@Gkil-home:/spca5xx-20060501# 

Any Help at all would be great. Thanks.

](*,)

---

