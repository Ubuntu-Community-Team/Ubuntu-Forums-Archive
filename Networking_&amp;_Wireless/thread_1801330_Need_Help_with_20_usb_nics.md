---
title: "Need Help with 20 usb nics"
date: 2011-07-10
forum: Networking &amp; Wireless
---

### Post by VVAW on 2011-07-10
I have 1 wireless 1 ethernet on laptop
I need to connect 20 usb nics for gns3 lab however I 
only see
eth6-20

when I issue the command
I see them all but ifconfig I do not 
So is there a way/how to delete all nics and start from the beginning
My do list for Sunday

---

### Post by VVAW on 2011-07-10
anybody on how to delete all of the usb nics and reinstall them.

I am thinking the only way to fix this is to re-install ubuntu a new fresh copy which I don't wan to do at all.

I see all nic but using this command

sudo lshw -C network
I will see some of them say something like
eth1-eth9 
disabled etc

It would be great if I could get some help thanks
I even setup a teamviewer session

---

### Post by flash63 on 2011-07-11
> **VVAW said:**
> I have 1 wireless 1 ethernet on laptop
I need to connect 20 usb nics for gns3 lab however I 
only see
eth6-20

when I issue the command
I see them all but ifconfig I do not 
So is there a way/how to delete all nics and start from the beginning
My do list for Sunday

Hello,
probably there is additionally a problem with the power consumption by the USB ports and not all adapters work properly.

Check the adapter and the system-log
```
lsusb
cat /var/log/syslog | egrep 'eth|usb'
```

The configuration can changed manually in the /etc/udev/rules.d/70-persistent-net.rules

A reinitialization is also possible
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
sudo udevadm trigger
```

---

