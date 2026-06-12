---
title: "building wireless card module from source code (realtek)"
date: 2006-01-14
forum: Networking &amp; Wireless
---

### Post by kasemodz on 2006-01-14
alright i have a realtek 8185 wireless pci card. I tried installing via ndiswrapper but something keeps messing up. So I went to their website and they have a driver for linux/unix. When I downloaded it there were many files. Here is the installation part of the readme. 
> RTL8185 Linux Driver 11102005 for linux kernel 2.6 Fedora 2

< Component >
The driver is composed of several parts:
    (1)source code
	r818x.tar.gz
	stack.tar.gz

    (2)Script ot build the modules
        makedrv

    (3)Script to load/unload modules
        wlan0up
        wlan0down

    (4)Script and configuration for DHCP
	wlan0dhcp
        ifcfg-wlan0

    (5)Supplicant source code
	wpa_supplicant-0.3.8.tar.gz
    	
    (6)Example of supplicant configuration file
	wpa1.conf

< Installation >
Running the scripts can finish all operations of building up modules from source code and start the nic:

	(1)Build up the driver from the source code
         	./makedrv

    	(2)Load the driver module to kernel and start up nic
    		./wlan0up

	(3)Refer to < Set wireless lan MIBs > to set Wireless LAN specific parameters.

As you can see the readme is for fedora users, my question is how would I build this driver in ubuntu?

---

### Post by Lambert on 2006-01-14
See if this thread will help you.

[http://ubuntuforums.org/showthread.php?t=95879](http://ubuntuforums.org/showthread.php?t=95879)

---

### Post by kasemodz on 2006-01-14
yeah i looked at that page before, however it doesn't go in detail on how to build the driver.

---

### Post by Lambert on 2006-01-14
There is an attachment in that thread that you download and untar and it gives you a .deb file to install. What ever directory you untar in will give you ./home/will/rtl8180...deb

tar zxvf file_name.tar.gz

then just install by moving that that directory and then run this command

sudo dpkg -i file_name.deb

---

### Post by kasemodz on 2006-01-14
yeah true, but that supports the rtl8180 series. I have a rtl8185. The difference is that the rtl8180 is 802.11b compliant and rtl8185 is 802.11b/g compliant. So I dunno if it will work. can someone just tell me how to build a drive from source? Thats all I really need.

---

### Post by pjbgravely on 2006-04-24
This thread should help you.
[http://forums.xandros.com/viewtopic.php?p=137349&]("http://forums.xandros.com/viewtopic.php?p=137349&")

Xandros is built on Debian so it should work. You could also try the .deb further down.  
There is a native driver in Dapper now but it is still buggy and no WPA support. I use ndiswrapper for my card with good results.

Paul

---

