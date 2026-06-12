---
title: "Wireless suddenly stops working until reboot"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by mylifedrive on 2009-12-18
>I have a Toshiba laptop.
I start up my Ubuntu 9.10, and everything works fine, but then, in 15-20 minutes it disconnects, and asks me for my net password. It doesn't matter if I enter it, it will try for a while and then ask again. The only fix is to reboot and then I will have another 20 minutes of net.

---

### Post by Dark_Stang on 2009-12-18
What type of wireless card do you have in there?

---

### Post by mylifedrive on 2009-12-19
Atheros?

---

### Post by drpjkurian on 2009-12-20
> **mylifedrive said:**
> Atheros?
Download the following packages using synaptic package manager.
linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic
This may solve your problem

Please type the following command in terminal
```
lshw -C network
```
You will be able to know the type of the card.

Well if it atheros you can install Madwifi drivers according to the instructions in my thread.
it is [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)


With best of luck
Dr Kurian

---

