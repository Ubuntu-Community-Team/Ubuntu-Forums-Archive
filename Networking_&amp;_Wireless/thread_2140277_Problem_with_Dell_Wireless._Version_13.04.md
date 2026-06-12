---
title: "Problem with Dell Wireless. Version 13.04"
date: 2013-04-29
forum: Networking &amp; Wireless
---

### Post by ChessMasterJoe on 2013-04-29
Hey guys, 

I'm not sure if anyone remembers me, but I posted here a few months ago when I could get my Dell Laptop to pickup wifi signals. I'd suggested taking a look at the old thread for details regarding the situation. [http://ubuntuforums.org/showthread.php?t=2081424](http://ubuntuforums.org/showthread.php?t=2081424) In short, I had to install the 64 bit version of 12.10 and follow a few steps to download the drivers/software. Much thanks to Hadaka and Chill555.

Anyway, I got on my computer early and saw that an update was available. Ubuntu 13.04! Oh boy I thought, I can't wait to install this. Right....Well, couple hours later, computer rebooted.....NO WIFI! I went back to the old thread and tried to old steps....didn't work. (There's a chance I'm messing this up since I basically have no clue what I'm doing.) Anyway, I'm quite lost. 

Also, how do I know if I have the 32 or 64 bit version. I would assume there's some extremely simple way to check. 

Thanks guys.

---

### Post by zhjsh on 2013-04-29
i have the same question in ubuntu 13.04 yet ,8188cus chip .


cc1: some warnings being treated as errors
make[2]: *** [/home/zhjsh/8188c/core/rtw_cmd.o] &#38169;&#35823; 1
make[1]: *** [_module_/home/zhjsh/8188c] &#38169;&#35823; 2
make[1]:&#27491;&#22312;&#31163;&#24320;&#30446;&#24405; `/usr/src/linux-headers-3.8.0-19-generic'
make: *** [modules] &#38169;&#35823; 2

but this error does not exist in ubuntu 12.04.

---

### Post by boonkui on 2013-05-01
Got the same problem. Found a working solution at [https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/](https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/). I tested it to work on Ubuntu 13.04 32-bit desktop. Rough steps: Blacklist 8192CUs drivers, reboot, install deb package, reboot, done.

---

### Post by Hadaka on 2013-05-01
Hi, oh no ! :P
to see if your are 32 or 64 please do...
```
arch
```
thanks.

---

