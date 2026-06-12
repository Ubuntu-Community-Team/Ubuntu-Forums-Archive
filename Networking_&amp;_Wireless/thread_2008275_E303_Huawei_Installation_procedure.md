---
title: "E303 Huawei Installation procedure"
date: 2012-06-22
forum: Networking &amp; Wireless
---

### Post by sunilgavaskar on 2012-06-22
Tried hard in searching solution in this forum, to install E303 in Ubuntu 11.04 but all efforts gone in vain.!
Later we identified the E303 card has driver and installation binary files within. But we could not see listing of files.. (Bloody huawei... ). However, listing can be seen at very first time plugging into a new PC. hurray!!
Copied all binaries and drivers into a pen drive and took back it to my PC and installed it. It works..

[B]Procedure:
- Login as su
- download the attached zip - [https://docs.google.com/open?id=0B4oQlH9i38JPR3hDRlNXbFRWYjQ](https://docs.google.com/open?id=0B4oQlH9i38JPR3hDRlNXbFRWYjQ)
( Click File--->Download)
- unpack the zip
- cd linux_mbb_install
- ./install

[/B]Intercepts the card as eth2- wired connection. Start browsing
Now you could see "... Driver=cc_ether", while running 'lsusb' or 'usb-devices'
:guitar:
p.s: The forum is implemented in stone age.. please upgrade.. even attaching files sucks!

---

### Post by darkhoros on 2013-01-21
Hi,
Had this issue and tried this solution, it worked, you will need to chmod 777 install to make this file work though.

Some explanation about this issue here
[http://sgolubtsova.blogspot.com/2012/07/installing-huawei-hilink-3g-modem.html](http://sgolubtsova.blogspot.com/2012/07/installing-huawei-hilink-3g-modem.html)

Thank you

---

