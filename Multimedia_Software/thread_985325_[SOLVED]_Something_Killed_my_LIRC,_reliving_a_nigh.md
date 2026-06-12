---
title: "[SOLVED] Something Killed my LIRC, reliving a nightmare"
date: 2008-11-17
forum: Multimedia Software
---

### Post by laceration on 2008-11-17
I had an awful time installing LIRC as I posted about in [http://ubuntuforums.org/showthread.php?t=929009](http://ubuntuforums.org/showthread.php?t=929009)

I finally figured out that my mainstream pinnacle remote and usb reciever weren't even supported until I got a hold of a new shiney lirc_dev driver in the CVS.  It has worked great for about a month and a half but has just stopped working for no apparent reason.  It seems as if the kernel does not recognize the module.  It is not loaded at boot.
```
modprobe lirc_dev
modprobe lirc_mceusb2
```
loads them, but the driver does not get attached to the device
```
cat /proc/bus/usb/devices
...T:  Bus=01 Lev=01 Prnt=01 Port=09 Cnt=03 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=2304 ProdID=0225 Rev= 0.01
S:  Manufacturer=Pinnacle Systems
S:  Product=PCTV Remote USB
S:  SerialNumber=7FFFFFFFFFFFFFFF
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 [COLOR="Red"]Driver=(none)[/COLOR]
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
```
should be driver=mceusb2

and
```
ls /dev/lirc*
/dev/lircd
```
/dev/lirc0 should be there too.

I recompiled lirc hoping it would repair, it didn't.  I went to the lirc source and got lirc_dev.c 1.61 (had 1.6) and lirc_mceusb2.c 1.53 (had 1.5) and compiled again, didn't fix it.

What might have broke it?  I plugged in a usb printer and printed some stuff just before this happened.  Could this have done something?  I also may have rebooted for the first time in awhile. What are all those linux-header files that are always in the updates?  Could one of these have affected the way modules are loaded?  I am clueless.

I am still on 8.04 and am developing a strong fear of updates.

---

### Post by laceration on 2008-11-19
Hello out there!  What would cause a module not to be recognized or loaded, when it previously was?
Should I go through all the updates over the last couple of weeks and undo them if they look suspicious?  How would you do that?
Could some kind of usb conflict play a part?  I see there is the usbcore driver that seems to work with usb devices.

---

### Post by cariboo on 2008-11-19
What did you change between the time it was working and when it stopped working?

Jim

---

### Post by laceration on 2008-11-19
Hi Jim, thank you for answering.  That is the $64 question.  As I mentioned I plugged some usb in and out.  That doesn't seem too likely to me, that's all I can think of.  I am always messing around with software, but haven't done anything with modules, unless it was in the update manager.  I removed my old linux images.  I added a couple of memory sticks lately--that was done before the lirc problem.  I considered a hardware malfunction, but its all there, the lights come on and the driver=none would indicate that's not the problem.  I'm racking my brain.

---

### Post by laceration on 2008-11-29
Hello anybody.  Today there was an update of linux-headers.  I thought there was an outside possibility that would fix my problem.  It didn't.  My current thinking is that a prior linux-headers update changed the kernal's ability to load the modules that make my remote work.  I am no expert, am I off the wall here?  What if I went into synaptic and removed all but the oldest linux-headers-2.6.24-** and linux-headers-2.6.24-**-generic to test this?  Would it be safe?  Today's were 22, I have back to 19 installed.

---

### Post by laceration on 2008-12-10
For the benefit of anyone who stumbles here in the future, who this may help, I finally figured out my problem.

First I tried booting into an older kernel.  This totally messed up my whole computer.  Apparently you do not have the option of booting into older kernel if you have the propriety nvidia driver.  It was frustrating to have mop up that mess and not make any progress.

I then went about learning how drivers work in Linux and honed in on dkms - Dynamic Kernel Module Support.  I had needed a bleeding edge cvs version of lirc to make hardware work and compiled from source.  I did not use dkms to install my modules.  Lirc was working and I didn't really understand the significance of dkms.  When the kernel was upgraded my lirc was broken.  dkms is is precisely what maintains your modules across kernel upgrades--I'm pretty sure of that.

(A small primer here:  Your kernel contains the instructions or code to interface with your hardware.  For the kernel to support all the hardware out there would necessitate a gargantuan kernel.  That's where modules come in.  A module is code you can add to your kernel to support some hardware you specifically have, like a remote receiver for lirc.)

It was pretty hard to wrap my head around the dkms manpage, so I procrastinated on this for awhile.  Finally from the back of my mind I remembered this post, which is the very last post of one of the most useful lirc threads ever:

[http://ubuntuforums.org/showthread.php?p=5126843#post5126843](http://ubuntuforums.org/showthread.php?p=5126843#post5126843)

I followed those instructions to install my modules with dkms and :p my remote works!!

---

