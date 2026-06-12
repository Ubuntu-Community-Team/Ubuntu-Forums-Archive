---
title: "Logitech Quickcam Fusion?  UVC not working?"
date: 2006-11-24
forum: Multimedia &amp; Video
---

### Post by rainbowjoshua on 2006-11-24
Hello!

Okay, I have just gotten a "Logitech Quickcam Fusion".  I installed the UVC driver with no errors, but still get no video, when I plug it in, I get the following in the dmesg:

```

[17203984.592000] usb 3-2: new high speed USB device using ehci_hcd and address 5
[17203984.912000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c1)
[17203985.932000] 5:3:1: cannot set freq 0 to ep 0x86
[17203986.932000] 5:3:2: cannot set freq 0 to ep 0x86

```

Any help would be appreciated.  Thank you!
Joshua

---

### Post by cokelid on 2006-11-26
What did you do exactly when you "installed the UVC driver"?

Cheers,

Justin

---

### Post by rainbowjoshua on 2006-11-27
Well, I downloaded the newest version from [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) noting that it IS in the supported list.  and did "sudo make install" which went off without a hitch once I had all the required dependencies installed.  Then I did "modprobe uvcvideo" and again no errors.

Thanks, hoping for ideas!
Joshua

---

### Post by rainbowjoshua on 2006-11-27
I just rain "sudo modprobe uvcvideo" again and unplugged it and plugged it back in and got two extra lines in the dmesg than I got before.  Here is my output:

```
[17277561.620000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c1)
[17277562.220000] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -110.
[17277562.220000] uvcvideo: Failed to initialize the device (-5).
[17277563.220000] 5:3:1: cannot set freq 0 to ep 0x86
[17277564.220000] 5:3:2: cannot set freq 0 to ep 0x86

```

---

### Post by amwg16 on 2006-12-08
Same here!!! I installed the UVC drivers and when I dmesg i get the same thing:

> [17245182.332000] usb 4-1: new high speed USB device using ehci_hcd and address 6
[17245182.640000] usb 4-1: configuration #1 chosen from 1 choice
[17245182.640000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c1)
[17245183.656000] 6:3:1: cannot set freq 0 to ep 0x86
[17245184.656000] 6:3:2: cannot set freq 0 to ep 0x86
[17245185.660000] 6:3:3: cannot get freq at ep 0x86

Any help??? Really want to get this working, last piece of hardware on my system that doesn't work on Ubuntu. Everything else is flawless .....

---

### Post by rainbowjoshua on 2006-12-11
So, I have made some progress.  I tried for a while to get the debian package of uvc-video-source, but couldn't get it to compile.  The svn version compiles perefectly, and after doing finally I have a video device in existence, and Ekiga sees it, but it still doesn't work.  In dmesg I get:

```
[17179783.108000] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
```

I don't know what to try, and am not finding any new information anywhere on the web.  Please, if anyone has any clues or ideas, please do share!

Cheers!
Joshua

---

### Post by [Jen0] on 2007-01-09
Hi Joshua,

I got the same problem and I would like to ask if you have found any solution.

Thanks,

J.

---

### Post by cbrese on 2007-01-21
I just got the QuickCam for Notebook sPro working with the uvc driver.

The trick for me was to add trace=15 as a modprob param

So far the webcam is only working in Ekiga, I'm still trying to get it to work with Kopete.

Here are the steps i used:

```
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4 subversion
mkdir uvcdriver
cd uvcdriver
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
sudo modprobe uvcvideo trace=15

```

---

### Post by Vantskruv on 2007-06-26
Thanks cbrese!

That made my Quickcam Fusion work in Ekiga. No let's see if it's working in other applications.

Thanks again!

/Johannes

---

### Post by vinzan on 2008-01-14
Did someone got his/her webcam working under Kopete ?
The problems I have are:
   - very bad quality of image (on Windows it looks like a REAL resolution but under Kubuntu it's awefull)
   - the image seems truncated (showing only the left part ! not things just in front of the webcam)
   - i tried to test a video conference with Kopete and people under MSN, they can't have my cam also i see a window with the video capture of me....
Thanks for your help

---

