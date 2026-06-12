---
title: "Stuck with logitech quickcam E 3500"
date: 2009-01-20
forum: Multimedia Software
---

### Post by alarichall on 2009-01-20
Hello,

I'd be very grateful for any help getting this working.

I have Ubuntu 8.04 on a Thinkpad T40. When I type uname -a, I get

2.6.24-23-generic #1 SMP Thu Nov 27 18:44:42 UTC 2008 i686 GNU/Linux

I got hold of a logitech quickcam E 3500 today. When I type lsusb, I get

Bus 004 Device 004: ID 046d:09a4 Logitech, Inc.

I can't make it work at all. Besides looking at various other pages, I've worked through the instructions at [https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC). At the end of that I got an error message. When I typed dmesg, I got:

[ 2508.869851] usb 4-4: new high speed USB device using ehci_hcd and address 4
[ 2509.111493] usb 4-4: configuration #1 chosen from 1 choice
[ 1003.665208] uvcvideo: disagrees about version of symbol v4l_compat_ioctl32
[ 1003.665219] uvcvideo: Unknown symbol v4l_compat_ioctl32
[ 1003.665982] uvcvideo: disagrees about version of symbol video_devdata
[ 1003.665985] uvcvideo: Unknown symbol video_devdata
[ 1003.666827] uvcvideo: disagrees about version of symbol video_unregister_device
[ 1003.666830] uvcvideo: Unknown symbol video_unregister_device
[ 1003.667087] uvcvideo: disagrees about version of symbol video_device_alloc
[ 1003.667089] uvcvideo: Unknown symbol video_device_alloc
[ 1003.667269] uvcvideo: disagrees about version of symbol video_register_device
[ 1003.667271] uvcvideo: Unknown symbol video_register_device
[ 1003.667711] uvcvideo: disagrees about version of symbol video_usercopy
[ 1003.667714] uvcvideo: Unknown symbol video_usercopy
[ 1003.667794] uvcvideo: disagrees about version of symbol video_device_release
[ 1003.667797] uvcvideo: Unknown symbol video_device_release
[ 2512.914508] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/usb/usbaudio.c:1289: 4:3:1: cannot set freq 16000 to ep 0x86
[ 1010.809027] uvcvideo: disagrees about version of symbol v4l_compat_ioctl32
[ 1010.809039] uvcvideo: Unknown symbol v4l_compat_ioctl32
[ 1010.809827] uvcvideo: disagrees about version of symbol video_devdata
[ 1010.809830] uvcvideo: Unknown symbol video_devdata
[ 1010.810648] uvcvideo: disagrees about version of symbol video_unregister_device
[ 1010.810651] uvcvideo: Unknown symbol video_unregister_device
[ 1010.810907] uvcvideo: disagrees about version of symbol video_device_alloc
[ 1010.810909] uvcvideo: Unknown symbol video_device_alloc
[ 1010.811088] uvcvideo: disagrees about version of symbol video_register_device
[ 1010.811091] uvcvideo: Unknown symbol video_register_device
[ 1010.811530] uvcvideo: disagrees about version of symbol video_usercopy
[ 1010.811533] uvcvideo: Unknown symbol video_usercopy
[ 1010.811613] uvcvideo: disagrees about version of symbol video_device_release
[ 1010.811616] uvcvideo: Unknown symbol video_device_release

I'm stuck and would really appreciate any help. I could really do with getting the camera working quickly, so I'd even be willing to consider upgrading to 8.10 if that would be a reliable solution.

Thanks!

---

