---
title: "T-mobile webconnect jet Huawei UMG1691"
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by Yep on 2010-03-31
Hello linux people! 

I'm trying to get this T-mobile USB modem (webconnect jet Huawei UMG1691) to work with my ubuntu 8.10 to no avail. 

I've found little-to-nothing about this on the interwebs...anyone got a fix for me? 

Thanks 
Tim

---

### Post by pdc on 2010-03-31
if you know how to open a terminal, do so and type

> lsusb

and copy and paste what you get;

also 

> dmesg | grep tty

and copy and paste results

and finally ...... what happens if you follow the instructions

"How to create a mobile broadband connection ........"

as here, half way down page 

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

8.10 is from October 2008 so an older version of Ubuntu, but that might be good!

---

### Post by Yep on 2010-04-01
hey

first

lsusb in terminal gave me this:
 
Bus 004 Device 002: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

and then this from dmesg|grep tty 

[    0.004000] console [tty0] enabled
[   10.421219] tty ptyy0: hash matches


I've gone through the editing/adding of my connections, but i can't get it to work... 

I've tried the APN set at "wap.voicestream.com" a "internet2.voicestream.com" but I can't seem to connect, or even see it listed on my network list.
I don't have a username or password from T-mobile. Also, when i add or edit My Mobile Broadband connections, after the operation, the network icon disappears from my panel and i can't access my regular WiFi connection til i restart...not a problem, as i won't be the one using this T-mobile thing, it's for a different machine, but i just wanna know i can get it to work....

Thanks
Tim

---

### Post by pdc on 2010-04-01
do you get an icon on your desktop, when you plug the modem in?

If so, right-click on it, and select "eject";

if so, type

> lsusb

if it now says

> 12d1:0x14ac

you have successfully "flipped" the device ..

..as ... I suspect it is being seen as a virtual CD-ROM device (loaded with windows software); and to use in linux, it needs to be "flipped" to unmask it as the modem it also is;

a programme called usb_modeswitch does this; but lets see how the above goes;

by the way, can you type

> uname -r in a terminal and copy and paste the results; checking you have the latest kernel version installed

---

### Post by Yep on 2010-04-02
Yes the T-mobile webconnect manager icon shows up. I eject/unmount it, but it is not recognized as a usb modem still. 
When i do 'lsusb' in the terminal i get the same result as before.


tim@tim-laptop:~$ uname -r
2.6.27-17-generic


I found this USB_modeswitch program that i'll try next...and update ASAP. Any other ideas?

---

### Post by pdc on 2010-04-02
you are absolutely right;

download and install usb_modeswitch

your device is recognised there;

if you type 

> lsusb

after installing, you should see 

> 0x12d1:0x14ac 

and if you type

> dmesg | grep tty

we hope you will see ttyUSB0 and ttyUSB1 at least ..

.. and then configure as in 

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

half-way down page

"Create a mobile broadband connection .."

and you have the latest kernel installed, so that should be fine

---

### Post by BSD_dad on 2010-07-16
Here's a step by step with screen captures that worked for me (Linux greenie) [http://forums.t-mobile.com/t5/Laptop-Stick-Help/FYI-Rocket-USB-Laptop-Stick-Huawei-UMG1831-Works-Under-Ubuntu-10/m-p/377151#M782](http://forums.t-mobile.com/t5/Laptop-Stick-Help/FYI-Rocket-USB-Laptop-Stick-Huawei-UMG1831-Works-Under-Ubuntu-10/m-p/377151#M782)

Note: my umg1691 showed up as a 140c instead of the authors 1404 (different stick). Substituting that worked fine. Also Ubuntu 10.04 showed a T-Mobile G1 account with the correct APN. 

Still working on getting Wine to run the stick's apps (Ubuntu wants the executable bit set unfortunately) just in case I want to see the other features (mail to device, whether on 3G or not, data used, etc.)

Edit: Ran across work around of launching Explorer in Wine and launching TM's webconnect mgr from there. The webconnect mgr didn't run from the stick but the setup program did which invoked Install Shield. Webconnect mgr shows in Wine section under Ubuntu but doesn't come up. Can launch it from browser and get the spash screen for it then it hangs. Oh well, I can live without the extra features or boot in IE for them.

---

