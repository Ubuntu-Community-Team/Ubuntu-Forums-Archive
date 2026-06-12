---
title: "Cannot connect to device using ADB"
date: 2014-09-08
forum: Mobile Technology Discussions (CLOSED)
---

### Post by typos1 on 2014-09-08
[TABLE="class: tborder"]
[TR]
[TD="class: posterInfo"][>]("http://forum.xda-developers.com/#")
 		
 		        		 	[/TD]
  	 	[TD="class: alt1 postContent"] 	 		 	  		  		 		          			I m having problems  connecting my device with adb (I ve connected several other devices  before with no problems). 

I ve got an Allwinner A20 tv box, it worked fine for a few months then  one day, after being on (but idle) for a few hours, I noticed the screen  was blank but the light on the front was blue (indicating it was on,  red is standby). It would not respond to the remote control or to  anything, so I unplugged it and since then it will not boot and the  screen is blank, the red light will light up but that is it. I ve  eliminated the remote controller not working, but I cant boot the  device.

So I ve tried connecting via ADB (with Ubuntu) but I cant get the device to show up after typing "adb devices".

Using this guide: 

[http://androidonlinux.wordpress.com/...-adb-on-linux/]("http://androidonlinux.wordpress.com/2013/05/12/setting-up-adb-on-linux/")

I can get the vendor id and device id and I ve added it and the  manufacturer to udev/modeswitch devices, but when I type "sudo  usb_modeswitch -v 0x1f3a -p 0xefe8 -S -R -W"

I get the following error:

~/Android/sdk/platform-tools$ sudo usb_modeswitch -v 0x1f3a -p 0xefe8 -S -R -W
Take all parameters from the command line


* usb_modeswitch: handle USB devices with multiple modes
* Version 2.1.1 (C) Josua Dietze 2014
* Based on libusb1/libusbx

! PLEASE REPORT NEW CONFIGURATIONS !

DefaultVendor= 0x1f3a
DefaultProduct= 0xefe8
SierraMode=1
NeedResponse=0

Look for default devices ...
found USB ID 048d:1336
found USB ID 1d6b:0002
found USB ID 19a8:2036
found USB ID 1f3a:efe8
vendor ID matched
product ID matched
found USB ID 1d6b:0001
found USB ID 062a:0102
found USB ID 1d6b:0001
Found devices in default mode (1)
Access device 004 on bus 003
Current configuration number is 1
Use interface number 0

USB description data (for identification)
-------------------------
Manufacturer: not provided
Product: not provided
Serial No.: not provided
-------------------------
Send Sierra control message
Error: Sierra control message failed (error -7). Abort

I ve searched Google for the error code but I cannot find anything.

The device was rooted and USB debugging was on.

For some reason it sees the device but cannot connect, I cant work out why

Any help would really be appreciated.

Thanks 		

[/TD]
[/TR]
[/TABLE]

---

