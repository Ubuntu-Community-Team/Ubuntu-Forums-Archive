---
title: "R8168B/8111 lost driver sometimes (11.10)"
date: 2012-02-22
forum: Networking &amp; Wireless
---

### Post by ayozito on 2012-02-22
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

This is the information from the command lspci | grep 8168 on my 10.04 Ubuntu.

On 11.10 I have problem with NIC. By default Ubuntu doesn't detect it, so I have to install the driver downloaded from Realtek webpage.

The problem is that sometimes seem like whitin the driver is uninstalled and I have to install again, and over and over...

---

### Post by roelforg on 2012-02-22
Let's run through the basic steps:
```

sudo ifconfig -a
sudo cat /etc/network/interfaces
sudo uname -a
sudo cat /etc/resolv.conf
sudo lshw -C network
sudo modprobe -l | grep "8161"
sudo modprobe -l | grep "8111"

```
Note: the lshw command can take a while
If it's possible, please post the dmesg output as well.

---

### Post by zapho on 2012-02-22
Hi guys, just popped on to say that I've got this problem too and I've literally just noticed it.

Like the OP I had to manually install the 8168B driver from Realtek website as ubuntu 11.10 installs the wrong driver by default (8169). I did this when I noticed that my machine was becoming unstable with heavy ethernet traffic. I installed the correct driver and everything was perfect....until I noticed today that my ethernet adaptor isn't present in ifconfig and it turns out I was running off the wifi for the last 2 days! 

Happy to help out as much as I can.

---

### Post by ayozito on 2012-02-23
The same with me. When using these commands it show that my network card is the correct one (8168B) but however, after see that it fail and install driver from Realtek it say: Unload previous driver: **8169**.

---

### Post by roelforg on 2012-02-23
> **ayozito said:**
> The same with me. When using these commands it show that my network card is the correct one (8168B) but however, after see that it fail and install driver from Realtek it say: Unload previous driver: **8169**.
```

sudo modprobe -r 8169

```
Edit: if the new driver works, edit /etc/modules and remove the line containing:
```

8169

```

---

### Post by ayozito on 2012-02-23
I mean that the installer of the driver shows that. It did it by itself.

Right now I have been whole day with a new fresh installation and still 0 problems. Only at the installation but I sttoped it and installed drivers from Realtek and then was fine.

---

### Post by ayozito on 2012-02-25
I really don't understand this...

After 2 days working fine, this morning when I turned on the PC again network problems. Checked and... 8169 driver installed instead of 8168.. Again need to replace it and all fine then.

At /etc/modules  8169 isn't listed (8168 neither)

---

### Post by gobprasad on 2012-02-25
frnds...
      I had also such issues but now it solved.. just look at here 

[http://ubuntuforums.org/showthread.php?t=1931195](http://ubuntuforums.org/showthread.php?t=1931195)

---

### Post by ayozito on 2012-02-25
I haven't any issue related with cable unplugged.

---

### Post by ayozito on 2012-03-09
Today kernel updated and same problem. How can I delete the r8169 driver from kernel so it won't be installed again on future updates?

---

