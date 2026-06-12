---
title: "Can't find my iPod listed in gtkpod"
date: 2009-05-03
forum: Multimedia Software
---

### Post by Lakeside5 on 2009-05-03
Ok, I am starting to think there is something wrong with my iPod, or how my iPod connects to my computer. I just bought a secondhand iPod (knowing nothing of iPods previously) and so far I have managed to convert  an avi into mp4, and install gtkpod BUT, when I plug my iPod into the USB, turn it on, and load up gtkpod, I do not see my iPod listed on the left hand screen as I am supposed to: [http://linuxondesktop.blogspot.com/2008/05/converting-and-transferring-audiovideo.html](http://linuxondesktop.blogspot.com/2008/05/converting-and-transferring-audiovideo.html) Can someone please tell me what the problem may be? thanks

---

### Post by fornix on 2009-05-03
after you connect your ipod, do a 
```
$ dmesg | tail
```
and post your output

---

### Post by Lakeside5 on 2009-05-03
Thanks fornix, here it is:
[24920.941729] usb 5-4: USB disconnect, address 9
[24925.740040] usb 5-4: new high speed USB device using ehci_hcd and address 10
[24925.894704] usb 5-4: configuration #1 chosen from 3 choices
[25640.501321] usb 2-1: USB disconnect, address 4
[25653.110045] usb 2-1: new low speed USB device using uhci_hcd and address 9
[25653.303621] usb 2-1: configuration #1 chosen from 1 choice
[25653.321129] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:10.1/usb2/2-1/2-1:1.0/input/input9
[25653.398010] input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:10.1-1
[25653.429494] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:10.1/usb2/2-1/2-1:1.1/input/input10
[25653.560433] input,hidraw1: USB HID v1.10 Device [Logitech Logitech USB Keyboard] on usb-0000:00:10.1-1
*update*  I took my iPod to Future Shop, and as soon as the clerk hooked it up to their computer, my iPod popped upk and iTunes loaded, so at least I know my iPod is ok. The clerk explained that my best bet is to have Windows on  my computer too (uggh) because the guy I bought it off of must have configured it to run in Windows with iTunes, so if I wanted to get it to run with a different OS (which he didn't recommend) I would first  have to find a Windows OS computer anyway, and reconfigure   my iPod etc. Unless anyone knows how I can reconfigure my iPod using my own linux computer and starting all over with it..

---

### Post by fornix on 2009-05-06
Which ipod do you have?
I have a nano 3g running with gtkpod with no issues at all.

---

### Post by Lakeside5 on 2009-05-09
It's an iPod touch. I decided to finally get my daughter's computer fixed (it had a 'Windows' problem, let's see how long before it crashes again lol) because it plays nice with iTunes and iPods, so I can use my iPod. Still curious how to get Linux to do the same. thanks.

---

