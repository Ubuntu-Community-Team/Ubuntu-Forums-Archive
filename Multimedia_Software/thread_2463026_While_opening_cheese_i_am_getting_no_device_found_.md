---
title: "While opening cheese i am getting no device found message"
date: 2021-06-01
forum: Multimedia Software
---

### Post by harish1999 on 2021-06-01
HELLO,
I recently switched to UBUNTU. I installed Ubuntu 20.04. I was not able to access camera and touch screen on my system. If i open cheese application i am getting a error message saying " NO DEVICE FOUND". could somebody please tell me how do i sort it out.

---

### Post by Holger_Gehrke on 2021-06-01
Sad to say, but we are not mind readers - at least I am not. Laptop or desktop, what camera and touchscreen make and model ? Normally cameras are connected through USB (even on laptops) and almost all of them are UVC (USB Video Class) compliant. But some models have various ... quirks ... and you have to make some settings - usually in the form of parameters for the kernel modules / drivers - to make them work. Touchscreens usually are connected through USB also, but they should come up as HID (Human Interface Devices). A look at the output of 'lsusb' in a terminal is probably the quickest way to find out if the devices are getting seen and what the Kernel identifies them as.

Holger

---

### Post by harish1999 on 2021-06-01
hey Holger,
I am using Surface pro 6. I am using built in camera integrated camera

---

### Post by Holger_Gehrke on 2021-06-01
Don't have one of these, but it doesn't look too good. These two-in-one machines are highly integrated using lots of proprietary hardware. There is a [project to add support]("https://github.com/linux-surface/linux-surface") to the Linux kernel for various Surface machines, and it does give installation instructions for installing the patched kernel on Ubuntu, but the camera of the Surface Pro 6 isn't currently supported.

Holger

---

