---
title: "webcam /dev/video0 Permission denied"
date: 2010-01-05
forum: Multimedia Software
---

### Post by JNik on 2010-01-05
I just updated from 9.04 to 9.10. My camera was working fine on 9.04 but I can access it only as root on 9.10.

**cheese**
```
(cheese:4015): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstpython.so': /usr/lib/gstreamer-0.10/libgstpython.so: file too short

** (cheese:4014): WARNING **: Failed to open /dev/video0: Permission denied
Segmentation fault
```

I have added myself in the video group

**id**
```
id=1000(john) gid=1000(john) groups=4(adm),20(dialout),21(fax),24(cdrom),26(tape),29(audio),30(dip),44(video),46(plugdev),104(fuse),106(lpadmin),112(netdev),121(admin),122(sambashare),125(vboxusers),1000(john)
```


Any help would be very appreciated

---

### Post by JNik on 2010-01-06
Google isn't helping much with this one, so if anyone knows a way to fix this...

---

### Post by Yellow Pasque on 2010-01-06
```
sudo apt-get --reinstall install python-gst0.10
```
As for permissions, I believe there is a separate 'camera' group. You can check the permissions of /dev/video:
```
ls -la /dev/video0
```

---

### Post by JNik on 2010-01-06
Thaks Temüjin.

My primary problem is the webcam permission (in all programs). 

I have changed the permissions of /dev/video0 to 666 by hand

**ls -la /dev/video0**
```
crw-rw-rw-+ 1 root video 81, 0 2010-01-05 22:16 /dev/video0
```

but still no go

---

### Post by Yellow Pasque on 2010-01-07
It looks like that device has an ACL. To remove:
```
sudo apt-get install acl
sudo setfacl -b /dev/video0
```

---

### Post by JNik on 2010-01-07
Unfortunately that didn't work.

Also after reboot, the permissions of /dev/video0 get changed again
```
crw-rw----+ 1 root video 81, 0 2010-01-07 12:04 /dev/video0
```

**grep video /etc/group**
```
video:x:44:john
```

**lsusb**
```
Bus 001 Device 005: ID 1e3d:8246  
Bus 001 Device 002: ID 0bc2:0502 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:08ad _Logitech, Inc. QuickCam Communicate STX_
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by JNik on 2010-01-08
bump...

---

### Post by JNik on 2010-01-11
anyone? :(

---

### Post by xc3RnbFO8P on 2010-01-11
Try this:
> I solved the problem. You must give to the user (you) permission for use video devices. Go to System > Administration > Users and Groups. Unlock and select your username. In user privileges, you must enable the line "Capture video from TV or webcams, and use 3d acceleration" or "Use Video Devices" log off and log in.

[http://ubuntuforums.org/showthread.php?t=1058495]("http://ubuntuforums.org/showthread.php?t=1058495")

---

### Post by JNik on 2010-01-11
[IMG]http://208.64.137.125/uploads/Screenshot-Account_Properties.png[/IMG]

I don't have that option... I only have video



I've even changed the owner and group of /dev/video0 to myself and it is still not working

ls -la /dev/video0
```
crw-rw-rw-+ 1 john john 81, 0 2010-01-10 17:47 /dev/video0
```

---

### Post by repat on 2010-05-08
sry for bumping but...any progress on this? i got the exact same problem-.-

edit:
i googled a bit more, this was my solution:

$ sudo chown user.group /dev/shm/usb-*

---

### Post by JNik on 2010-05-09
My problem was solved 2 days ago when I upgraded to 10.04 :)

---

