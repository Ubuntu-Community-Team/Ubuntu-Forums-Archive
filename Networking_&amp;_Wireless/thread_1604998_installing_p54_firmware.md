---
title: "installing p54 firmware"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by asg55 on 2010-10-24
I'm new to ubuntu.
I'm trying to install p54. I got the firmware from [http://wireless.kernel.org/en/users/Drivers/p54#Contact](http://wireless.kernel.org/en/users/Drivers/p54#Contact)

the instructions say

There are several different firmwares for different hardware. You have  to pick the right one, download, rename to the listed name and put it  into the right place... Normally this should be /lib/firmware. However  some distributions put firmware in a different place. 

what do I rename it to and where exactly do I place the file?

---

### Post by Der Ritter on 2010-10-24
> **asg55 said:**
> I'm new to ubuntu.
I'm trying to install p54. I got the firmware from [http://wireless.kernel.org/en/users/Drivers/p54#Contact](http://wireless.kernel.org/en/users/Drivers/p54#Contact)

the instructions say

There are several different firmwares for different hardware. You have  to pick the right one, download, rename to the listed name and put it  into the right place... Normally this should be /lib/firmware. However  some distributions put firmware in a different place. 

what do I rename it to and where exactly do I place the file?

The name is listed next to the download link. For example, isl3887usb. Then stick it in /lib/firmware as the instructions say.

```
mv 2.13.24.0.lm87.arm isl3887usb
sudo mv isl3887usb /lib/firmware
```

---

### Post by chili555 on 2010-10-24
If you have a wired ethernet connection, you could also do:```
sudo apt-get install linux-firmware-nonfree
```

---

### Post by asg55 on 2010-10-28
i tried the sudo apt-get install linux firmware command, but It still won't detect the wusb54g wireless card...is there another step?

---

