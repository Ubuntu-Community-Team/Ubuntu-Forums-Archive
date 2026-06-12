---
title: "Wifi disasters Oneiric 11.10"
date: 2012-01-23
forum: Networking &amp; Wireless
---

### Post by andrew.kunk on 2012-01-23
So after the upgrade to 11.10 from 11.04 the wifi on my computer has been messed up. I uninstalled network manager, and tried to install wicd, which didn't work. and so i have reinstalled network manager via packages (.deb files). This did not install it until i clicked nm-applet in /usr/bin/nm-applet. Finally I got the notification in the upper right hand corner, however it is just the empy quarter circle. the network light on my laptop is on, and the hardware wifi switch is in the on position. however I still can't get wifi. Please walk me through how I can fix this

---

### Post by andrew.kunk on 2012-01-23
and important to note that when I do rfkill list it shows that dell-wifi is hard and soft blocked

---

### Post by varunendra on 2012-01-24
> **andrew.kunk said:**
> and important to note that when I do rfkill list it shows that dell-wifi is hard and soft blocked
Then recheck the physical switch and BIOS to make sure it is enabled at these places. If you dual boot with windows, make sure it is turned on there, then reboot into Ubuntu while it is still 'On'.

If all of the above is already ok, please post these outputs then:
```
uname -rm
lspci -nnk | grep -iA2 net
ifconfig -a
iwconfig
rfkill list all
lsmod
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
```

---

