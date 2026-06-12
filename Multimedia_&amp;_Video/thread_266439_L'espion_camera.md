---
title: "L'espion camera"
date: 2006-09-27
forum: Multimedia &amp; Video
---

### Post by Zalbor on 2006-09-27
I've been trying to make my small camera work. I know the "pencam" program can use it, as I've done it in another distro and Breezy, but since upgrading to Dapper it doesn't work. It's the version from the repositories, and happens even if I try to run it as root.
The error is:
```
 pencam_set_configuration error
 Error initializing camera in main!
```

---

### Post by mgiese on 2007-02-14
> **Zalbor said:**
> I've been trying to make my small camera work. I know the "pencam" program can use it, as I've done it in another distro and Breezy, but since upgrading to Dapper it doesn't work. It's the version from the repositories, and happens even if I try to run it as root.
The error is:
```
 pencam_set_configuration error
 Error initializing camera in main!
```

same here for me, i am using gentoo linux, i have the stv680 as module compiled into the kernel and the cam is working in "xawtv"

pencam2-0.67 tells me : 

# ./pencam2
 pencam_set_configuration error
 Error initializing camera in main!


i also used the old pensnap-0.21 and it tells me / when trying to "z = start autosnap" :

usb_bulk_read error
 Re-initializing camera
 Couldn't get image info
 usb_bulk_read error
 Re-initializing camera
 Couldn't get image info

i have libusb-0.1.12
thats to sad

---

