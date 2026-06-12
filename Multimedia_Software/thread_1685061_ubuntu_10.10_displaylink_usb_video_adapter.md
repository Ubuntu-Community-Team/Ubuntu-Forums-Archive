---
title: "ubuntu 10.10 displaylink usb video adapter"
date: 2011-02-10
forum: Multimedia Software
---

### Post by alberto.priore on 2011-02-10
I just bought this USB graphics adapter [http://www.hi-techitaly.com/news/computer/2501-bestit-itek-uga-connettere-fino-a-6-monitor-allo-stesso-computer.html](http://www.hi-techitaly.com/news/computer/2501-bestit-itek-uga-connettere-fino-a-6-monitor-allo-stesso-computer.html) and I need to use it on Ubuntu 10.10. I followed this guide,[http://libdlo.freedesktop.org/wiki/](http://libdlo.freedesktop.org/wiki/) but when I ran

$ ./configure && sudo make install && make check nothing happened. On Windows, after the installation the monitor was detected automatically.

How do I get it to work on Ubuntu?

---

### Post by c678014 on 2011-03-04
Rather than attempting to compile the display link driver I installed the Ubuntu 10.10 package:

aptitude search displaylink
i   xserver-xorg-video-displaylink                                          - X driver for DisplayLink devices

---

### Post by EugenePer on 2011-03-09
> **c678014 said:**
> Rather than attempting to compile the display link driver I installed the Ubuntu 10.10 package:

aptitude search displaylink
i   xserver-xorg-video-displaylink                                          - X driver for DisplayLink devices

I did it on ubuntu 10.04 but i have problem with xserever configuration there. Does it work on ubuntu 10.10 ? How to configure xserever for it?

---

