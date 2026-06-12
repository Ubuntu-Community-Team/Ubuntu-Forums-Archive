---
title: "Intel graphics in 9.10"
date: 2010-03-19
forum: Multimedia Software
---

### Post by wrekced1 on 2010-03-19
I just installed 9.10 on my new machine and it only has 640x480 and 800x600 available for resolutions. I read the Intel graphics in Juanty howto. But there's no xorg.conf and the command given there does not create one. Doesn't do anything as far as I can tell.

Anyway here are my questions:

    How is xorg configured in 9.10?
    How do I go about fixing this?

lspci gives this:
$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

My monitor is a:
    Dell E151FP LCD display

My motherboard docs say it's an  "Intel G41" chipset

Thank you,
Keith

---

### Post by gudrade on 2010-03-19
[http://ubuntuforums.org/showthread.php?t=1324239](http://ubuntuforums.org/showthread.php?t=1324239)

---

### Post by wrekced1 on 2010-03-19
Thanks! That works. I had to tweak the settings a bit from what cvt recommended. My monitor likes 60Hz better...
Thanks again,
Keith

---

