---
title: "rtl8188ce disconnects using battery power"
date: 2011-03-31
forum: Networking &amp; Wireless
---

### Post by rayian on 2011-03-31
I've got a Toshiba Satellite with the Realtek rtl8188ce network card. I've successfully downloaded, compiled and installed the driver and it works great except when running the machine on battery power when it constantly disconnects, like every minute or two.
Does anyone have any experience with this issue?
I've emailed realtek but I'm still waiting for a reply.

---

### Post by drewesq on 2011-04-01
Hey man, this is your fix:
 
go to [www.realtek.com]("http://www.realtek.com") > then click on the "Downloads" link > then "Downloads Search" Box > type RTL8188CE and click "Go" > then choose the top result which is "RTL8188CE (Software)" on the next page you should see a list of mirrors where you can download the linux driver from.
 
Basically this happened becaue the card is brand new (and probably not tested too well) but downloading the newest driver will fix the problem.

---

### Post by rayian on 2011-04-01
> **drewesq said:**
> Hey man, this is your fix:
 
go to [www.realtek.com]("http://www.realtek.com") > then click on the "Downloads" link > then "Downloads Search" Box > type RTL8188CE and click "Go" > then choose the top result which is "RTL8188CE (Software)" on the next page you should see a list of mirrors where you can download the linux driver from.
 
Basically this happened becaue the card is brand new (and probably not tested too well) but downloading the newest driver will fix the problem.

Yes, you're right. That's exactly the driver that I'm using.

---

### Post by rayian on 2011-04-01
OK. Very good. A guy from Realtek sent me a new driver. Problem solved. No more disconnecting.

---

### Post by xtoph on 2011-04-06
I've been having this exact problem with Windows7 on a Satellite L635 laptop.  Upgrading from the preloaded 1002 version to 1005 of the RTL8188CE driver fixed it.  I also downloaded the latest linux driver for use with Linux Mint, no trouble with that.

...Just thought I would contribute that in case anyone else's googling brings them here.

---

### Post by rayian on 2011-04-07
OK Here's the latest driver from Realtek for the rtl8188ce. You need to go into the folder where you compiled the old driver and do a make uninstall. Then enter the folder of the new driver  and do
1. sudo su
2. make
3. make install
4. reboot

This driver is only for kernel version >= 2.6.35 so only for Ubuntu 10.10 at this point I believe.
Read the readme file.

---

### Post by NoVista on 2011-04-09
Thanks for the link to the updated driver.
I'll post back once I can confirm the sporadic disconnects stop.

---

### Post by NoVista on 2011-04-10
Yes, this driver appears to be steady, and also shows itself  in the proprietary driver list, whereas the old one did not.

---

