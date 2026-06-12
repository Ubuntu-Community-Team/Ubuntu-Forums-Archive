---
title: "Pwc loaded directly after connecting webcam"
date: 2008-03-11
forum: Multimedia &amp; Video
---

### Post by LordTiggy on 2008-03-11
Hi there,

I am trying to get a logitech webcam working on ubuntu 6.10 (dapper drake) and so far it seems to work; but when I connect the webcam using usb the kernel emidiatly loads the driver (pwc) what is not the problem but the resolution is set way to low by default and I can't seem to find the place where to give extra arguments to the modprobe line ...

Any ideas where I can set those things ...

Did a grep on pwc in the /etc directory but found nothing ... is the module loaded by some autoload thingy ...

Sorry if this post seems kinda chinese; but I don't know how to say it otherwise.

---

### Post by LordTiggy on 2008-03-11
Foudn it myself ...

just create a file in the /etc/modprobe.d/ dir called pwc with the needed arguments in it :)

Greetz

---

