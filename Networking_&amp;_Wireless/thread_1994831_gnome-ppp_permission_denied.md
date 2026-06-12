---
title: "gnome-ppp permission denied"
date: 2012-06-03
forum: Networking &amp; Wireless
---

### Post by rdh61 on 2012-06-03
Hi,

I am running Ubuntu 12.10, connecting to the Internet with a USB modem. I can do this in a terminal with wvdial but only if I use sudo. Without this I am told "permision denied". However, I prefer to use the graphical interface gnome-ppp. With this connection fails, and the log tells me "permission denied". If I open "set up" and click on "detect", I am told that gnome-ppp cannot detect a modem on my system. However, I still have a hunch it may be more of a permissions issue.

I would be grateful for help in solving this. Please let me know what information I should post here in order to help you help me.

Many thanks.

---

### Post by rdh61 on 2012-06-04
Wrong device was selected.

Open gnome-ppp, click on "Setup", enter correct device in Device. 

In my case it wasn't one of those in the drop-down menu. It was: /dev/ttyACM1.

Device can be found with by typing this in terminal: sudo wvdialconf /etc/wvdial.conf

---

