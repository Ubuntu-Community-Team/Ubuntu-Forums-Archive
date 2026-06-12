---
title: "Fix: Ubuntu 12.10 does not connect to the wireless network"
date: 2013-02-24
forum: Networking &amp; Wireless
---

### Post by Angelus1102 on 2013-02-24
to fix the problem of not being able to connect to the network or the internet after you've updated ubuntu 12.10 follow the following easy codes on the terminal(you will need internet connection for this so use a usb wireless card or other method):

first: sudo apt-get remove bcmwl-kernel-source
second: sudo apt-get purge bcmwl-kernel-source
third: sudo apt-get install linux-firmware-nonfree

after this just restart your pc and you will be set to go...

---

### Post by mörgæs on 2013-02-24
Thanks for posting the fix.

To which kind of netcards does the fix apply?

---

