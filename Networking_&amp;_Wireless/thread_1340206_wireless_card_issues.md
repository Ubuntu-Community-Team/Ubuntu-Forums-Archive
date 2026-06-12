---
title: "wireless card issues"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by trombonecricket on 2009-11-28
Hi I just made the switch from windows to ubuntu on my dell laptop. Ubuntu didn't detect my wireless card and the help menu told me how to use a windows driver. But it told me I needed the .inf file. When I downloaded the driver it was only one file and it was .exe so what do I do? By the way, I'm using Hardy Heron. Also, where I live I don't get any wifi so I use a verizon usb modem. It has to install software to work and it usually autoruns the setup. But it isn't doing it with ubuntu and I can't open it manually. Would I be able to do this through Wine? Thanks!

---

### Post by nixscripter on 2009-11-28
It might be a self-extracting archive. Try running this in a terminal: ```
unzip driver.exe
``` and see if it uncompresses into an INF file and a SYS file (which is what one would expect). If that doesn't work, you can always install **wine** and execute it.

Hope this helps.

---

