---
title: "New netbook. Wireless not even listed in lshw"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by zepita on 2010-03-24
Hello people,

My brother brought me a netbook to remove windows 7 starter and to put linux on it.
I decided to try netbook remix and it works well, but wireless did not work.

Any help would be very appreciated :)

lshw output attached

---

### Post by Alabamaschalk on 2010-03-24
Hi!
If it is a Dell 10v, you can follow:
[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)
Hope that helps.

---

### Post by zepita on 2010-03-24
it does not seem to be a broadcom adapter since it's not dell.

I have read that updating the system will add support for broken drivers.

Downloading updates now to see if that works.

---

### Post by zepita on 2010-03-24
ok, it looks like it has a "wifi usb dongle" from syntek semiconductor withour any hardware switch. Instead, it has a Fn+F2 key shortcut to turn it on or off.
So far, it hasn't worked in ubuntu 9.10 netbook remix (not even recognized by lsusb or lspci)

---

### Post by Megafag on 2010-03-24
> **zepita said:**
> ok, it looks like it has a "wifi usb dongle" from syntek semiconductor withour any hardware switch. Instead, it has a Fn+F2 key shortcut to turn it on or off.
So far, it hasn't worked in ubuntu 9.10 netbook remix (not even recognized by lsusb or lspci)

Did the wireless work with the stock OS?

---

### Post by zepita on 2010-03-24
> **Megafag said:**
> Did the wireless work with the stock OS?

yes, it worked well.

Strange thing is that under linux, all the other Fn+F# keys do work well (touchpad lock, suspend, brightness level, etc)

Still testing...

Mandriva 2010 did not even boot from usb, but recognized the "usb dongle"
Now downloading easypeasy 1.5

---

