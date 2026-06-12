---
title: "icon 515 need an answer it works on 10.10"
date: 2010-12-09
forum: Networking &amp; Wireless
---

### Post by darkworld on 2010-12-09
A mystery to me. 

I couldnt get this to work on 10.4 but this has just happened. 

At home 64bit amd machine 32 bit 10.10. It sees the icon515 as eth0 and puts orange icon on desktop. Thats as far as i can get. 

But at work on my laptop....64bit latitude ES400...i have 64bit 10.10 on a usb stick...boot laptop of stick... and then plug in icon515...it doesnt see it as eth0...it sees it as exactly icon515 GSM device in network manager...sets up and connects??? yipee....but at home I need to solve and i need to keep 32 on 64 at home.

ok...why doesnt it do this on my 10.10 32bit at home any ideas?

---

### Post by alexfish on 2010-12-09
hi

not sure, don't know about 64bit , but could look at versions of Network Manager and Modem Manager

also there is a util called "hsolink" , this is missing in the repos in 32.bit 

can also see how they are listing with this code from the terminal

Code
usb-devices

also checkout with a file search for hso.ko

and see if usb_modswitch is installed

Added:
another area to look ; although long winded , udev , look in the /lib/udev/rules.d/*

check out both 64 bit and 32bit / before deciding actions

Added: also check which interface is been used , look at ifconfig when the connection is up

Code:

ifconfig

see if its on the ethernet : or pppd

---

### Post by darkworld on 2010-12-09
thanks alex i will do this when im back at work tomorrow. I did look at version of network manager at work and it is different. 32 bit is 0.8 but I think on my laptop it was 0.8.01

---

