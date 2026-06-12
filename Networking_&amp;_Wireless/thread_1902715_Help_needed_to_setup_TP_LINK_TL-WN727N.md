---
title: "Help needed to setup TP LINK TL-WN727N"
date: 2011-12-31
forum: Networking &amp; Wireless
---

### Post by lintoon on 2011-12-31
Hi can anyone point me in the right direction please.

I have just purchased a TP LINK TL-WN727N usb wireless adapter to use with my Ubuntu 11.10 installation (running Unity).  It is shown as a working device here.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB)

lsusb shows my device as

Bus 001 Device 006: ID 148f:5370 Ralink Technology, Corp

iwconfig shows no wlan0 connection.   It only shows my ethernet and local connections (eth0, eth1 and lo)

I read that my adapter (tp link tl-wn727n) only works with the rt2870sta driver and I had to disable the other drivers in /etc/modprobe.d/blacklist.conf.  

I added the following to the conf file (as recommended here [http://ubuntuforums.org/showthread.php?t=1340584](http://ubuntuforums.org/showthread.php?t=1340584)).

#disable the misbehaving RALink drivers.
#The WN727N only needs the rt2870sta driver.
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib

And that's about as far as I've got.  Can anyone help me get this usb adapter working.  I'm not asking for step by step instructions (although that would be nice), just any pointers to get me further forward.

I've also searched for firmware for my adpater but could not find it on the manufacturers website.

---

### Post by praseodym on 2011-12-31
Hi,

the driver rt2870sta is no longer part of the Linux kernel (since 3.x). Try to add the device ID to the driver rt2800usb:

```
echo 'install rt2800usb modprobe --ignore-install rt2800usb ; /bin/echo "148f 5370" > /sys/bus/usb/drivers/rt2800usb/new_id' | sudo tee /etc/modprobe.d/rt2800usb.conf
sudo modprobe -v rt2800usb
```
and replug the stick. If it works you need to take those drivers off the blacklist afterwards.

---

### Post by lintoon on 2011-12-31
Thank you for that.  I'll try it tomorrow and post the results.

Cheers.

---

### Post by lintoon on 2012-01-01
You are a genius.  Thank you so much.  I have spent hours looking into this and nowhere did it mention the sta driver wasn't part of the kernel.

I ran the commands you gave and BAM the wireless just kicked into life and saw my network.

For the record it is working with wpa and seems to be a decent connection.  I am currently watching streaming tv and it's flawless (so far).  For anyone else who is reading, I don't have an 802.11n router so I can't confirm whether n is as reliable as my g connection.

---

### Post by lintoon on 2012-01-01
Update for anyone who needs it:

The wireless module did not start after rebooting so I ran 
sudo modprobe -v rt2800usb

and the wireless worked immediately.

I then removed the blacklisted drivers (which I added earlier) from /etc/modprobe.d/blacklist.conf

Next I added rt2800usb to /etc/modules.  Rebooted and my wireless starts up automatically.

Sorted :)

---

### Post by Falc7 on 2012-05-13
Just wanted to say thanks for leaving us the answer here, this thread has helped at least 3 people within the last 24 hours alone :)

---

### Post by jsroth on 2012-08-22
> **Falc7 said:**
> Just wanted to say thanks for leaving us the answer here, this thread has helped at least 3 people within the last 24 hours alone :)

Just saved my life as well. This is great! There are so many "solutions" to this problem, but this one actually worked with current systems.

Works for Mint 13 as well in case someone uses that.

---

