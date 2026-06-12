---
title: "Broadcom 802.11 Linux STA driver"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by mjr4189 on 2009-04-05
Alright so i just installed Kubuntu 8.10 and i am trying to get my BCM4328 network card to work.  I am trying to install the proprietary driver that Broadcom offers for Linux users.  I ave gotten through most of it but the last step is giving me a problem.  I need to use the command "insmod <path>/wl.ko", the path is /home/mjr4189/hybrid_wl. The file is there and the path leading to it is correct but i keep receiving the error message "insmod: error inserting '/home/mjr4189/hybrid_wl/wl.ko': -1 File exists". I have no idea what that means i am jsut doing what broadcom told me too do. I am also logged in as root if that is helpful to the situation.

driver: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
steps: [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

Thanks for any help you guys can provide,
mjr

---

### Post by Sam Lars on 2009-04-07
I think it's telling you that the driver is already installed.
Ubuntu already has the STA driver in the kernel.  If it doesn't work for you, then maybe you just need firmware for your card.
You could try renaming that file and then running the insmod again...

---

### Post by superprash2003 on 2009-04-07
post output of the following commands from your terminal
1)iwconfig
2)iwlist scanning
3)lshw -C network

---

### Post by Ayuthia on 2009-04-07
Sam Lars is correct.  The wl module is most likely loaded already from the one that Ubuntu built.  You can verify this by going into the Terminal and typing:
```
lsmod|grep wl
```If it comes back with wl, then it is already loaded.  You can remove that module by doing the following:
```
sudo modprobe -r wl
```After that you can then try the insmod command.

---

### Post by Peasantoid on 2009-04-07
Try System > Administration > Hardware Drivers? Worked for me.

[edit] Oh wait, Kubuntu, duh. Never mind.

---

