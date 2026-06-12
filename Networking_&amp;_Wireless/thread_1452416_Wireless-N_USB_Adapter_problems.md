---
title: "Wireless-N USB Adapter problems"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by lunanueva on 2010-04-11
Hello, 

I'm trying to run a Wireless-N USB Adapter off an old pc and can't get it to enable wireless.  The adapter is recognized by the computer and I have installed ndiswrapper, but still no luck...Any help would be greatly appreciated.  Thanks in advance!!!!!!:confused:

---

### Post by 2hot6ft2 on 2010-04-11
I don't know how much help you'll get for 8.10 since it's at the end of its life cycle but.
It would be more help to know what wifi adapter you have.
Open a terminal
Applications > Accessories > Terminal
and run

If internal PCI
```
lspci
```
That's LSPCI in lower case, and post the results.

If it's a USB adapter
```
lsusb
```
That's LSUSB in lower case, and post the results.

---

### Post by Bucky Ball on 2010-04-11
Plug in an ethernet cable and boot up the machine. Make sure you are online. Plug in the adapter. Wait for a few minutes. There is a good chance you will be offered the correct restricted drivers.

Ndiswrapper is basically a thing of the past and not required for most wireless devices anymore. Avoid at all costs as it will block other, correct drivers and firmware and is generally problematic. Also, please include the manufacturer and model of your device and PC.

---

### Post by lunanueva on 2010-04-12
the device i'm trying to run is a Netgear WN111v2 Wireless-N USB Adapter and i'm trying to run it off a Dell Dimension 8200 (old box).  Here is the output from the terminal after running 'lsusb':

Bus 005 Device 002: ID 0846:9001 NetGear, Inc. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


the pc is online and the usb device is mounted, however no restricted drivers were offered after waiting a couple of minutes.

---

### Post by lunanueva on 2010-04-12
Any other ideas???

By the way, thanks for responding.

---

### Post by Bucky Ball on 2010-04-12
In your current situation, with the machine online, cable and USB wireless plugged in, unplug the cable then:

System->Admin->Network

Hit 'Unlock' and input your password. Now, disable the wired device and the enable the wireless device, if it's not already. Does it now start to look for networks? 

Now highlight the wireless device and then click 'Properties'; make sure you have it set up for your situation (static IP, DHCP, Roaming; whatever you need - probably start with enable roaming off, Configuration = AutoConfig (DHCP)); you need the correct ESSID name and WEP or other security key; you need to get these from your wireless router if you don't know them.

Also, in System->Admin->Hardware Devices, is there a driver for the wireless that is disabled? 

Finally, sounds to me like all is happening hardware-wise, you just don't have the correct ESSID and security key in the network set up on the software side.

Keep asking questions and we'll keep trying to answer them! ;)

---

### Post by chili555 on 2010-04-12
Please let us see:```
sudo modprobe ar9170usb
iwconfig
```Thanks.

---

### Post by lunanueva on 2010-04-21
I was able to get the netgear wireless device working perfectly by following this thread that was posted a long time ago.

[http://ubuntuforums.org/showthread.php?t=885520](http://ubuntuforums.org/showthread.php?t=885520)

Thanks to all that offered their help with this problem and thx to msikma for posting the fix back in 2008 and bean1975 for attaching those damn windows drivers that i needed to get the device working!!!


much love to the ubuntu forums. i would be lost in the woods with out this support.

:p

---

### Post by Bucky Ball on 2010-04-21
You are not alone!

---

