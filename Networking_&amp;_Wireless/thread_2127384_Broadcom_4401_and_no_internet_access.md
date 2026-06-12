---
title: "Broadcom 4401 and no internet access"
date: 2013-03-19
forum: Networking &amp; Wireless
---

### Post by whitecrow on 2013-03-19
Just installed Ubuntu 12.04 on a Dell Inspiron 8500.  It has no wireless hardware.  lspci tells me the ethernet controller is bcm4401.  Because I have no driver, the box is mute and without an internet connection.  On another computer, I downloaded what I believe to be the correct linux driver from the Broadcom site.  Unfortunately, it's a tar.gz file.  I have followed the instructions to the letter six times yesterday and six times today without being able to install the driver.  The driver package also contains an rpm but I have no idea how to install that.  So, I need a debian/ubuntu installer for the bcm4401 driver that I can download to usb and move to the mute box.  Any idea where I can get that or what I should do?  I googled other distros that come with broadcom drivers and have downloaded a couple but haven't tried those yet because I would prefer unbuntu on this box.  It runs well and fast and the graphics are great.  Any help?

---

### Post by chili555 on 2013-03-19
There is probably a better way. Please run and post:```
lspci -nn | grep 0200
sudo modprobe b44
dmesg | grep b44
```The pipe symbol | is on the right side of my US keyboard on the same key with\. Thanks.

---

### Post by whitecrow on 2013-03-19
A screen shot of your code results is attached.

---

### Post by chili555 on 2013-03-19
In *dmesg*,we see that the device grabbed the correct driver *b44* very early in the boot process and created an ethernet interface, eth0. Most importantly, we see no errors, glitches, etc. Confirm you have an interface with:```
ifconfig
```If you see an eth0 there, no need to show us, just tell us yes or no. We would like to see:```
nm-tool
```If it's easier, you can jot down the result with a pencil and put it here.

---

### Post by whitecrow on 2013-03-19
ifconfig shows eth0.  Network Manager shows a "disconnected" wired connection using B44 driver.  State is unavailable.  Default is no.  Under capabilities, carrier detect is yes and under wired properties, carrier is off.  An HW address is also listed.

---

### Post by chili555 on 2013-03-19
> under wired properties, carrier is **off**.That usually means there is no cable or the cable is defective. Can you check the cable at both the computer and the router?

---

### Post by whitecrow on 2013-03-19
Dude, I feel like an idiot!  Unresponsive router port.  Cable was good but one port wasn't working correctly when the other three were fine.  Reset router and all is good.  I saw BCM4401 and knew I had had MANY problems with Broadcom drivers and so guessed that was it.  I wasn't able to recall the exact commands to use to determine the driver in use, tho.  Ubuntu mostly works out of the box these days.  You were INCREDIBLY helpful!

---

### Post by chili555 on 2013-03-19
Glad it's working by whatever means! Have fun. I'll take an easy one once in a while. I'm old and I deserve a break!

---

