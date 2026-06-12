---
title: "Video in camorama, but no video device in skype 2.0.0.72 :("
date: 2008-12-29
forum: Multimedia Software
---

### Post by frenchn00b on 2008-12-29
Any ideas what it could be ?
thanks

> uname -a:
2.6.26-bpo.1-686 #1 SMP Thu Dec 18 23:55:11 UTC 2008 i686 GNU/Linux

~$ lsmod   | grep spca
gspca                 640624  0
videodev               27680  1 gspca
usbcore               118192  8 snd_usb_audio,snd_usb_lib,gspca,usbhid,ehci_hcd,uhci_hcd

---

