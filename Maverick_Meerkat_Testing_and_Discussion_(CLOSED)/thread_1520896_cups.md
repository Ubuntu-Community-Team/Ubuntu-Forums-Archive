---
title: "cups"
date: 2010-06-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by koso on 2010-06-30
Hello,

last few days, my printer stopped working and I am not able to reinstall it. When I connect usb cable, printer seems to be recognized, but cups show no printer.

```
usb 4-1: new full speed USB device using uhci_hcd and address 2
usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04A9 pid 0x107F
usbcore: registered new interface driver usblp
```

So i tried to install it manually using cups web interface, and i found another problem ... i cannot login. System log shows:

```
2010-06-30 11:36:22	kubuntu-nb	cupsd	PAM _pam_init_handlers: could not open /etc/pam.conf
2010-06-30 11:36:22	kubuntu-nb	cupsd	PAM pam_start: failed to initialize handlers

```

and cupsd error log shows:
```
E [30/Jun/2010:11:36:22 +0200] cupsdAuthorize: pam_start() returned 26 (Critical error - immediate abort)!
```

Any idea where can be problem? I am using KDE4 but this seems to be general ubuntu problem.

---

### Post by caryb on 2010-06-30
I don't believe my KDE printer app has worked at all in Maverick so I use this in my browser [http://localhost:631/]("http://localhost:631/")
Cary

---

### Post by koso on 2010-06-30
> **caryb said:**
> I use this in my browser [http://localhost:631/](http://localhost:631/)
Cary

But all administrative operations in this web interface needs authorization, and that is my problem. I simply cannot login, so I am not able to add, remove and modify printer settings.

Strange is, that few days ago, I simply connected printer, it downloaded drivers and everything worked, but once I disconnected printer, I am not able to make it work again.

---

