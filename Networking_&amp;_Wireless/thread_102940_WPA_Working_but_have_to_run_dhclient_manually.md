---
title: "WPA Working but have to run dhclient manually"
date: 2005-12-13
forum: Networking &amp; Wireless
---

### Post by theduno on 2005-12-13
Hi There, I have wpa working with the intel 2200bg thanks to [this guide]("http://www.ubuntuforums.org/showthread.php?t=90450&highlight=wpasupplicant") , the only problem is I have to manually run sudo dhclient eth1 after I boot up each time.......I'm pretty sure this is a stupid question, but how do I automate this process?

thanks everyone

---

### Post by firecat53 on 2005-12-13
I put the following in my /etc/network/interfaces (for madwifi drivers, but should be the same). I have to use static IP, but you should just have to change the iface line to : iface ath0 inet dhcp and remove the address, netmask and gateway lines.

```
auto ath0
iface ath0 inet static
address 192.168.0.110
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid athome
pre-up /usr/local/sbin/wpa_supplicant -wB -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
post-down killall -p wpa_supplicant
```

Good luck!

Scott

---

### Post by theduno on 2005-12-16
thanks Scott that worked, although I had to add "map eth1" as well...took a guess there as "map eth0" was already in

Thanks

---

### Post by firecat53 on 2005-12-16
Happy to help :)

Scott

---

