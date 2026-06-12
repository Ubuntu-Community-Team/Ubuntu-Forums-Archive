---
title: "Inserting wireless card causes computer to reboot."
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by chrisN_uk on 2008-12-28
I've recently upgraded to 8.10 and everything works fine except for my wireless card, which causes my system to (freeze|reboot|turn off) whenever I plug it in. I have a belkin F5D7051 usb adapter. 

/var/log/kern.log and dmesg  seem to show a lot of lines like this as the last log before my computer reboots:

```

[  440.120805] ppdev0: registered pardevice
[  440.168454] ppdev0: unregistered pardevice
[  441.217107] ppdev0: registered pardevice
[  441.264313] ppdev0: unregistered pardevice
[  441.380169] ppdev0: registered pardevice
[  441.428062] ppdev0: unregistered pardevice

```

and one time showed this: 

```

Dec 28 13:23:56 chris-desktop kernel: [  455.347163] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Dec 28 13:23:56 chris-desktop kernel: [  455.416164] usbcore: registered new interface driver ndiswrapper

```


I'm guessing this is due to some driver incompatibility somewhere, but I don't know how to find out? Are there other logs that I should be looking in?

---

