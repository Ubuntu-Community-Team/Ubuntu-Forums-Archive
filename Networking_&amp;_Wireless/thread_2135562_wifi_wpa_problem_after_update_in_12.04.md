---
title: "wifi wpa problem after update in 12.04"
date: 2013-04-14
forum: Networking &amp; Wireless
---

### Post by mge on 2013-04-14
Hi, 
I have a EW-7318usg usb dongle (rt73usb driver) dongle and the wifi worked fine in 12.04.
(I tried it in 12.10 but it didn't work so I downgraded to 12.04 version).

About a week ago I did an update and the wifi stopped working (exactly as it didn't work in 12.10 when I tried).

I can connect to my AP, but I can't ping anything (even the AP itself).
I have the problem only when using WPA encryption.
Everything works when I connect to unprotected network.

I tried a lot of things among them to set nohwencrypt:
sudo modprobe rt73usb nohwcrypt=1
but nothing worked...

Thanks in advance,
Michael

---

