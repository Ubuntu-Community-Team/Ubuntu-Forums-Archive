---
title: "Fujifilm A850 digital camera won´t mount"
date: 2014-06-14
forum: Multimedia Software
---

### Post by trickster3 on 2014-06-14
Hi all,
i´m new here. Also, i am new to Ubuntu and linux. I have installed Ubuntu 14.04 LTS on my mother´s Acer Aspire 3515. Everything works fine apart from her digital camera, which won´t mount. I plug it in and nothing happens. No error, nothing. I typed "lsusb" to terminal and there was fujifilm something listed (can´t remember exactly, didn´t take screenshot as i don´t know how) but that´s as far as it goes.
Googling doesn´t help, so i decided to try to ask here :-)
There is no such thing as linux drivers for cameras, right ? I don´t own camera myself, and being linux newb leaves me clueless...
Thanks in advance.

---

### Post by Bucky Ball on 2014-06-14
*Thread moved to **Multimedia & Video**.*

Better here. We'll need the model number of the camera and/or the output of 'lsusb'. Just the Fujifilm line is fine. No need for screenshot, just scribble it down.

---

### Post by trickster3 on 2014-06-14
Hey Bucky Ball, thanks for quick reply. Camera has Fujifilm A850 written on it, no additional numbers or whatever. lsusb output:

Bus 002 Device 003: ID 04cb:01e7 Fuji Photo Film Co., Ltd

---

### Post by trickster3 on 2014-06-16
Bump... any advice please ?

---

### Post by ibjsb4 on 2014-06-16
I have had the same problem with fuji in the past and found that the package "shotwell" will detect these cameras.  Give it a try, its in the software center.

---

### Post by trickster3 on 2014-06-16
Hi ibjsb4, actually i have already fixed the problem, by installing gtkam which detects it just fine. Thank you for your suggestion.
Hope this may help someone with similar issue.
Cheers :-)

---

### Post by ibjsb4 on 2014-06-16
gtkam??  Have not played with that one, thanks for the tip :)

---

