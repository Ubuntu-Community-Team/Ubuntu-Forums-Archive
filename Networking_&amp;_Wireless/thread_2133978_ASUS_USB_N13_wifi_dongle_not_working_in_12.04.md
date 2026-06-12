---
title: "ASUS USB N13 wifi dongle not working in 12.04"
date: 2013-04-09
forum: Networking &amp; Wireless
---

### Post by ndfreeman on 2013-04-09
I need help! I have a fresh install of 12.04, no ethernet options, and a non-working ASUS USB wifi stick.

lsusb returns the relevant line:
```
Bus 002 Device 004: ID 0b-5:17ab ASUSTek Computer, Inc.
```

I followed this advice of one other thread on this topic, downloaded the realtek driver for my specific usb stick, and ran the following code:
```

cd ~/Downloads
unzip RTL8192xC_USB_linux_v3.4.4_4749.20121105.zip
cd RTL8192xC_USB_linux_v3.4.4_4749.20121105
chmod 755 ./install.sh
sudo ./install.sh
```

After that I added "8192cu" to the end of the file /etc/modules

The internet worked for about 10 minutes, and as apt-get update was running, it suddenly stopped working. Keep in mind, I never lost internet on any other device. Since the initial connection, nothing has worked since.

At this point, my wifi is stuck in a perpetual state of attempting to connect and I am at a loss. Thanks in advance.

---

### Post by ahallubuntu on 2013-04-09
~

---

### Post by ndfreeman on 2013-04-09
That did the trick! When I first followed the other thread, I didn't realize that blacklist.conf was read-only, but now I made sure to exclude the old drivers and it seems to be working. I'll mark the thread as solved once I successfully update. Many thanks :)

---

### Post by SUPERFITTER on 2013-04-10
Some of us have the same problem with ASUS USB N13 wifi dongle not working in 12.04. Can you please explain what steps you did to fix the problem and how you preformed each step.

Thank you from all us ASUS USB N13 wifi dongle users!!!!!

---

### Post by ahallubuntu on 2013-04-10
~

---

### Post by SUPERFITTER on 2013-04-11
I closed the terminal before I could do the following:

[I]You may need to blacklist your existing driver by adding these three  items to the end of the file /etc/modprobe.d/blacklist.conf :

     Code:
[/I]

blacklist rtl8192cu blacklist rtl8192c_common blacklist rtlwifi[I]

and add the name of the new module "8192cu" to the end of the file /etc/modules so it will be automatically loaded at each boot.[/I]

How do I fix this?

Thank You

---

### Post by SUPERFITTER on 2013-04-13
chili555, has found the answer: [http://ubuntuforums.org/showthread.php?t=2133710&page=3](http://ubuntuforums.org/showthread.php?t=2133710&page=3)

Thank you chili555

---

### Post by Darth Buh on 2013-05-08
I need help with this too!!!

I have the RTL8192CU chipset in the device and have tried installing the new drivers.

Here's the problem --

When I add blacklist rtl8192cu to the blacklist.conf file as sudo, and plug in the N13, the computer crashes and the Caps Lock and Scroll Lock lights on the keyboard flash on and off.  This continues through reboots until either I 1. Remove the N13 and reboot or 2. Remove that blacklist entry.

Help?

---

