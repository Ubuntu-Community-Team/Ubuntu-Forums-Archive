---
title: "Wicd drops connection after suspend"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by Tyke91 on 2009-12-28
Hey there. using ubuntu 9.10 with the wicd network manager. After I come out of suspend, wicd can no longer connect to my router. I've tried restarting the wicd daemon (/etc/init.d/wicd stop and /etc/init.d/wicd start), and then restarting the client and daemon together, but I've had no luck. The only solution seems to be a reboot :(

I've got a Broadcom Corporation BCM4312 802.11b/g network controller (Using a custom compiled module to run it since ubuntu does not support it out of the box)

---

### Post by shredder12 on 2009-12-29
I  have the same wireless card but i don't think I have ever faced this problem.. 
btw.. I use network manager.
It seems to be a bug to me.. 
well, it seems stupid but have you tried turning the wireless switch on nd off again..nd the usual restaring network.

---

### Post by djkrisx on 2010-01-14
> **Tyke91 said:**
> Hey there. using ubuntu 9.10 with the wicd network manager. After I come out of suspend, wicd can no longer connect to my router. I've tried restarting the wicd daemon (/etc/init.d/wicd stop and /etc/init.d/wicd start), and then restarting the client and daemon together, but I've had no luck. The only solution seems to be a reboot :(

I've got a Broadcom Corporation BCM4312 802.11b/g network controller (Using a custom compiled module to run it since ubuntu does not support it out of the box)



hey I have the same problem I have tried a few things like:

gksudo gedit /etc/pm/config.d/00sleep_module and SUSPEND_MODULES="ath9k" 
 
 sudo /etc/init.d/NetworkManager restart turning wlan0 on and off 
 but I had no luck so far. Has anyone reported this bug? I like 9.10 but restarting the system every time after suspend its really anoying...

---

### Post by utkjamie on 2010-02-10
There hasn't been a follow-up in this thread in 3 weeks. Does that mean there is no known solution?

---

### Post by uhhhh2 on 2010-02-21
Try this (substitute ath_pci for the name of your driver):

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/275692](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/275692)

---

### Post by c_07 on 2010-03-11
I can confirm that the workaround linked to by uhhhh2 works for my Broadcom 4311 rev. 01 wireless card using the official drivers from Broadcom. I created the file /etc/pm/config.d/01-modules and added the line "SUSPEND_MODULES="wl"" to it, and the problem seems to be resolved.

Note that I use NetworkManager instead of WiCD, but the results should be the same.

Thanks uhhhh2!

---

