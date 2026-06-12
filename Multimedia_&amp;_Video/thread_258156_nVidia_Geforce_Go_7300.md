---
title: "nVidia Geforce Go 7300"
date: 2006-09-15
forum: Multimedia &amp; Video
---

### Post by bitoiu on 2006-09-15
Hi,

Yesterday I bought an asus laptop. It works fine in ubuntu with exception on the graphics card. The two major problems were

-> Max Resolution : 1024 . 768
-> "unstable refreshes"

After reading almost every article and after trying the official driver ( the general one that's on nVidia site, that stopped when it couldn't find the kernel-source-tree despite my efforts) I found two methods.

1) The one from the italian user who had a script ( I guess a well know for ppl with this problem ) that I dind't follow because I think mu graphics card don't match the criteria.

2) A guide from ubuntu forums ( i guess ) that told to install the drivers from automatix ( nv drivers i guess ) . So i tried this method and solved the unstable refreshes, but i stiil have a VERY BRIGHT screen in ubuntu, and the resolution is the worst still the same.

Can someone please help me. I bought this pc mostly for ubuntu since I need it to program. In last case I just need the color right and resolution. Just so i can open my emacs and eclipse in peace...

Please, someone out there....

---

### Post by psygol on 2006-09-15
This ASUS have a max. resolution of 1280x800, no?. Once you have installed the nvidia drivers, edit the xorg.conf and add manualy the new resolution.

SubSection     "Display"
        Depth       24
        Modes      "1280x800" "1024x768" "800x600" "640x480"
EndSubSection

---

### Post by bitoiu on 2006-09-16
Hi,

I'll try that and keep u posted.

Thanks very much.

---

### Post by tseliot on 2006-09-17
please post the output of this command:
```
lspci -n | grep 300
```

if your card is not supported by the driver you won't be able to use it.

---

