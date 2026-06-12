---
title: "Belkin F6D4050 USB wireless dongle drivers"
date: 2012-01-28
forum: Mythbuntu
---

### Post by Levo2012 on 2012-01-28
I have just recently installed Mythbuntu 10.04 because none of the later versions want to install onto my old PC. 

I want to use it for a backend system, but I am having issue in installing the drivers for the wireless dongle.

In the past when I have been using Ubuntu 10.04 I have used the method outlined in. 

[http://ubuntuforums.org/showthread.php?t=1509403](http://ubuntuforums.org/showthread.php?t=1509403)

> Go to :
*Applications, Accessories, Terminal*
 
 	Code:
 	lsusb 
Check the output to make sure that your device ID is:
 
 	Quote:
 	 	 		 			 				050d:935a 			 		 	 	 
If it matches, do this:
 
 	Code:
 	sudo gedit /etc/udev/rules.d/network_drivers.rules 
Put in/add [COLOR=red]one[/COLOR] long line [COLOR=black]in the opened file[/COLOR]
 
 	Code:
 	ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="935a", RUN+="/sbin/modprobe -qba rt2870sta" 
Proofread carefully(ensuring that the opened file will be saved in the /etc/udev/rules.d directory), [COLOR=red]save[/COLOR] and close gedit.
 
Next do this:
 
 	Code:
 	sudo gedit /etc/modprobe.d/network_drivers.conf 
Put in/add [COLOR=red]one[/COLOR] long line [COLOR=black]in the opened file[/COLOR]
 
 	Code:
 	install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "050d 935a" > /sys/bus/usb/drivers/rt2870/new_id 
Proofread carefully(ensuring that the opened file will be saved in the /etc/modprobe.d directory), [COLOR=red]save[/COLOR] and close gedit
 
Reboot

This has worked fine when I tried it with Ubuntu 10.04 but it doesn't seem to want to work with Mythbuntu 10.04

When I run the first command the terminal just reads

```
sudo: gedit: command not found

```

Can you let me know if there is something I have to do differently?

If I run lsusb I get the following

```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1b80:c160 Afatech 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 050d:935a Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by ecwanet on 2012-01-30
gedit is probably not pre-installed with 10.04, I know it's not in 11.10, so you have to install it from the Ubuntu Software Centre application.

When you have opened Software Centre (look in the applications menu) you can search for text editors in accessories. When you've found the entry for gedit, just highlight it and click on the install button.

---

