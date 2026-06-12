---
title: "wifi confounded"
date: 2013-01-01
forum: Networking &amp; Wireless
---

### Post by Cimiyaxkin on 2013-01-01
Hi, not exactly a Linux newbie, but confounded by wifi on my Dell D600 latitude with Lubuntu 12.04 LTS. I have it working with some VERY un-elegant workarounds, but wonder if anyone has a simpler fix on this hardware.

I have installed the b43 firmware appropriate for my laptop.

Every time I log in I have to sudo modprobe b43 to "turn on". There has to be a better way....

The wifi drops constantly, sometimes I am up for hours, sometimes every minute or so it drops. I uninstalled Network Manager and installed wicd, however it still drops. I have to open wicd and force it to reconnect. Following a tip in another forum I reinstalled NetworkManager, and now when it drops having Network Manager  spinning its wheels seems to force wicd to reconnect. As I said, a very un-elegant workaround.

I should add I have none of these issues with Linux Mint 13 Cinnamon on my Dell D620 work machine on the same connection. None.

---

### Post by squakie on 2013-01-01
modprobe is loading a kernel module - in this case the b43 driver module.  There is a file in /etc named "modules".  This file says what modules to add at startup.  So, just edit the /etc/modules file, go to the end of the file, and then add the following new line:

b43

Save the file, exit the editor and reboot.  Your wireless should work now.

Also - please post back the output of the following:

lspsci | grep Ethernet

If by chance the wireless adapter is USB, then post back the results of:

lsusb

---

### Post by Cimiyaxkin on 2013-01-01
Here is the results of lspci|grep Ethernet

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)

Not a USB stick, built in broadcom b4306

Thanks, help is appreciated..

---

### Post by squakie on 2013-01-02
It's possible you need a different driver, however, please do add the b43 module to the end of the /etc/modules list first and reboot.  You can do this simply via a terminal window:

sudo echo b43 >> /etc/modules <press enter> and use your normal password.  It won't show as you are typing it.

Then

sudo shutdown -r now <press enter>

---

### Post by Cimiyaxkin on 2013-01-02
I added the b43 to the etc/ modules ( i used nano) it now b43 loads on boot. Doh. I am not sure why I didn't think of that.

Still dropping wifi, but usually reconnects in a second or two. I know there is a legacy  b43 driver out there, but my research told me to stay away from that one on my machine.

Thanks again for your help.

---

### Post by squakie on 2013-01-03
What I don't know is if the STA (wl) driver might be better for you.  Now that you have an internet connection, I would go to Additional Drivers again and let it run.  Maybe it will come up with a better driver for you.

---

### Post by Bucky Ball on 2013-01-03
*Thread moved to **Networking & Wireless***

You are creating an extra problem because wicd and Network Manager will not run simultaneously so one could be killing the other. 

Uninstall one or the other (I would uninstall wicd and start from the beginning), restart the machine and see how that goes.

---

