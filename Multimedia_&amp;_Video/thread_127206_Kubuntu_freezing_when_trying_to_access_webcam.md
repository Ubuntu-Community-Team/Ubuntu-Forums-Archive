---
title: "Kubuntu freezing when trying to access webcam"
date: 2006-02-08
forum: Multimedia &amp; Video
---

### Post by drange on 2006-02-08
Bought myself a new webcam, a Creative something...

According to dmesg, everything's OK, but when I try to access the webcam with Gimp, webcam or EffecTV, everything freezes, and nothing works. Can't even ctrl-alt-backspace out of KDE.
```
[4294722.099000] Linux video capture interface: v1.00
[4294722.111000] drivers/usb/media/spca5xx/spca5xx-core.c: USB SPCA5XX camera fo
und. Type Creative Instant P0620
[4294722.177000] usbcore: registered new driver spca5xx
[4294722.177000] drivers/usb/media/spca5xx/spca5xx-core.c: spca5xx driver 00.57.
02 registered
```

---

### Post by az on 2006-02-08
This is a known bug.  I think it is fixed in Dapper.  You can look on the wiki for instructions on how to recompile the module properly.

---

### Post by drange on 2006-02-08
[QUOTE=azz]This is a known bug.  I think it is fixed in Dapper.  You can look on the wiki for instructions on how to recompile the module properly.[/QUOTE]Thank you very much. Can you point to a page where this bug is mentioned?

I'll try to recompile the kernel.

---

### Post by az on 2006-02-08
[https://wiki.ubuntu.com/Spca5xx](https://wiki.ubuntu.com/Spca5xx)

Scroll down and use the second method.  You don't need to become root - just run the commands using sudo.

And you won't be recompiling the kernel.  You only need to compile the spca5xx module which should take you less then six minutes....

---

