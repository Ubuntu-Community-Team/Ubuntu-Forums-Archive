---
title: "USB Webcam - must unplug and plug after boot up"
date: 2011-02-12
forum: Multimedia Software
---

### Post by lipperreiher on 2011-02-12
Hello together,

I've bought a webcam (logitech C500) which works perfectly well with my ubuntu 10.04 (32bit) except this little problem:

When the Webcam is plugged in while I boot the computer, the cam does not work after boot. Even if the the device "/dev/video0" is apparent and the module uvcvideo is loaded, non of the applications (cheese, mplayer oder vlc) can connect to the webcam (error-message: device is busy(or the like) )

Unplugging and plugging the usb cable solves the problem.

Since I want to use the webcam from remote (for example with motion or zoneminder) it's not really cool if I had to call my wife and ask her to plug the usb cable after boot up ;-)

I'm looking forward to your tips.

Thanx in advance


Olaf

---

### Post by lipperreiher on 2011-02-13
Hello,

I could solve the problem on my own:

1.) Add the line **blacklist uvcvideo** into the file **/etc/modprobe.d/blacklist.conf**
     To prevent that the module is loaded

2.) Add the line **/sbin/modprobe** **uvcvideo** into the file **/etc/rc.local**
     In order to load the module at the end of the boot process.

The reason of the problem seems to be an awkward order of boot and load processes.


Many greetings from Germany


Olaf

---

### Post by SonjaRethel on 2011-03-04
I recently found my webcam on a Samsung Q45 not working.

May be after one of the last updates (I use Ubuntu 10.04 lucid with kernel 2.6.32-29 generic) suddenly cheese stopped working. When I started cheese an app window popped up and after a few seconds disappeared. The only remark in the system log was something like:

Mar  3 16:54:47 mypc kernel: [21346.342110] cheese[6407]: segfault at 0 ip (null) sp b44fbf9c error 4 in libstartup-notification-1.so.0.0.0[110000+7000]

I checked dmesg for the loaded video drivers: there where no errors.

So I blacklisted uvcvideo and put it into rc.local: voila, the cam is working again.

---

### Post by TimJC on 2012-05-01
I'm running 12.04 on an Atom board with a Microsoft Live Vision webcam with Motion in an effort to figure out which DH neighbor is throwing their dead fish bait at my house.

Unfortunately, I have discovered this same issue with needing to unplug and re-plug the webcam after a reboot.  I tried the noted fix, but after rebooting the machine Cheese reports 'no device found,' and Motion reports 'failed to open video device /dev/video0: No such file or directory.'  Is there something wrong with the syntax of files below, or is there a newer fix for this issue with 12.04?

/ect/modprobe.d/blacklist.conf
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

# USB webcam not recognized at boot.  Uvcvideo is blacklisted here
# and /sbin/modeprobe uvcvideo is added to /etc/rc.local
blacklist uvcvideo

```/etc/rc.local
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# USB webcam not recognized at startup.
# Adding blacklist uvcvideo to /etc/modprobe.d/blackblist.conf
# and adding /sbin/modprobe uvcvideo to this file changes the order
# the components are loaded in the startup sequence.
/sbin/modprobe uvcvideo

exit 0
```

---

