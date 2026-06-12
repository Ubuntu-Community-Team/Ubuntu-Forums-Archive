---
title: "Hauppauge Nova-TD stick"
date: 2008-09-19
forum: Multimedia Software
---

### Post by TheValk on 2008-09-19
Has anyone managed to get one of these working in Hardy yet?
lsusb recognises it as a hauppage with ID 2040-5200.
I can't get it to list in dmesg at all.
I have spent a good few hours searching the forums and the web but sadly, all the advice I found referred mostly to the Nova-T.

---

### Post by xc3RnbFO8P on 2008-09-19
There is two version of this card, try this:
2040:9580 [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-TD-Stick]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-TD-Stick")

---

### Post by TheValk on 2008-09-19
Thanks, I have already visited that site and unfortunately the procedures didn't work.
I suspect that it is because of the different ID, mine's 2040-5200.
It may be that dib0700 doesn't recognise it as a Nova-TD?

---

### Post by xc3RnbFO8P on 2008-09-19
It is working in Suse not in Hardy:
[http://www.linux-club.de/viewtopic.php?f=27&t=96802&p=585381]("http://www.linux-club.de/viewtopic.php?f=27&t=96802&p=585381")
using dvb-usb-dib0700-1.10.fw and kernel 2.6.25 .
Google this [B]wintv nova td 2040-5200
[/B]

---

### Post by TheValk on 2008-09-19
It seems that I'll just have to wait for an update to the driver to come through.

---

