---
title: "b43 xubuntu"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by jan@ejdnb.nl on 2011-11-09
i just installed xubuntu on an old laptop. Afterwards i installed the drivers for an linksys B43 pcmcia wifi card. Everything works more or less well. De only problem i have is that i have to manually start the driver with "sudo modprobe b43". Is there a way to do this automatically. I have only a basic knowledge of linux - xubuntu.

Thanks for the help
Jan

---

### Post by chili555 on 2011-11-09
Please try this; open a terminal and do:```
sudo su
echo b43 >> /etc/modules
exit
```Upon reboot, you should be all set.

---

### Post by jan@ejdnb.nl on 2011-11-09
thank you very much. I saw that i put an extra line in the modules file. De modules file starts the kernel modules at boot. Learned something new.

---

