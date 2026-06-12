---
title: "Frequent disconnect and resetting problem with huawei HSDPA modem"
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by web-e on 2010-12-03
I just bought USB HSDPA modem by Huawei to access internet via 3G few days ago.It works fine with windows 7 64bit,but having problem to run on ubuntu 10.10 32bit desktop edition (tried on different systems also).

When I connect the device ubuntu can detected it as "yyyyxxxxxHuawei modem" (y and x are not numbers,it shows like that).Then I created a mobile broadband connection and put the same parameters as in windows (those APN and other stuff)

Then when I try to connect, it fails.After attempting two three times it connects,but the problem is within 15 seconds,it got disconnected and the indicator on modem blinks like the modem is being reinitialized.

Please tell me how to deal with such problem.
Here is the hardware information,

MODEL : HUAWEI E169
HARDWARE VERSION: CD57TCPU

---

### Post by pdc on 2010-12-03
perhaps if you **copy and paste** this command

> dmesg | grep tty

into a terminal and look to see if you get ttyUSB0 and others ..

..if you do, the device is seen as a modem; if no ttyUSB0 etc

suggest you install usb_modeswitch

debian packages are available here

[http://packages.debian.org/squeeze/usb-modeswitch](http://packages.debian.org/squeeze/usb-modeswitch)

the unstable just means the packages are the latest

if you select the one that matches your system ie 32bit or whatever

your system will ask you if you want to install with gdebi package installer: say yes; it should then install the data package as well;

and all this should "flip" your device so it is seen as a modem

you can subscribe to these threads: go to thread tools at teh top; then the forum will email you, and let you keep in touch with what folks suggest ..

i*f you can't copy and paste the above command, just type dmesg in a terminal; you will get lots of information; look for any ttyUSB0 and ttyUSB1 information*

---

### Post by Harry h on 2010-12-03
p { margin-bottom: 0.21cm; }  This is how I have set up  Huawei E160e HSDPA USB Modem with a prepaid Optus account on Ubuntu 10.10. in Australia.
 

 
[LIST=1]
[*]Plug in the USB stick
[*]Boot up the computer and log in
[*]Left click on  the Network Manager 	Applet at top right of screen
[*]Click on “New Mobile Broadband 	(GSM) connection (This will bring up the Mobile Broadband Connection 	Assistant)
[*]Click on forward and select 	Australia
[*]Click on forward and select Optus
[*]Click on forward and select 	Prepaid Mobile Broadband
[*]Click on forward and click Apply
[*]If the Network Manager tries to 	connect left click on it and then click on disconnect
[*]Right click on the Network Manager 	and then edit connections
[*]Click on Mobile Broadband
[*]Click on Optus Pre-paid Mobile 	Broadband. You may have to enter your password here.
[*]Click edit
[*]In  APN:  highlight current 	setting and delete and type in connect. Click on Available to all 	users
[*]On the PPP Setting tab 	Authentication: CHAP only untick the rest. Compression: Be sure the 	following are ticked: Allow BSD data compression, Allow Deflate data 	compression and  Use TCP header compression
[*]On the Ipv4 Settings tab Method: 	Automatic (PPP)
[*]Then click on Apply.
[/LIST]
 

 You may need to reboot. It worked for me. Hope this helps.

---

### Post by web-e on 2010-12-03
[FONT=Tahoma]Thanks to all,problem solved.
@pdc yeah I am getting the modem on USB0.

@Harry Your method worked out.. though the modem is made for Optus, [/FONT][FONT=Tahoma]Huawei service centre gives me as a replacement in india.
It is working fine till now and hope will work.Thanks again.[/FONT]:D

---

### Post by Harry h on 2010-12-06
Happy to help.

All the best.

---

