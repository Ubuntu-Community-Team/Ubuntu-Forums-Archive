---
title: "Realtek 8192CU keeps disconnecting"
date: 2013-01-16
forum: Networking &amp; Wireless
---

### Post by ZenMasta on 2013-01-16
Hi Guys,
Just revived an old desktop with a clean install of 12.10.

I plugged in a new usb wifi adapter which was plug and play, it detected visible networks and it connected.

BUT it keeps dropping from the network. I will click on the wireless icon to scan for networks and it will show my network but when I click on it the icon just animate as if it is trying to connect. It will ask for a password prompt but after continuing it doesn't connect and eventually it keeps asking for the network password. 

If I choose disconnect then the network is removed from the list and it wont come back.

Sometimes if I unplug the adapter and reconnect it will pick it up and connect just fine. But presently it is not doing so, it keeps asking for the network password, and I can assure you it is the right password.

I'm using [http://www.asus.com/Networking/USBN13/](http://www.asus.com/Networking/USBN13/)

The desktop is in an opposite corner of my office so I was hoping I wouldn't have to hardwire. The base station is only 10 feet away but other devices (my phone) can maintain connections from much farther distances.

---

### Post by ahallubuntu on 2013-01-16
Yes, the driver for the Realtek 8188/8192CU chipset used in this dongle is broken even though it exists in the kernel in 12.04 LTS and 12.10.  You can simply download the latest driver from Realtek and install it, though it requires building in a terminal, and you have to blacklist the older driver so the new one will be picked up.  You want RTL8192CU .  Instructions here:

[http://ubuntuforums.org/showpost.php?p=12318056&postcount=2](http://ubuntuforums.org/showpost.php?p=12318056&postcount=2)

---

### Post by ZenMasta on 2013-01-16
Thanks I tried those instructions. I downloaded RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105
The instructions were simple.

But the outcome is questionable and I've pasted a possible error. 

> 
##################################################
Compile make driver ok!!
##################################################
Authentication requested [root] for remove driver:
ERROR: Module 8192cu does not exist in /proc/modules
Authentication requested [root] for insert driver:
insmod: error inserting '8192cu.ko': -1 Device or resource busy
Authentication requested [root] for install driver:
install -p -m 644 8192cu.ko  /lib/modules/3.5.0-21-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.5.0-21-generic
##################################################
The Setup Script is completed !
##################################################


I guess only time will tell if this works. 

Also, concering the blacklist. As I just downloaded and installed this new driver how is it not going to blacklist the newone if its for the same chipset, wouldn't it go by the same name?

---

### Post by ahallubuntu on 2013-01-17
The new module is called "8192cu" .  The old module is called rtl8192cu" .  So no, blacklisting the old module doesn't block the new module.

The error message you saw is normal (unfortunately misleading).  You must add the new module name "8192cu" to the end of the file /etc/modules.

---

### Post by ZenMasta on 2013-02-07
I tried following your instructions by 
adding 8192cu to the end of /etc/modules
and 
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

to the end of /etc/modprobe.d/blacklist.conf

I rebooted and when I logged back in I got an instant message saying wifi is disconnected. When I click on the wifi icon in the system tray I don't have any connection options.

I disconnected and reconnected the adapter and it connected. But it shows that it is using rtl8192cu driver.

---

### Post by Fernando_Herranz on 2013-12-06
I suffered from the same problem and came up with a workaround: Just keep pinging a random network address (e.g. 192.168.1.1 or google.com). Voilà, steady connection!

---

