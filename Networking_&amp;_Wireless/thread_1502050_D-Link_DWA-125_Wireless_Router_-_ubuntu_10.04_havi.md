---
title: "D-Link DWA-125 Wireless Router - ubuntu 10.04 having issues"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by matjnewton on 2010-06-05
Hi all

I've done my best to make this work but being an Ubuntu n00b isn't helping. I've been trying to get my dongle to work. I've read through a ton of threads and haven't understood much. :)

Steps taken so far:

1. Installation of ndiskwrapper (or however it's spelled). The hardware is showing as "installed" when I load up the windows network drivers screen but isn't showing up elsewhere

2. Iwconfig:

> 
lo        no wireless extensions. 

eth0      no wireless extensions. 


3. lsusb:

> Bus 001 Device 003: ID 07d1:3c0d D-Link System 

is the only line that matters.

4. sudo modprobe rt3070sta:

> password returned me to the blank command line


5. sudo gedit /etc/modprobe.d/blacklist.conf

blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib

---

sudo rmmod rt2800usb
> ERROR: Module rt2800usb does not exist in /proc/modules 

Hope someone can help!

---

### Post by David006 on 2010-07-25
I have resolved this (for me), without using NDIS/wrapper or compiling driver code.

see:
[http://ubuntuforums.org/showpost.php...7&postcount=15](http://ubuntuforums.org/showpost.php...7&postcount=15)

---

### Post by ario on 2010-09-30
> **David006 said:**
> I have resolved this (for me), without using NDIS/wrapper or compiling driver code.

see:
[http://ubuntuforums.org/showpost.php...7&postcount=15](http://ubuntuforums.org/showpost.php...7&postcount=15)

Sure you resolved this! But your link is broken. Let me post a similar response:
> I have my DWA-125 adapter worked finally. Here you can see my solution:
[http://ubuntuforums.org/showpost.php...something...somethingelse!](http://ubuntuforums.org/showpost.php...something...somethingelse!)
Please do not respond if you do not know what to say or simply post your link again.

---

### Post by ario on 2010-09-30
> **matjnewton said:**
> Hi all

I've done my best to make this work but being an Ubuntu n00b isn't helping. I've been trying to get my dongle to work. I've read through a ton of threads and haven't understood much. :)

Steps taken so far:

1. Installation of ndiskwrapper (or however it's spelled). The hardware is showing as "installed" when I load up the windows network drivers screen but isn't showing up elsewhere

2. Iwconfig:



3. lsusb:



is the only line that matters.

4. sudo modprobe rt3070sta:



5. sudo gedit /etc/modprobe.d/blacklist.conf

blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib

---

sudo rmmod rt2800usb


Hope someone can help!

As far as I know, And I'm testing it right now, Ubuntu 10.04 have the drivers needed for DWA-125 built-in. So you do not need to install any driver. I mean when you connect your USB wireless, Ubuntu will automatically detects it and it's led is blinking.
Heres my dmesg output after plugging it in:
```
[  522.716160] usb 1-1: new high speed USB device using ehci_hcd and address 3
[  522.953661] usb 1-1: configuration #1 chosen from 1 choice
[  523.006099] phy1: Selected rate control algorithm 'minstrel'
[  523.006757] Registered led device: rt2800usb-phy1::radio
[  523.006780] Registered led device: rt2800usb-phy1::assoc
[  523.006801] Registered led device: rt2800usb-phy1::quality

```
Now I don't know how to get it working. Science I'm on Ubuntu 10.04 Server Edition, I do not have/want to work with any GUI.
Anyone knows a CLI solution? I want to get it connected to my laptop in Ad-Hoc mode.
Please remember, any attempt to run this command:
```
sudo ifconfig wlan0 up
```
will cause the wireless adapter's led to turn off and stop blinking, and the terminal to hang up!
Thanks in advance.

---

