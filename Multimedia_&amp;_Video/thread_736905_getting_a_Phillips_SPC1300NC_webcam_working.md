---
title: "getting a Phillips SPC1300NC webcam working"
date: 2008-03-27
forum: Multimedia &amp; Video
---

### Post by mrpixels0 on 2008-03-27
is there an easy way to get this to work my system sees it but it just won't work:confused:


results of lsusb:      (only relevant parts are listed)

Bus 001 Device 006: ID 0471:0331 Philips




results of dmesg:   (only relevant parts are listed)

[   92.562292] usb 1-2.4: new full speed USB device using uhci_hcd and address 6

[   92.856046] uvcvideo: disagrees about version of symbol video_devdata
[   92.856050] uvcvideo: Unknown symbol video_devdata
[   92.856530] uvcvideo: disagrees about version of symbol video_unregister_device
[   92.856532] uvcvideo: Unknown symbol video_unregister_device
[   92.856594] uvcvideo: disagrees about version of symbol video_device_alloc
[   92.856596] uvcvideo: Unknown symbol video_device_alloc
[   92.856642] uvcvideo: disagrees about version of symbol video_register_device
[   92.856643] uvcvideo: Unknown symbol video_register_device
[   92.856753] uvcvideo: disagrees about version of symbol video_device_release
[   92.856755] uvcvideo: Unknown symbol video_device_release
[   92.858192] usbcore: registered new interface driver snd-usb-audio

is there somthing I am missing ?, I have tried the following to get it working:

1. compiled the latest v4l from source
2. compiled gspca from source
3. tried using pcw but could not find source for it.

is there anything else I could try or need to look for ?

sorry to keep buging everyone but I just get stumped on video related devices for some reason.

thanx for any help or advice you can give

MP0

---

### Post by linuxwizard on 2008-03-27
I can't find a listing of your webcam to which driver you need. You might want to see if this will work > [http://www.saillard.org/linux/pwc/](http://www.saillard.org/linux/pwc/) > 



Your webcam is not listed in the drivers you already tried.

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
[http://www.lavrsen.dk/twiki/bin/view/PWC/WorkingWebcamsWithPWC](http://www.lavrsen.dk/twiki/bin/view/PWC/WorkingWebcamsWithPWC)

---

### Post by mrpixels0 on 2008-03-28
Hi there Linuxwizard,

I compiled the pwc modules and did the Kernel thing, so I am just going to give this cam to a buddy who has Windows XP and I will just buy another webcam that is compatible with Linux :), hopefully I will be able to find a good one with at least 6.0 MP like this one.

thanks for the reply and advice.

PS: how do I thank folks, I mean so that it shows up on the right side of the screen, cause I thank people all the time and where it says thanks mine says 0 even though I thank people all the time.

MP0

---

### Post by linuxwizard on 2008-03-28
Hello mrpixels0
I have nothing else I can offer you or what else you could try to get your webcam working. To thank someone look on the right side of the post there is a yellow star click on that for the one you want to thank. Good Luck

---

### Post by mrpixels0 on 2008-03-28
No problems Linuxwizard :), I should looked more carefully before I made the Purchase thats all and thanks for the info on "Thanks" :).

MP0

---

### Post by LordTiggy on 2008-04-28
Uvc supports your webcam ... check link below :)

Didn't get mine working thou ... no /dev/video is created; hope you have better luck :)

[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

---

### Post by deloptes on 2008-05-26
> **mrpixels0 said:**
> is there an easy way to get this to work my system sees it but it just won't work:confused:


results of dmesg:   (only relevant parts are listed)

[   92.562292] usb 1-2.4: new full speed USB device using uhci_hcd and address 6

[   92.856046] uvcvideo: disagrees about version of symbol video_devdata
[   92.856050] uvcvideo: Unknown symbol video_devdata
[   92.856530] uvcvideo: disagrees about version of symbol video_unregister_device
[   92.856532] uvcvideo: Unknown symbol video_unregister_device
[   92.856594] uvcvideo: disagrees about version of symbol video_device_alloc
[   92.856596] uvcvideo: Unknown symbol video_device_alloc
[   92.856642] uvcvideo: disagrees about version of symbol video_register_device
[   92.856643] uvcvideo: Unknown symbol video_register_device
[   92.856753] uvcvideo: disagrees about version of symbol video_device_release
[   92.856755] uvcvideo: Unknown symbol video_device_release
[   92.858192] usbcore: registered new interface driver snd-usb-audio


MP0

Hello, I've been looking for a soulution for about a few days, and it was that simple. So I decided to share it with you. Ot may help.

The problem with the "disagrees about version of symbol " is that if you install v4l-dvb-experimental then the kernel source file *Module.symvers* does not get updated.

What you have to do is before you run make, to copy this file like this:
```
cp <PATH_TO>/v4l-dvb-experimental/v4l/Module.symvers .
```

then make and make install, load the module and enjoy

The info is from [http://lists.berlios.de/pipermail/linux-uvc-devel/2008-February/003104.html]("http://lists.berlios.de/pipermail/linux-uvc-devel/2008-February/003104.html")

regards

---

