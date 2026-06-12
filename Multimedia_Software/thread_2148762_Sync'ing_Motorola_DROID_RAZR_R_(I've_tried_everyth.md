---
title: "Sync'ing Motorola DROID RAZR R (I've tried everything I could find)"
date: 2013-05-26
forum: Multimedia Software
---

### Post by duranl on 2013-05-26
I'm trying to get Rhythmbox to be able to sync with my Motorola DROID RAZR M for about 8 hours.  My phone is set on MTP mode.  So far, all I get are errors.  Here's what I have tried followed by where I get stuck.[URL="http://www.mysolutions.it/mounting-your-mtp-androids-sd-card-on-ubuntu/"]

[/URL][http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html](http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html)

> ThinkCentre-M52:~$ go-mtpfs /media/MyAndroid2013/05/26 12:20:59 compiled against libmtp 1.1.5
Device 0 (VID=22b8 and PID=710f) is a Motorola XT890/907 (MTP+?).
2013/05/26 12:20:59 found device Motorola: XT890/907 (MTP+?) (22b8:710f) @ bus 1, dev 7
: 
LIBMTP PANIC: Unable to find interface & endpoints of device
2013/05/26 12:20:59 rdev.open failed: open: open returned nil



[http://www.mysolutions.it/mounting-your-mtp-androids-sd-card-on-ubuntu/](http://www.mysolutions.it/mounting-your-mtp-androids-sd-card-on-ubuntu/)

> ThinkCentre-M52:~$ sudo mtpfs -o allow_other /media/MTPdeviceUnable to open ~/.mtpz-data for reading, MTPZ disabled.Listing raw device(s)
Device 0 (VID=22b8 and PID=710f) is a Motorola XT890/907 (MTP+?).
   Found 1 device(s):
   Motorola: XT890/907 (MTP+?) (22b8:710f) @ bus 1, dev 7
Attempting to connect device
LIBMTP PANIC: Unable to find interface & endpoints of device
Unable to open raw device 0


[http://bernaerts.dyndns.org/linux/268-ubuntu-automount-any-mtp-device#h4-one-click-automatic-script](http://bernaerts.dyndns.org/linux/268-ubuntu-automount-any-mtp-device#h4-one-click-automatic-script)

> ThinkCentre-M52:~$ sudo mtp-declare
tee: /sys/bus/pci/drivers/ehci_hcd/unbind: No such file or directory
tee: /sys/bus/pci/drivers/ehci_hcd/bind: No such file or directory
 ^ This comes up on Step 6 "Device detection" on the terminal and the orange bar just goes back and forth forever.  It also won't let me cancel out.

[http://forum.xda-developers.com/showthread.php?t=2223401](http://forum.xda-developers.com/showthread.php?t=2223401)

> [COLOR=#222225][FONT=Arial]Add the udev rules:[/FONT][/COLOR]

[COLOR=#222225][FONT=Arial]This is the core of making the auto mounting work. The first link I reference has all the information on how you discover the Vendor and Product ids. While it is interesting reading, I have just skipped over all that and supplied the TF700 specific values. If you are trying to setup another device you WILL NEED TO read it and get the appropriate values, as they are device specific.[/FONT][/COLOR]
 ^ I don't know what the hell to do from here on out.  Instructions aren't clear enough or I'm too stupid.

Has anyone gotten this to work?!  I'm going crazy here.



_System_
Ubuntu 13.04 Gnome 3.8
Intel Pentium D 2.99 GHz (Dual core)
RAM 4GB (3GB usuable because of motherboard limit)



Update: Also tried this one out.

[http://blog.itsbilal.com/2012/12/connect-an-android-4-0-phonetablet-to-ubuntu-the-reliable-way/](http://blog.itsbilal.com/2012/12/connect-an-android-4-0-phonetablet-to-ubuntu-the-reliable-way/)
> ThinkCentre-M52:~$ go-mtpfs ~/MyAndroid &
[1] 4573
duranl@duranl-ThinkCentre-M52:~$ 2013/05/26 12:51:04 detect failed: no MTP devices found


---

