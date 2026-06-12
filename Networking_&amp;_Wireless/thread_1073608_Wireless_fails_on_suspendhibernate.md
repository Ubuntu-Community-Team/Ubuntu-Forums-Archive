---
title: "Wireless fails on suspend/hibernate"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by drewcoon on 2009-02-18
Hey everybody,

 I'm running Ubuntu on my college laptop (an IBM Thinkpad T43), and everything is working awesome, minus the fact that using the suspend feature kills my wireless until I reboot.

 I googled my problem and found a possible solution that involves editing /etc/default/acpi-support , and adding "networking" to the STOP_SERVICES section to tell it to stop networking on suspend. However, this isn't working for me. I also tried doing a different acpi-support tweak to stop asking for my password on resume, and it also had no effect (It seems to me that Ubuntu isn't even acknowledging my acpi-support changes).

 I'm using 8.1 Intrepid Ibex and my wireless card is an
Atheros Communications Inc. AR5212 802.11abg NIC
according to lspci. I believe my wireless driver is madwifi (whichever one comes with the disk, my wireless worked out of the box).

 Does anybody have any possible solutions to my problem? This is the closest I've ever gotten to having a working suspend on Ubuntu, so I'd be super happy if I could just get my wireless to resume with the laptop :)

Thanks!

EDIT I found a working solution (post #3).

Did they remove the "mark thread as solved" tool? I can't find it so I'll just edit the title :|

---

### Post by danmarycap on 2009-03-12
Did you ever find a solution?  If not, please check out these posts.

-Dan

[http://ubuntuforums.org/showthread.php?p=6883391#post6883391](http://ubuntuforums.org/showthread.php?p=6883391#post6883391)

[http://ubuntuforums.org/showthread.php?p=6883479#post6883479](http://ubuntuforums.org/showthread.php?p=6883479#post6883479)

---

### Post by drewcoon on 2009-03-20
Yes I found a solution, Somebody suggested that I create a new file at

/etc/pm/config.d/madwifi

and add a single line,
```
SUSPEND_MODULES=ath_pci
```

Wireless now works great, but thanks for the help :)

---

