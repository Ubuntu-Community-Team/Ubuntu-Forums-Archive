---
title: "Problem Logitech webcam uvcvideo"
date: 2010-03-07
forum: Multimedia Software
---

### Post by roundhay on 2010-03-07
I am having problems using a Logotech quickcam fusion in 9.04 & 9.10

model info:

```

~$ lsusb
Bus 001 Device 005: ID 046d:08ca Logitech, Inc. Mic (Fusion)

```

I can get the webcam to work by using the following terminal commands:

```

~$ sudo rmmod uvcvideo
~$ sudo modprobe uvcvideo

```

The problem is that I have to run these commands every time I reboot the PC. How can I make this fix permanent?

I have found several posts which suggest loading in a new uvcvideo module but before I try this I was wondering if there is a simpler solution.

---

### Post by roundhay on 2010-04-03
Bump, does anyone know how I can do this?

---

