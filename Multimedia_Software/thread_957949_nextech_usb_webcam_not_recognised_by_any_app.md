---
title: "nextech usb webcam not recognised by any app"
date: 2008-10-24
forum: Multimedia Software
---

### Post by Xant on 2008-10-24
I turned from the dark side a few months ago with only a few minor errors on my system. those problems being mainly: I cannot have my 10$ webcam found by any means. Iv tried all the apps in add/remove that are supposed to find one, and nothing will even note that SOMEthing is in the usb jack.
Im un an acer aspire 3680

---

### Post by Yellow Pasque on 2008-10-24
Does lsusb even see it?:
```
lsusb
```
If not, see if this works:
```
sudo update-usbids
lsusb
```

---

### Post by Xant on 2008-10-26
how would I know?
I get
Bus 005 Device 002: ID 2770:930c NHJ, Ltd
Bus 005 Device 001: ID 0000:0000
Bus 004 ""
Bus 003 ""
Bus 002 ""
Bus 001 ""

---

### Post by yamushk on 2008-12-25
> **Temüjin said:**
> Does lsusb even see it?:
```
lsusb
```
If not, see if this works:
```
sudo update-usbids
lsusb
```

Hi,

My lsusb sees it:

```
Bus 002 Device 002: ID 093a:262a Pixart Imaging, Inc.
```

But Skype doesn't see it. I tried to install EasyCam using information from both [here]("http://ubuntuforums.org/showthread.php?t=699578&highlight=nexxtech+webcam") and [here]("http://blognux.free.fr/?p=27"), but installation is not finished properly. Adept Manager shows that the installation is "BROKEN" something (I haven't seen that before, so I don't know what it means).

I'm using Ubuntu 8.04.1, KDE (Kubuntu).

Is there another driver I should try? Or maybe Skype is simply a bit stupid? :-)

Thanks!

:popcorn:

---

