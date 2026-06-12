---
title: "no wireless interface available on Ubuntu Intrepid"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by eljuanito on 2009-04-19
I am an Ubuntu newbie and I am having trouble configuring my wireless internet connection with a USB wireless adapter. Here are the specs:
Dell Inspiron B120
Belkin USB wireless adapter fd7050 ID: 050d:705e
Ubuntu 8.10
When I run ifconfig only eth0 and lo are listed, no wlan0. I tried following the directions at [http://linuxsoftwareblog.com/blog/?p=30](http://linuxsoftwareblog.com/blog/?p=30). lsusb shows the adapter fine.
Any ideas why wlan0 is not showing up in ifconfig?
Any help would be greatly appreciated.

---

### Post by pytheas22 on 2009-04-19
This device should work on Ubuntu 8.10 as long as you apply all Ubuntu updates and reboot (the reboot is important).  You can apply updates using the graphical update manager that should appear in your system tray, or you can update manually by typing:
```

sudo apt-get update
sudo apt-get upgrade
```

Then reboot (make sure you choose the kernel at the top of the list at the boot menu--it should be the default) and the device should work.  If not, please post the output of these commands:
```

uname -rm
lshw -C Network
dmesg | grep -e rtl -e wlan
```

---

### Post by eljuanito on 2009-04-20
It works! Problem solved. Thanks a bunch!

---

