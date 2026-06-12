---
title: "Wireless Not Showing Up"
date: 2011-06-05
forum: Networking &amp; Wireless
---

### Post by justingo147 on 2011-06-05
My Wireless isn't popping up in the network tab. I'm running off of a ethernet cable. I tried reinstalling the drivers using Windows Wireless Drivers, it said it "detected hardware" but it didn't really enable my wireless. I'm on Ubuntu 11.04. Help please?:(

---

### Post by ivanovnegro on 2011-06-05
Have you tried yet to go to System-> Additional drivers, that could maybe install your drivers for wireless?

---

### Post by chili555 on 2011-06-05
> I tried reinstalling the drivers using Windows Wireless Drivers,It sounds like you are using ndiswrapper and the Windows .inf and, possibly, .sys file. Did you use the Windows XP .inf file? Vista, 7, 3.0, etc. just won't work. Here is a snip from the manual page for ndiswrapper:> DESCRIPTION
       ndiswrapper is two parts: user space tool that is used to install Windows **XP**  drivers  and kernel module to load the Windows **XP** drivers. Both are called ndiswrapper.

---

