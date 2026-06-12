---
title: "Problems with networked printers, cupsys and firewall"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by Irihapeti on 2009-02-20
I have a laptop (EeePC with standard 8.04.2) connected via crossover ethernet cable to my desktop computer (also 8.04.2), which is acting as a router to dialup internet. I got that working after some fun & games noted here: [http://ubuntuforums.org/showthread.php?t=1073111](http://ubuntuforums.org/showthread.php?t=1073111)

The desktop has a printer attached to it. Now I have been trying to get network printing to work and been having intermittent success. I finally discovered that I'm getting a number of errors on the laptop like this:

E [21/Feb/2009:15:23:30 +1300] cupsdReadClient: 7 IPP Read Error!

I've discovered that one of the things that causes this is reloading the firewall (on the desktop), or even unloading it altogether, but I think there are other things happening as well. Only restarting the cupsys daemon on the desktop allows printing to proceed.

Has anyone else come across anything of this kind? Any suggestions re things I might have overlooked in setting the network up?

Irihapeti

---

### Post by Irihapeti on 2009-03-01
I've managed to solve the problem, but purely by luck.

I decided to set up the network with dhcp instead of fixed IP addresses. Even before I could configure dhcpd on the desktop (server) machine, I was able to print from the laptop. I've since done so several times. So I don't know what I'd done wrong before, but it's all working now.

---

### Post by dmizer on 2009-03-01
In the future, if you would like to have your thread marked solved, you can use the tag feature. Simply edit the tags and include "solved" as I've done here.

Thanks! :)

---

### Post by Irihapeti on 2009-03-01
> **dmizer said:**
> In the future, if you would like to have your thread marked solved, you can use the tag feature. Simply edit the tags and include "solved" as I've done here.

Thanks! :)

Ah, so that's how it's done now. Thanks.

---

