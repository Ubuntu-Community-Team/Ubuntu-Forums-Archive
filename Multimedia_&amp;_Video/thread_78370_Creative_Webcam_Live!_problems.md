---
title: "Creative Webcam Live! problems"
date: 2005-10-18
forum: Multimedia &amp; Video
---

### Post by zarathustra on 2005-10-18
I think I've managed to get working drivers installed, but it still won't run (so I don't really know if they're working). I get errors like this:

> nick@kitsune:~/downloads/spca5xx-20050906$ gqcam
/dev/video: No such file or directory


Completely stuck and no idea what to do.

---

### Post by az on 2005-10-18
In Hoary, I had to compile the driver by hand, change the X configuratin to enable v4l and make a symlink from /dev/video0 to /dev/video for it to work.

I have not tried a webcam in Breezy, yet.  I know that the spca5xx dirver is included in the kernel, so you do not have to compile it (if that is your webcam's driver)

---

### Post by zarathustra on 2005-10-18
I did a bit of searching before posting this, and there was talking of the default driver being faulty. I followed instructions to compile a new driver, although still having problems. I shall try what you've suggested though, thanks.

---

### Post by zarathustra on 2005-10-18
Hmm, things are getting weird now.

> nick@kitsune:/dev$ gqcam
/dev/video: No space left on device


Not a reply I'm expecting for a webcam!

---

### Post by zarathustra on 2005-10-18
It's also removing the symlink I create every time I reboot.

---

### Post by az on 2005-10-18
file://usr/share/doc/udev/writing_udev_rules/index.html


You need to make a udev rule for it since the udev devices are created on each boot.

---

### Post by zarathustra on 2005-10-18
I compiled spcaview to test it without fiddling with symlinks for the minute and this is the error I get:

> nick@kitsune:~/downloads/spcaview-20051001$ spcaview
 Spcaview version: 1.1.1 date: 01:10:2005 (C) [email]mxhaard@magic.fr[/email]
Initializing SDL.
SDL initialized.
bpp 3 format 15
Using video device /dev/video0.
Initializing v4l.
ERROR opening V4L interface
: No space left on device


I don't understand the "no space left on device". What is it trying to do?

---

### Post by zarathustra on 2005-10-18
I've also managed to created a symlink with udev (another thing learnt on my journey through Linux).

---

### Post by zarathustra on 2005-10-18
Can't anyone help?

---

### Post by kerinin on 2005-12-01
*bump*

i'm having the same problem...

---

### Post by hunteramor on 2005-12-07
try unplugging all other USB devices.

that solves my "no space left on device" problem.  of course, i just run into another problem immediately thereafter  ;)  but it might solve it for you

---

### Post by bandi13 on 2006-01-08
haha! Now I understand what "other problems" you speak of. I get the following problem:

andras@bandi:~$ webcam
reading config file: /home/andras/.webcamrc
v4l2: open /dev/video0: No space left on device
v4l2: open /dev/video0: No space left on device
v4l: open /dev/video0: No space left on device
no grabber device available

When I unplug all the other USB devices and run it again, the whole system crashes. In these times of despair, you managed to get a chuckle out of me.
-Andras

---

### Post by bandi13 on 2006-01-08
Ha! I figured it out! The reason it locked up my system is because the driver that comes with the kernel is compiled with gcc-4.0. All I needed to do was download the driver from [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) and recompile the driver using gcc-3.4, unload and remove bad drivers. Do a make install and modprobe spca5xx. One trick I did was when I first started gnomemeeting, I unpluged all my USB devices except the camera. It worked and everything, then I plugged back my other USB stuff, and the camera continued to work.

---

### Post by chele on 2006-01-14
EasyCam [https://wiki.ubuntu.com/Webcam]("https://wiki.ubuntu.com/Webcam") is a cool utility to update, download and build drivers for many webcams.

---

### Post by jbraum on 2006-01-14
I used the code from this post [http://www.ubuntuforums.org/showthread.php?t=75284&highlight=webcam](http://www.ubuntuforums.org/showthread.php?t=75284&highlight=webcam) and got my creative camera to work with no problems

Good luck

---

### Post by lnxpwr on 2006-01-17
spca5xx is included in breezy....but FAULTY !!!
I had the same problems like you with a Trust Spacecam150 and have done the following:
-downloaded spca5xx driver
-switched to superuser
-export cc=gcc-3.4
-export CC=gcc-3.4
-unpacked the driver and changed to its directory
-make clean
-make
-make install
-switched to /lib/modules/<your version>/kernel/drivers/usb/media/
-deleted the file spca5xx.ko and also the same file in the folder spca5xx
-copied the new spca5xx.ko I downloaded to both locations
-rmmod spca5xx
-modprobe spca5xx
 
that's all I've done and it works !

---

### Post by vodunvibe on 2006-08-31
> **zarathustra said:**
> I compiled spcaview to test it without fiddling with symlinks for the minute and this is the error I get:



I don't understand the "no space left on device". What is it trying to do?


Hi,

When other USB devices are present on the same host controller bus as the camera, the bandwidth requirements of the spca5xx driver are not being met, with some hardware configurations.
The spca5xx driver is asking for more bandwidth than is available which results in the following error messages:

No space left on device
can't open /dev/video0: No space left on device.

Please take a look at this howto. I hope that it helps you resolve your issues.
[http://www.ubuntuforums.org/showthread.php?t=247646](http://www.ubuntuforums.org/showthread.php?t=247646)

---

### Post by tripmix on 2006-09-01
I followed vodunvibes howto whit no luck. I cant understand this. The camera allways goes on bus 001 and my usbdisk allways goes on 002. It seems there is no difference in what plug I put them inn. 

I tried the modifed drivers from the how to but still get the same "/dev/video1: No space left on device"
I compiled the driver on a custom kernel built whit gcc4.0, I asumed the other gcc in the howto was for ubuntu only.

I'm not exacly sure what a usb bus is but I got 2 extra usb brackets plugged in to my motherboard and lsusb gives me:

Bus 001 Device 023: ID 046d:08ad Logitech, Inc.
Bus 001 Device 017: ID 044f:b322 ThrustMaster, Inc.
Bus 001 Device 016: ID 06a3:a501 Saitek PLC
Bus 001 Device 013: ID 06a3:8020 Saitek PLC
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 019: ID 1058:0201 Western Digital Technologies, Inc.
Bus 002 Device 001: ID 0000:0000

I got no errors or anything when compileing the modified driver.

I'm on Debian etch kernel 2.6.16 amd64 smp, if that makes any difference.

Hope someone here can help.

---

### Post by scorptig on 2007-09-25
I have had no success for Configuring Creative Live Ultra Webcam, on Ubuntu 7.04 Edgy Eft,
somewhere it said it should work with Edgy, because the Webcam source is included. Sorry I tried Everything, and it boils down to modprobe not working, your instructions Well they cover a few various Ubuntu's, but they lead people to Give Up, because the postings are outdated.

So I am re-installing Ubuntu 7.04, and I hope at some point someone Knows how to configure
a webcam for Ubuntu 7.04

I just need instructions which are UP to DATE, today is Tuesday September 25th, 2007.

Thank You in advance, I'll have another issue  to post Wireless  separately.

---

