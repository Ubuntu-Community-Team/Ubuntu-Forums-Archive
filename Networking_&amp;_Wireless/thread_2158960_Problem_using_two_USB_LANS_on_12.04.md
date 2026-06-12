---
title: "Problem using two USB LANS on 12.04"
date: 2013-07-01
forum: Networking &amp; Wireless
---

### Post by blood207 on 2013-07-01
i have two usb lan on ubuntu 12.04 , when connect two usblan at the same time view on usblan (eth1) and view on virtual box usblan 2 (rename7) 
how edit usblan rename7 to ether 2 . note: two device the same type (jp1082) driver (dm9601) .

---

### Post by newbie-user on 2013-07-02
You can rename your network connections in /etc/udev/rules.d/70-persistent-net.rules

---

### Post by Bucky Ball on 2013-07-02
Welcome to the forums.

I have edited the thread title. Please help us help you and use a descriptive thread title. A generic one generally doesn't get you far. Just about everyone here has a 'problem' or 'needs help'. Good luck. ;)

(If you want to change the title, edit the first post and 'Go Advanced'. If it won't let you, tell me what you'd like. It appears like that on searches and the first post here but not other posts on the thread.)

---

