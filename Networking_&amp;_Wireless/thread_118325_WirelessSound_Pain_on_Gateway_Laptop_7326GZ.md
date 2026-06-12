---
title: "Wireless/Sound Pain on Gateway Laptop 7326GZ"
date: 2006-01-16
forum: Networking &amp; Wireless
---

### Post by Jhodytropical on 2006-01-16
Wireless Pain on Gateway 7326GZ

Hi
 I have a Gateway Laptop with the Following Configuration :
 3 GHz, 512 Ram, 80Gb Hd with on onboard Broadcom Wireless card with the following Specs :
A. 0000:01:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
B. 0000:01:09.0 0280: 14e4:4320 (rev 03)

After looking in the Threads I found out that for that type of Wireless Card I need to install 2 specific file 'BCMWL564.sys and 'NETBC564.inf'. I did that along with the installation of : 'ndisgtk' ; 'ndiswrapper-utils' ; 'ndiswrapper-source'. 

Then I go to 'System-Administration-Windows Wireless Drivers' I select it and then 'Configure Network' and I all I see is my Ethernet Card and my Modem no sign of WLan.

So, I decided to bring the manufacturer driver to linux and see if that could solve the problem  that didn't help either. The Lignt of my wireless connection on my Laptop would not come on.

I disabled my WEP on my router which is a Linksys Wrtp54g but that didn't solve the problem either. 

Linux is not being able to bring the Wlan up for some reasons. Please help !!!

---

### Post by Lambert on 2006-01-16
You have a broadcom chipset which tends to be troublesome for many.

With no wlan0 interface showing up that means your driver is not functioning properly.

You might need to try other drivers if the one you use looks like it loaded ok but won't work. I show alot of others using a bcmlw5.inf or bcmlw5a.inf driver to get this chipset working.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)

---

### Post by Jhodytropical on 2006-01-17
[QUOTE=Lambert]You have a broadcom chipset which tends to be troublesome for many.

With no wlan0 interface showing up that means your driver is not functioning properly.

You might need to try other drivers if the one you use looks like it loaded ok but won't work. I show alot of others using a bcmlw5.inf or bcmlw5a.inf driver to get this chipset working.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)[/QUOTE]

I tried both drivers they are not working either. Thanks for your help

---

### Post by FarEast on 2006-01-21
Hi;) ,

> After looking in the Threads I found out that for that type of Wireless Card
> I need to install 2 specific file 'BCMWL564.sys and 'NETBC564.inf'.
> I did that along with the installation of : 'ndisgtk' ; 'ndiswrapper-utils' ;
> 'ndiswrapper-source'.

Did you built 'ndiswrapper module' with 'module assistant' and install it?
If you have not done it yet and do not know how to do it, please tell me.

Below is the usage of ndiswrapper which I read on a web.

$ cd *(dir. in which windows drivers and regarding files are put)*
$ sudo ndiswrapper -i NETBC564.inf
Installing xxxxx
$ sudo ndiswrapper -l
Installed ndis drivers:
xxxxx driver present, hardware present
$ sudo modprobe ndiswrapper
$ sudo iwconfig wlan0 essid *ESSID*
$ sudo iwconfig wlan0 key restricted s:*WEP KEY*
$ sudo dhclient wlan0

---

