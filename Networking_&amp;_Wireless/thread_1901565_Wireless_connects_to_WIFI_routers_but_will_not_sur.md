---
title: "Wireless connects to WIFI routers but will not surf net"
date: 2011-12-28
forum: Networking &amp; Wireless
---

### Post by zuerston on 2011-12-28
Hello
I did as in your pics and still no go :D

---

### Post by mikewhatever on 2011-12-28
There isn't a wireless device under 'lspci'. Is it a usb device? Do you have any info on it?

---

### Post by zuerston on 2011-12-28
Hello
I did as in your pics and still no go

---

### Post by wildmanne39 on 2011-12-28
Hi, you have two drivers installed run this command please:
```
sudo apt-get purge b43-fwcutter firmware-b43-installer
```
Then unplug wired connection and reboot.
Thanks

---

### Post by zuerston on 2011-12-28
Hello
I did as in your pics and still no go

---

### Post by wildmanne39 on 2011-12-28
Hi, unplug the wired connection then run the command also instead of rebooting just run this command:
```
sudo modprobe rtl8187
```
Thanks

---

### Post by zuerston on 2011-12-28
Hello
I did as in your pics and still no go

---

### Post by zuerston on 2011-12-28
Hello
I did as in your pics and still no go

---

### Post by wildmanne39 on 2011-12-28
Hi, let's dig a little deeper.

Please post output of with the wired connection unplugged:
```
nm-tool
```
```
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e rtl -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by zuerston on 2011-12-29
Hello
I did as in your pics and still no go

---

### Post by wildmanne39 on 2011-12-29
Hi please run these commands now that you are connected to the router.
```
iwconfig
```
```
dmesg | egrep 'rtl|wpa|wlan0'
```
Thanks

---

### Post by zuerston on 2011-12-31
Hello
I did as in your pics and still no go

---

### Post by zuerston on 2011-12-31
Hello
I did as in your pics and still no go

---

### Post by wildmanne39 on 2011-12-31
Hi, click on the network icon in the top right corner click on edit connections, wireless, make sure yours looks like my screenshots, you do not have to enter the numbers in ipv4 but everything else needs to be the same.

Screen shots in next post.
Thanks

---

### Post by wildmanne39 on 2011-12-31
Sorry I missed putting the screenshots in the previous post.

---

### Post by zuerston on 2011-12-31
Hello
I did as in your pics and still no go

---

### Post by praseodym on 2012-01-01
Hi,

try to deactivate/uninstall the firewall and remove the iptables:
```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

---

