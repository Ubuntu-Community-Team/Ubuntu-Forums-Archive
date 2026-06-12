---
title: "WiFi Intellinet 150N + modprobe RT2800USB command"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by ales on 2011-10-15
Hello,


just upgraded to 11.10. Of course like every new version also this one has some issues. I have to type always when I restart this command to make wifi working:

sudo modprobe rt2800usb

After typing it in Terminal, the wifi goes on in 4-5 seconds.

Why I have to do it always manually?

Has someone the same issue?

Ales

---

### Post by ales on 2011-10-15
SOllution for all with this USB wifi also maybe for other who have the RT2xxx/3070 chip.

TYPE IN TERMINAL
[B]sudo su 
echo rt2800usb >> /etc/modules 
exit[/B]

RESTART AFTER

Thanks to widmanne39 for posting this. It makes the permanent solution and no need to type the command always after start.
Thread [http://ubuntuforums.org/showthread.php?p=11350106#post11350106](http://ubuntuforums.org/showthread.php?p=11350106#post11350106)

---

### Post by wildmanne39 on 2011-10-15
Hi, your welcome! I am glad I could help.
Enjoy

---

