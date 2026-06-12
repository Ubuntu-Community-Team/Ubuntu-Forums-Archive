---
title: "How do you get the Asus N13 WiFi to be controlled by the Network manager app?"
date: 2011-03-11
forum: Networking &amp; Wireless
---

### Post by nerderello on 2011-03-11
Hi,
I have eventually (a week's work) got my Ubuntu 10.04 to recognise my Asus N13 WiFi dongle (had to compile the source from Ralink with the "y" against the two things it tells you to if you want network manager to work (source that came with dongle wouldn't compile) and then set up rules (for some reason the driver - rt2870sta - wouldn't recognise the dongle until the rule about the vendor and product ID was in place; and the drivers that come with Ubuntu wouldn't recognise it even with the rule in place)). 

Big thank you to chilli555 for all of the posts that got me this far.

I would like to use the Network Manager app that comes with Ubuntu, to control the dongle. At the moment it will aknowledge when the driver has been loaded (have to do a modprobe), but does not "see" any of the many WiFi routers around my house, so I can't click on one to select one.

My only guess on this is that, to get the dongle to work I copied the config file that is part of the driver source files into /etc/Wireless/RT2870, and this is getting in the way. However, I have tried removing it and the network manager still doesn't work. 

Or is it because the network manager needs the dongle to be called "wlan0" and it's called "ra0"? If so, can you aliase this?

thanks in advance.

---

### Post by chili555 on 2011-03-11
Generally, you need to compile *OR* write usb.id rules; not both. Let's analyze where you are so far. Please post:```
lsusb
modinfo rt270sta | grep -i version
ls /etc/Wireless
ls /etc/Wireless/RT2870STA
```> Or is it because the network manager needs the dongle to be called "wlan0" and it's called "ra0"?No. If it is properly installed and working, NM will grab it. What does this tell us?```
sudo iwlist ra0 scan
```> Big thank you to chilli555You are very welcome.

---

### Post by nerderello on 2011-03-11
well this is embarrassing.

I got home to find that I had "gone backwards" and no longer had anything under ra0!

So I undeed everything that I could remember doing. Still nothing. So I copied back the rt2870sta.ko that had come with Ubuntu and put back the rules and the network config.
/etc/udev/network_driver.rules
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt2870sta
```

/etc/modprobe.d/network_drivers.conf
```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id
```

As soon as I re-loaded the module (sudo modprobe rt2870sta) everything sprang into life. It connects to my router and is perfectly controllable through the network manager app. And has "survived" a reboot. ;-)

I'm not sure what went wrong the first time I tried the rules and network config (along with the Ubuntu driver), but this time it's worked.

So, Chili555, sorry to have taken up your time and thank you again for the solution.

---

### Post by chili555 on 2011-03-11
No problem at all. If your wireless is working, I'm happy.

---

