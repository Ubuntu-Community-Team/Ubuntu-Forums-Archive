---
title: "Wireless not working on multiple devices when running ubuntu 13.04"
date: 2013-03-26
forum: Networking &amp; Wireless
---

### Post by Zakalibal on 2013-03-26
Hi Guys!

I have just updated my netbook os from 12.10 to ubuntu 13.04.
So far all good....almost....
The only problem i found: i cannot connect with other devices to the net using the same wireless connection.
It's like that Ubuntu sucks all connection speed and doesnt let the other devices in.
Can anybody help?
Thabks!!

---

### Post by athampan on 2013-03-26
Can you provide some details about your network?  What steps have you taken to diagnose your problem - to figure out that it is indeed ubuntu 13.04 that is hogging the network?

---

### Post by HenkJan85 on 2013-05-05
I'm experiencing the same problem.
Just after upgrading I'm having problems with my mobile phone and tv-mediaplayer. Those devices can connect to wifi, but not send or receive anything.
My notebook isn't **"**using**" **speed, it's just idle.
Zakalibal, what wireless card do you use? You can figger out by pasting this into a terminal: [FONT=courier new]lspci | grep -i wireless[/FONT]
This is my wireless card: Broadcom BCM4313
Maybe not very useful, but I'm using the wl driver. I will try another driver later.
Someone at askubuntu.com noticed the same problem: [http://askubuntu.com/questions/287426/after-upgrading-to-ubuntu-13-04-from-12-10-other-devices-are-not-able-to-keep-c](http://askubuntu.com/questions/287426/after-upgrading-to-ubuntu-13-04-from-12-10-other-devices-are-not-able-to-keep-c)

---

### Post by adamklempner on 2013-05-05
Same problem here!  I have 8 devices connected to my router and only some of them can communicate with the router now that i have upraded my laptop to 13.04.  Disconnecting the this laptop allows everything else to work.  There are no conflicting IPs, not sure what else to look at, or what could even cause this.

Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

---

### Post by adamklempner on 2013-05-05
Problem solved!  HenkJan's comment about broadcom was the give away.  The proprietary driver is the issue.  

Go to:  System Settings -> Software and Updates -> Additional Drivers tab -> Check "do not use the device" under the Broadcom section to disable the proprietary drivers and switch to Ubuntu's open driver.  Press Apply then restart the computer.  All should be good.

---

### Post by HenkJan85 on 2013-05-14
I don't have the option to use the [COLOR=#000000]open driver. I suppose I removed this a while ago because the connection was very unstable.
What is the name of the open source driver? I might try install it manually.[/COLOR]

---

### Post by praseodym on 2013-05-14
The open-source driver "brcmsmac" is already part of the kernel, but the proprietary firmware is missing:
```

wget media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_070513.tar.gz -C /lib/firmware
```
After that remove the other driver and its config:
```

sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
```
Shutdown, remove any current source for ten minutes and reboot.

---

