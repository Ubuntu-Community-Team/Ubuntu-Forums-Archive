---
title: "being root when using libdc1394"
date: 2009-02-17
forum: Multimedia Software
---

### Post by zykos on 2009-02-17
Hi,

I'm writing a program to capture frames from a firewire webcam (unibrain fire-i), and tried using libdc1394. The dc1394_new function seems to work, but the driver then can't find the cameras unless I run the program as root. I've installed Coriander, but it too seems to be able to get data from the camera only if ran as root. I looked into the issue, and modified the permissions on /dev/raw1394 and /dev/video1394/0, but that didn't solve the problem. Also, the image I get when the program does run is distorted, but that's another issue altogether.

Any idea how to allow libdc1394 functions to work for a normal user would be great.

Thanks.

---

### Post by Roving Sign on 2009-02-17
> **zykos said:**
> Hi,

I'm writing a program to capture frames from a firewire webcam (unibrain fire-i), and tried using libdc1394. The dc1394_new function seems to work, but the driver then can't find the cameras unless I run the program as root. I've installed Coriander, but it too seems to be able to get data from the camera only if ran as root. I looked into the issue, and modified the permissions on /dev/raw1394 and /dev/video1394/0, but that didn't solve the problem. Also, the image I get when the program does run is distorted, but that's another issue altogether.

Any idea how to allow libdc1394 functions to work for a normal user would be great.

Thanks.

Perhaps: in System > Administration > User and Groups

Check your users Properties > User Priviliges

There should be a checkbox that references webcams/capture...

---

### Post by zykos on 2009-02-17
> There should be a checkbox that references webcams/capture...
It was unchecked, but that didn't solve the problem. Both Coriander and my own program fail if I don't start them as root.

The error message I get when I start Coriander is:
```
Warning: could not get a handle to your IEEE1394 card.

Please check that:
- the card is present
- the IEEE modules (ieee1394, ohci1394, raw1394 and video1394) are loaded
- you have read/write permissions on the /dev/raw1394 and /dev/video1394 devices.
```

I modprobe'd all the modules listed, and it works when I'm root. And it still fails even with 777 privileges on both the devices.

---

### Post by alexei.colin on 2010-01-22
Just wanted to note that 
1. checking the webcam box in User Priveleges (which just adds the user to the video group)
2. changing the group on /dev/raw12394 and /dev/video1394* to video (chgrp), and
3. logging out/in (for group membership change to take effect) 
solved my same firewire camera permissions problem but with a different application.

---

