---
title: "disable wireless network on startup with commands"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by kptsuresh on 2010-07-02
Hi guys,

Please anyone tell me how to turn off wireless network on start up or completely disable by using terminal. Because I had wired network and I do not need wireless network anymore.

Thanks...:)

---

### Post by puppywhacker on 2010-07-02
By commandline you can do somehing like this
```
sudo ifconfig wlan0 down
```

---

### Post by flash63 on 2010-07-02
Hello,
> Because I had wired network and I do not need wireless network anymore.
in this cause you better disable the Driver (Module) for your WLAN-Hardware permanent if there is no Hardware-Switch for Wifi.

Edit the blacklist-file **/etc/modprobe.d/blacklist.conf** with root privileges and add following line at the end:
```
...
blacklist <modulename>
```
Example for Atheros
```
blacklist ath9k
```

Find out the module being used
```
lspci -nnk | grep -i net -A2    # for PCI(e)-Cards
lsusb                           # for USB-Sticks
```
If you still need WiFi, you can load the module manually
```
sudo modprobe <modulename>
```

---

