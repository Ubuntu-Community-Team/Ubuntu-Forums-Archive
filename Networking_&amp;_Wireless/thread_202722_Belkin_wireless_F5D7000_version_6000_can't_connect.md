---
title: "Belkin wireless F5D7000 version 6000 can't connect with Ubunbu 6.06"
date: 2006-06-23
forum: Networking &amp; Wireless
---

### Post by he11 on 2006-06-23
i have a belkin g wireless 802.11g wireless card, its part number is F5D7000 and its version is 6000, when i use the command lspci it says that it is a Ralink device and the networking utility picks it up as ra0. I've gotten ndiswrapper and ive tried to load up the driver that came with the card but when ndiswrapper tries to load up that .inf file i get this as an error 
grag@grag-desktop:~$ sudo ndiswrapper -i rt61.inf
Installing rt61
couldn't copy rt61.inf at /usr/sbin/ndiswrapper line 135.

ive tried every other driver for that card and ive gotten the bcmwl5.inf file to install, but then when i type sudo ndiswrapper -l it says that the driver is present but not the hardware, i am total linux n00b so i dont know what else to try, ive tried manually configuring my wireless card and ive also tried using the system>admin>networking and using that utility and that doesnt work for me either. If i try to use the DHCP option my comp freezes up and i have to restart and when i restart and it tries to config my network devices during start up it gets stuck there and i cant get around it and have to re-install ubuntu. if you have any advice it would be very much appreciated.

---

### Post by Aaron Kupniewski on 2006-07-01
I'm having very similar issues with my bcmwl5 drivers.  I get the line 135 error and I really have no idea as to what can be done.  I've done this same procedure on debian and it worked... so I don't know what's up.

---

### Post by K3V on 2006-07-12
I am having the same problem. Using Belkin wireless F5D7000 here as well. This is strange. I know that the drive is working because I see all the SSID around my network. Thus, I know that it is working for some reasons. So I choose the SSID of my router, enter WEP Key, IP address, and gateway ip address. After I enter every necessary information, I clicked on Activate button and I see the small window with message about activating interface. I thought everything works... I didn't get any error. But when I try to use Firefox to surf the net, it keeps displaying.... looking up [www.google.com](www.google.com).... and after a few minutes... I got "Server not found" error... I tried to ping other website but nothing happened right away... after a few minutes.. The following message was displayed "ping: unknow host www.google.com"


Well, I am using Live CD to test with my PC to make sure that everything works before I install it for real. 

Anyway, I also tested Ubuntu 6.06 Live CD with my IBM Laptop T42 and everything works out of the box. All I need to do is configure the wireless network connection. SWEET!!!:)

---

### Post by KidRdbz on 2006-07-23
I have the same card.  It uses the RaLink RT61 chipset.  I got it working with the instructions found here: [http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)

If you are using Dapper scroll down to the Dapper instructions a little way down the page.

Note: There is a newer version of the driver available at the RaLink website here: [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)

---

