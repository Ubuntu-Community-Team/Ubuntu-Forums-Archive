---
title: "Capped Bandwidth Tools"
date: 2012-11-11
forum: Networking &amp; Wireless
---

### Post by thetrickybuddha on 2012-11-11
I have recently installed Ubuntu 12.04 on a fairly new machine (Intel i3, Gigabyte H77N-WIFI, 8 GB RAM) in order to build a specialized network appliance for one of my customers. 

Note: The OS is installed on a USB flash drive attached the machine, it does not have an optical drive or HD. Additionally the board has two LAN ports which are recognized by Ubuntu and are functional. There are no issues as far as I can tell with compatibility or the hardware. 

The customer, who is very poor with computers, is on a rural satellite connection and have very limited monthly bandwidth (15 GB). The goal of the appliance is three-fold: 

1) Provide a visual look at the current bandwidth usage as well as show how much bandwidth has been used for the month. 
2) Send an alert when certain bandwidth milestones are reached and allow for the ability to disable to connectivity. 
3) Have one LAN port be dedicated to the satellite connection and the other provide connectivity to a wireless router so the machine would act as a router in that sense.

Now I am pretty new to Ubuntu and can think of some ways to start to accomplish these goals but I dont want to reinvent the wheel. I'd like to set up remote desktop viewing and find the right tools to accomplish these tasks (if they exist) 

Thank you in advance.

---

### Post by thetrickybuddha on 2012-11-11
Update: I have installed FreeNX and now have remote entry into the desktop so that is addressed. Additionally I may be able to use the onboard WIFI as a hotspot thus eliminating the need to provide DHCP services to the second LAN port though that functionality still sounds useful.

---

### Post by thetrickybuddha on 2012-11-12
Ever impatient I ventured forth to get into trouble on my own. After essentially getting it much of what wanted working in 12.04 TLS I encountered a Network Manager error I could no get around. While it still essentially functioned I do not feel like dealing with giving terminal commands over the phone to change WLAN configuration data and the like should that arise. 

So I started over with 12.10. This gives me the opportunity to give the steps I used to community in order to help someone else with this issue get resolution. 

First I decided the USB stick looked lame so I installed a spare 80 SATA hard drive I had laying around. I then downloaded the latest 12.10 image and made an installer USB. 

Note: Making an image 798 MB is pretty irritating. Too big for overburn on a CD-R and too small to want to throw a whole single image DVD at it. 

After the install I immediately updated then configured it to update and disabled power management to prevent anything from going to sleep. It is intended to sit as a headless network appliance as well as preserve bandwidth as much as possible so these were necessary steps. 

In preparation for the installing the vnstat GUI I installed LAMPP and configured init.d to allow it to start on boot. After securing LAMPP I then installed vnstat. Once that was configured I installed the GUI and got the whole thing configured. It required a little finessing thanks to a lack of documentation. 

It took a lot cron configuration to get things the way I wanted and I didn't get any help on it from here sadly but maybe these steps can help someone else.

---

