---
title: "Best usb stick burner"
date: 2019-05-26
forum: Multimedia Software
---

### Post by geovino on 2019-05-26
Looking for a good program for burning images to USB stick. Found a very good one in Fedora but so far haven't found a good one in Ubuntu. Any suggestions?
Tried Ubuntu Startup Disk Creator but it doesn't see the iso file in the download folder.

---

### Post by oldos2er on 2019-05-26
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by Dennis N on 2019-05-26
These USB image writers aren't distro specific. If you have access to a Fedora system, theirs will create an Ubuntu installer USB for you from a Ubuntu .iso.

---

### Post by jeremy31 on 2019-05-26
I don't use any GUI program for writing ISO to USB stick, I just find out what the USB stick is mounted as /dev/sdb /dev/sdc and then in terminal do
```
sudo cp <imagename> /dev/sd?
```

---

### Post by geovino on 2019-05-26
Thank you. Works fine :)

---

### Post by C.S.Cameron on 2019-05-27
Mkusb is quick and simple to use.

---

