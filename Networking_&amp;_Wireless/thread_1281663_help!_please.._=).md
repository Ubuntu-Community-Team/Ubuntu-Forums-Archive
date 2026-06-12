---
title: "help! please.. =)"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by tophatandy on 2009-10-03
hokay, so heres the story:

recently bought 1005ha. decided linux was needed. installed 9.04. as you might know both of the NICs in the eee 1005ha don't work by default. I installed the drivers for the wired NIC. I then did a kernel update so that i could get the wireless drivers included with the next kernel. after updating i did a reboot. 

no wireless.

so of course i punched 

```
uname -r
```

in, and got back 
```
2.6.28-15-generic
```

so i was messing around in the modprobe man pages trying to find the command to list which drivers are installed, which i couldn't find. i am assuming that the ath9k driver installed as neeeded. anyone know that command or any suggestions on how to get my wireless up?

---

### Post by GeorgeVita on 2009-10-03
Hi **tophatandy**,
I cannot directly help but did you noticed thread:
[http://ubuntuforums.org/showthread.php?t=1219931](http://ubuntuforums.org/showthread.php?t=1219931)

(possibly post there a question)

Regards,
George

---

### Post by t0mppa on 2009-10-03
You can run **lsmod** to list all modules that are currently loaded and for instance **lsmod | grep ath9k** to see if ath9k is loaded. Another way to check is by running **lshw -C network**, which will list the status of your network interfaces and their drivers.

Also, to install ath9k, you only have to install the *linux-backports-modules-jaunty* through apt-get or Synaptic or by compiling the newest [compat-wireless]("http://linuxwireless.org/en/users/Download") by hand.

---

### Post by tophatandy on 2009-10-03
thanks for the help. i realized what was going on. everything after the kernel update was working fine, i was just right clicking instead of left clicking on the network manager tray. i felt like an idiot.

---

