---
title: "Update from 11.04 to 11.10: How to fix D-Link DWA-140"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by elf23 on 2011-10-14
When updating from 11.04 to 11.10, my DWA-140 USB wireless networking device stopped working.

It turned out that I'd previously blacklisted the rt2800usb driver which was problematic in ubuntu 11.04 (see [this thread]("http://ubuntuforums.org/showthread.php?t=1741600")), but which is now required in 11.10.

If you have the same problem, all you need to do is to edit the blacklist file in /etc/modprobe.d/blacklist.conf, and remove the line which blacklists rt2800usb.

Hope this helps someone with the same problem!

---

### Post by UCAP on 2011-10-17
Thank you for your post. That is exactly what I was looking for!

---

### Post by buratino22 on 2011-10-18
Thank you very much!

Writing through the newly fixed DWA140 wireless connection...:-)

---

### Post by gezacsikasz on 2011-10-19
Hello and thanks! Problem solved in 30 seconds. Strange, though, going back to previously blacklisted modules...

---

