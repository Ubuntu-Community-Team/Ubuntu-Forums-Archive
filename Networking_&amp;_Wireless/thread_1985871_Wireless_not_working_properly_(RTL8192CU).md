---
title: "Wireless not working properly (RTL8192CU)"
date: 2012-05-23
forum: Networking &amp; Wireless
---

### Post by AvixK7 on 2012-05-23
I have a netis wf-2109 usb wireless adapter that I can't get to work reliably.

It uses the RTL8192cu.

I've tried using preinstalled driver and ndiswrapper.

I would really appreciate some troubleshooting tips :)

```
lsusb
``` 
Bus 002 Device 005: ID 0bda:8178 Realtek Semiconductor Corp.

EDIT: After updating the distro via ethernet cable, I ran the install.sh script from the manufacturer's official linux driver. The wireless appears to be working fine. I believe I'll have to repeat the install script everytime there's a kernel update, but that's no big deal for now.

---

### Post by AvixK7 on 2012-05-24
It appears that I have to install the driver everytime I boot the OS. Once the driver is installed, it works great.

How can I get the driver to remain installed?

Thanks for the help :)

---

### Post by chili555 on 2012-05-24
What is the name of the driver it installs? r8192cu or similar? Please try this:```
sudo su
echo r8192cu >> /etc/modules
exit
```Of course, substitute the exact name of the driver, without the .ko extension, if it isn't r8192cu.

---

