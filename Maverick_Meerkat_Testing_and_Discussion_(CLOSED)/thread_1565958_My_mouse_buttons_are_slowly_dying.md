---
title: "My mouse buttons are slowly dying"
date: 2010-09-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by yaji on 2010-09-01
Weird things are happening. My mouse buttons are dying after login. At GDM all of them are fine, after login left one stops working, and after opening some apps like firefox or synaptic, rest of them dies too. 

I don't know how this happened, and without working mouse its really hard to figure it out. 

:confused:

*(In b4 "your mouse sucks", no its fine and its working right now on Windows).*

---

### Post by VMC on 2010-09-01
> **yaji said:**
> Weird things are happening. My mouse buttons are dying after login. At GDM all of them are fine, after login left one stops working, and after opening some apps like firefox or synaptic, rest of them dies too. 

I don't know how this happened, and without working mouse its really hard to figure it out. 

:confused:

*(In b4 "your mouse sucks", no its fine and its working right now on Windows).*

Is this a wireless mouse, wired, optical, usb, din ?

---

### Post by yaji on 2010-09-01
Wired, laser, USB.

---

### Post by yaji on 2010-09-02
*shameless bump*

---

### Post by lonniehenry on 2010-09-02
Have you tried a different mouse?  Or changing the click time and settings in Systems/Preferences/Mouse?  Sometime a starting to fail hardware shows odd behaviour before really failing.

---

### Post by yaji on 2010-09-02
The mouse is almost new, and I'm using it right now on Windows7. I'll try to mess with the click time. Brb.

edit.

Nope, it didn't helped.

---

### Post by VMC on 2010-09-02
> **yaji said:**
> The mouse is almost new, and I'm using it right now on Windows7. I'll try to mess with the click time. Brb.

edit.

Nope, it didn't helped.

Try plugging it into another usb port, and see if the same results.

Also check dmesg output from the port in use.

---

### Post by coffeeman1321 on 2010-09-02
hi, im new to linux. sorry not trying to steal your thread. i have a lap top and my mouse pad just died last night. the pointer will move on start up to log in, then it is inop once the desktop is present.  im using a usb type mouse now and that works. any help would be appreciated

---

### Post by ranch hand on 2010-09-02
This is a completely different subject.

Start a new thread.

---

### Post by yaji on 2010-09-02
> **VMC said:**
> Try plugging it into another usb port, and see if the same results.

It didn't helped ;(

> **VMC said:**
> Also check dmesg output from the port in use.

```
USB 3-2 : full speed USB device using uhci_hcd and address 2
input: A4TECH USB Device as /devices/pci0000:00 00:001a.0/USB3/3-2/3-2:1.0/input/input3
```

---

