---
title: "Onboard ethernet no likes me??"
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by ets2006 on 2009-12-21
Hello people.
My wired ethernet controller doesn't seem to be working when I'm using the kernel 2.6.31-16 generic. It works on 2.6.31-15 generic, otherwise you wouldn't be seeing this.
I've got a "Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)" according to lspci.
Any ideas?? I've tried modprobing "b44" but to no avail.
Any help or suggestions would be appreciated. Thanks!

---

### Post by hugmenot on 2009-12-21
What does the kernel say when you modprobe b44?

"dmesg" shows kernel messages.

---

### Post by ets2006 on 2009-12-22
Well... I rebooted back into 2.6.31-16 and Network Manager connected. I unplugged the cable, rebooted again into 2.6.32-16 and then waited for Network Manager to load, then plugged in my cable. It worked, I am connected.
I think that the system updates I done after posting the last message may have fixed it, but I'm not sure.
There seems to be a lot of posts(like this one [http://ubuntuforums.org/showthread.php?t=1356918](http://ubuntuforums.org/showthread.php?t=1356918)) about this particular ethernet controller anyways... is somebody able to enlighten me??

---

