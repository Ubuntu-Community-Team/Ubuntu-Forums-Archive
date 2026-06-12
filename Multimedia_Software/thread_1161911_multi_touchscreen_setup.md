---
title: "multi touchscreen setup"
date: 2009-05-17
forum: Multimedia Software
---

### Post by kev000 on 2009-05-17
I'm trying to setup a dual touchscreen setup on my pc.  I'm using the egalax driver found [here]("http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm").  I've got a dual head nvidia 6200 card that powers the two touchscreens.

I can get each of the touchscreens to work individually, but I cannot get them to work together.  The kernel creates 6 devices for the Touchscreens: /dev/input/event*, /dev/hidraw[1-2] and /dev/usb/hiddev[0-1].  Here is my xorg.conf for the egalax settings:

```
Section "InputDevice"
    Identifier     "EETI0"
    Driver         "egalax"
    Option         "Device" "/dev/hidraw1"
    Option         "Parameters" "/var/lib/eeti0.param"
    Option         "ScreenNo" "0"
EndSection

Section "InputDevice"
    Identifier     "EETI1"
    Driver         "egalax"
    Option         "Device" "/dev/hidraw2"
    Option         "Parameters" "/var/lib/eeti1.param"
    Option         "ScreenNo" "1"
EndSection


```

It appears though that even though I specify hidraw1, I see in my Xorg.0.log that it's using /dev/usb/hiddev0 for both devices!!

```
(II) HID Touch Controller @ /dev/usb/hiddev0 
(II) HID Touch Controller @ /dev/usb/hiddev0
```

Thinking I could "trick" the driver, I created a Udev rule to always make the second touchscreen /dev/input/tsfront0.  This caused me to not be able to read from the device.  Before I could `cat /dev/usb/hiddev1` and get input back when I touched the screen.  After the udev rule create the symlink, I get nothing:

```
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="0eef", ATTRS{idProduct}=="0001", KERNELS=="1-1", SYMLINK+="input/tsleft0"
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="0eef", ATTRS{idProduct}=="0001", KERNELS=="1-2", SYMLINK+="input/tsfront0"
```

I can confirm that the symlinks point to the correct device.  Why can't I read from the device from the symlink or the original device????

---

### Post by kev000 on 2009-05-29
Just an update.  I never figured out the udev issue, however the issue with the touchscreen was confirmed as a bug in the X driver.  EETI is working on a fix.

---

