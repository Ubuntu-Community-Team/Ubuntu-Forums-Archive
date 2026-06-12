---
title: "[SOLVED] Acer CrystalEye Webcam problems"
date: 2008-10-05
forum: Multimedia Software
---

### Post by FokkerCharlie on 2008-10-05
Hello!

I have a (fairly) new Acer Aspire 5920G laptop, which includes a built-in webcam.  It doesn't work properly- when starting the camera using Ekiga or Cheese or luvcview, initially all looks well.  However, after a few seconds (usually between 5 and 20) the camera stops, with the window displaying a corrupted image.

Some more info:

```
cat /proc/bus/usb/devices

T:  Bus=06 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(unk. ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=064e ProdID=a101 Rev= 1.00
S:  Manufacturer=SuYin
S:  Product=Acer CrystalEye webcam
S:  SerialNumber=CN0314-OV03-VA-R02.00.00
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
A:  FirstIf#= 0 IfCount= 2 Cls=0e(video) Sub=03 Prot=00
I:* If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
E:  Ad=83(I) Atr=03(Int.) MxPS=  16 Ivl=4ms
I:* If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 1 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS= 128 Ivl=125us
I:  If#= 1 Alt= 2 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS= 256 Ivl=125us
I:  If#= 1 Alt= 3 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS= 800 Ivl=125us
I:  If#= 1 Alt= 4 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=1600 Ivl=125us
I:  If#= 1 Alt= 5 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=2400 Ivl=125us
I:  If#= 1 Alt= 6 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=3000 Ivl=125us

```

After the device stops working:

```
dmesg

[  521.251212] uvcvideo: Failed to resubmit video URB (-45).
[  521.251229] uvcvideo: Failed to resubmit video URB (-45).
[  521.251240] uvcvideo: Failed to resubmit video URB (-45).
[  521.251249] uvcvideo: Failed to resubmit video URB (-45).

```

Whichever app I am viewing the webcam with also crashes, and I have to 'Force Quit'.

Any ideas?  New driver, maybe?  This is quite a common laptop, and the model of webcam is failry widespread, too.

Do I file a bug for this one?

Cheers
Charlie

---

### Post by FokkerCharlie on 2008-10-06
Anyone?  Happened on my previous, similar 5920, too.

Go on!
Charlie

---

### Post by FokkerCharlie on 2008-10-12
OK, I found a fix here:

[http://www.niftiestsoftware.com/?p=30#comment-442](http://www.niftiestsoftware.com/?p=30#comment-442)

This works for me- except for having to run:

```
sudo rmmod ehci-hcd
sudo modprobe ehci-hcd

```

Before using the webcam every time.  I don't know how to add this to a script to start in 'Sessions', as it's sudo, and running these commands sometimes break my usb mouse!  So we're getting there, but slowly....

Hopefully Intrepid will fix this and the webcam will work out of the box.

Cheerio
Charlie

---

### Post by FokkerCharlie on 2008-10-12
Ah-ha!
That's better.  Forget putting anything in sessions, do this instead:

```
gksudo gedit /etc/rcS.d/S99webcam.sh
```

Put this in the file:

```
#!/bin/sh
rmmod ehci-hcd
modprobe ehci-hcd
```

And save.  Navigate (as root) to /etc/rcS.d, and change the properties of the script you just created- go to the 'Permissions' tab and make those match the other files in that folder- particularly 'Allow executing file as program'.

I don't know if this is the smartest way of doing things, but it works OK for me.

Cheerio
Charlie

---

