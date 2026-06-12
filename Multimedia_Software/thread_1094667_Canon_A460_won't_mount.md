---
title: "Canon A460 won't mount"
date: 2009-03-12
forum: Multimedia Software
---

### Post by oygle on 2009-03-12
Have a Canon A460 digital camera, and it used to mount okay, but now it doesn't mount. I think this may be a KDE bug ?

I need to access the camera as a 'device', just as it used to do before, so it needs to be mounted.

When I turn the power on, the system logs show

> syslog

Mar 13 11:53:55  kernel: [  954.164059] usb 4-2: new full speed USB device using uhci_hcd and address 2
Mar 13 11:53:55  kernel: [  954.361673] usb 4-2: configuration #1 chosen from 1 choice
Mar 13 11:53:57  chipcardd[5722]: devicemanager.c: 3373: Changes in hardware list

messages

Mar 13 11:53:55  kernel: [  954.164059] usb 4-2: new full speed USB device using uhci_hcd and address 2
Mar 13 11:53:55  kernel: [  954.361673] usb 4-2: configuration #1 chosen from 1 choice

kern.log

Mar 13 11:53:55  kernel: [  954.164059] usb 4-2: new full speed USB device using uhci_hcd and address 2
Mar 13 11:53:55  kernel: [  954.361673] usb 4-2: configuration #1 chosen from 1 choice


and the output from lsusb is ..

> 
# lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04a9:3149 Canon, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


and the device doesn't show in the mount command

I'm using Intrepid with all updates applied, and KDE Version 4.1.4 (KDE 4.1.4)

Nautilus and Konqueror show the camera as:

Location:   gphoto2://[usb:004,002]/
Volume:     Canon, Inc. Canon Digital Camera

It is not shown under the /media folder.

How can I get this device to mount ?

Oygle

---

### Post by oygle on 2009-03-13
Is this a DigiKam problem, or a KDE problem ?

Why can I plug in a USB memory stick, and it is immediately recognised, and appears in /media ?

---

### Post by oygle on 2009-03-16
I even tried gphotofs, but still can't see the pics on the camera ?

---

### Post by xc3RnbFO8P on 2009-03-16
Install **kipi-plugins** in Synaptic Package Manager

---

### Post by oygle on 2009-03-16
Thanks, I did have kipi-plugins installed, but used Synaptic to re-install it. Still no go though, when the power is turned on, the camera does appear in Nautilus, but is not actually 'mounted'.

It doesn't show in /media , nor does it show in the 'mount' command.

I did notice in Synaptic, that when I searched for 'kipi', and viewed the results, some later versions of some packages were listed, these were not installed, but earlier ones were. Whether or not, they were dependencies of some important to resolve this, I don't know.

There must be a tool in Ubuntu, to check for all dependancies, and to then check that the latest version is installed ?

Oygle

---

### Post by xc3RnbFO8P on 2009-03-16
What is the output of:
> gedit /etc/udev/rules.d/45-libgphoto2.rules

---

### Post by oygle on 2009-03-16
The result of the gedit was an empty file, in fact the file does not exist.

> 
# ls -al /etc/udev/rules.d/45-libgphoto2.rules
ls: cannot access /etc/udev/rules.d/45-libgphoto2.rules: No such file or directory


---

### Post by xc3RnbFO8P on 2009-03-16
I have same problem connecting my Canon A590IS,
so I installed gThumb
started gThumb in Terminal **sudo gthumb**
just ignor errors turn the camera off and on again
You can also **choose from the catalog** (click the camera icon)

---

### Post by oygle on 2009-03-16
Thanks, I can see the thumbnails in gThumb | Import, but the camera still won't mount.

---

### Post by xc3RnbFO8P on 2009-03-16
When you are in gThumb turn the camaera off/on, you will get pop up window, do **unmount**
Then import in gThumb.

---

### Post by oygle on 2009-03-16
> **Ringi said:**
> When you are in gThumb turn the camaera off/on, you will get pop up window, do **unmount**
Then import in gThumb.

Thanks for your help. I will try that soon.

I'm actually able to import with a number of apps, DigiKam, F-Spot, gThumb, etc, but it is **mount**ing that will not work.

However, I noticed in DigiKam, the following under Import | Camera Configuration options ..

> 
To set a USB Mass Storage camera
(which looks like a removable drive when mounted on your desktop), please
use _[COLOR="Blue"]Mounted Camera[/COLOR]_ from camera list.
To set a Generic PTP USB Device
(which uses the Picture Transfer Protocol), please
use _[COLOR="Blue"]USB PTP Class Camera[/COLOR]_ from the camera list.


I had always used 'auto-detect' and it always found the Canon A460 in PTP mode, but I tried selecting the _[COLOR="Blue"]Mounted Camera[/COLOR]_ , it added 'Directory Browse' up the top, disabled the other previos options and added "/mnt/camera" as the camera mount path.

Now, there was no path by that name, however I notice that all the files on the camera can be seen by nautilus under the path

> 
~/.gvfs/gphoto2 mount on usb%3A004,006/DCIM/100CANON


and the results of lsusb are

> 
Bus 004 Device 006: ID 04a9:3149 Canon, Inc. 


Oygle

---

### Post by oygle on 2009-06-11
**lsusb**

> 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04a9:3149 Canon, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


which equates to this path when the camera is turned on ..

~/.gvfs/gphoto2 mount on usb%3A004,002/DCIM/100CANON

so, even though the camera is not mounted, it does show up in the filing system.

When will this mount problem be fixed ?

Oygle

---

### Post by cmreigrut on 2009-06-12
I can confirm this problem as well with a Canon PowerShot A570IS camera.  Interestingly enough, on my second computer (running Intrepid w/ KDE3.5) it automounts just fine, but on my primary computer (running Jaunty w/ KDE4) it fails.

Both machines report dmesg as:
```
[ 2611.685090] usb 2-3: new high speed USB device using ehci_hcd and address 21
[ 2611.829386] usb 2-3: configuration #1 chosen from 1 choice

```
and lsusb as:
```
Bus 002 Device 022: ID 04a9:314c Canon, Inc.

```

Googling around it would appear this may be a known bug ([http://ubuntuforums.org/showpost.php?p=7205851&postcount=4](http://ubuntuforums.org/showpost.php?p=7205851&postcount=4))

---

