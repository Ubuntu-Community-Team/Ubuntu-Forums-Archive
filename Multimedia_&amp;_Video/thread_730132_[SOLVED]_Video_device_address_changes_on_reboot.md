---
title: "[SOLVED] Video device address changes on reboot"
date: 2008-03-20
forum: Multimedia &amp; Video
---

### Post by peterthebike on 2008-03-20
I have a Logitech web cam connected by USB and a Hauppauge WinTV-Express PCI card. The WinTV-Express card is used as a video capture card for a video camera I have in a bird nesting box.

The nest box cam runs through Motion to only record when there is any movement in the nest box.

My problem is most times when I reboot, the video device for the nest box cam keeps changing between /dev/video1 and /dev/video0. Obviously this means I have to keep changing the configuration for Motion.

Is there a way to make the video device always have the same value?

---

### Post by floquet on 2008-03-21
To avoid the /dev/video(x) to be changed every time the computer is rebooted simbolic links are created at the initiatlization of udev by adding a file /etc/udev/rules.d/11-video.rules that will create the link to the subsystem/vendor/device. My 11-video.rules looks like this:

[PHP]KERNEL=="video?", BUS=="pci", SYSFS{subsystem_device}=="0x0012",SYSFS{subsystem_vendor}=="0x11bd", SYMLINK+="video-pinn-rave"
KERNEL=="video?", BUS=="pci", SYSFS{subsystem_device}=="0x002d",SYSFS{subsystem_vendor}=="0x11bd", SYMLINK+="video-pinn-300i"
KERNEL=="video?", BUS=="pci", SYSFS{subsystem_device}=="0x8277",SYSFS{subsystem_vendor}=="0x1043", SYMLINK+="webcam-logitech-fusion"[/PHP]

The right values for the bus, subsystem device and the subsystem vendor can be found by typing in the terminal 
[PHP]udevinfo -a -p $(udevinfo -q path -p /class/video4linux/video2)[/PHP]


A couple of web pages explaining how to do these changes are:
[http://willtofly.com/mythtv/](http://willtofly.com/mythtv/)
[http://www.knoppmythwiki.org/index.php?page=Udev](http://www.knoppmythwiki.org/index.php?page=Udev)

---

### Post by peterthebike on 2008-03-21
Thanks for that solution. I would _never_ have found that myself!

---

