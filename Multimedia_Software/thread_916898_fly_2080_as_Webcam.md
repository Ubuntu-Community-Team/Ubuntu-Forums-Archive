---
title: "fly 2080 as Webcam"
date: 2008-09-11
forum: Multimedia Software
---

### Post by anilg on 2008-09-11
hi,

my phone Fly 2080 has a webcam mode. When I connect it to my laptop with the provided USB, ekiga wont show me any video.

I've also noticed that the phone randomly restarts everytime i try to take a photo with the "cheese" software. The dmesg output after connecting the webcam is..

[ 8065.169561] usb 3-1: USB disconnect, address 14
[ 8069.167888] usb 3-1: new full speed USB device using ohci_hcd and address 15
[ 8069.260934] usb 3-1: configuration #1 chosen from 1 choice
[ 8069.266731] uvcvideo: Found UVC 1.00 device Fly2080 (0e8d:0004)
[ 8069.270160] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).


How do i get this working?

---

### Post by anilg on 2008-09-11
It started working with ekiga after restarting Ubuntu. however, cheese still wont recognize it.. i just see the color bars.

any idea?

---

