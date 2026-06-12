---
title: "Ubuntu Boot Splash Screen"
date: 2008-07-10
forum: Multimedia Software
---

### Post by sges on 2008-07-10
This is a minor annoyance but does anyone know how to control the resolution and the driver used for the ubuntu boot splash screen? the splash screen is in 640x480 and look distroted on my 1440x900 native resolution monitor. (once Gnome starts the resolution changes to the correct 1440x900, set with ENVYNG to the older Nvidia 96.43.05 driver as I as having problems with the 169.xx.xx and 173.xx.xx drivers)

---

### Post by Yellow Pasque on 2008-07-25
```
gksudo gedit /etc/usplash.conf
```

---

### Post by sges on 2008-07-25
> **Temüjin said:**
> ```
gksudo gedit /etc/usplash.conf
```

I edited the file. hres=1440, vres=900 
then I did **sudo update-initramfs -u**

No errors. 

Reboot

Still looks the same to me.

Maybe I issued the update-initramfs command incorrectly? I did not quite understand the man page. Should I issue a -c on the kernel?

---

### Post by sges on 2008-10-18
I tried again and it worked. Thanks

---

### Post by AGSzabo on 2008-10-18
i tried it, too and it did not work.

---

