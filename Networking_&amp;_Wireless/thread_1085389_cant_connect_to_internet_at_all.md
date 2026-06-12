---
title: "cant connect to internet at all"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by darko956 on 2009-03-03
i have a acer aspire 6530g laptop brand new so i installed unbuntu on it and no network connections at all work i know its probably because the drivers arent installed for my network devices how would i go about finding the drivers i need and installing them many thanks in advance
edit:if there is any more info you need on my system jsut let me know and ill try to get it to you
edit: i tryed using ndiswrapper but the only drivers for my card taht i could find was for vista i tryed using them with it and id still didnt work any ideas now?

---

### Post by darko956 on 2009-03-03
bump
i still need help with this if any can

---

### Post by darko956 on 2009-03-03
im kinda desperte here ive installed ndiswrapper and gotten the drivers for my card when i go to system/admin/wireless windows drivers i get a pop up that says unable to see if hardware is present there are 3 drivers currently installed and all 3 of them say that the hardware is present but it sill isnt working anyone konw anything that could help?

---

### Post by theozzlives on 2009-03-03
It would help to know what kinda NIC you have.

---

### Post by darko956 on 2009-03-03
the sticker on the laptop says its a Acer Nplify 802.11b/g/Draft-n WLAN 
when i do a lspci it listed as atheros communications inc. unknown device 002a
hope that helps

---

### Post by darko956 on 2009-03-03
donny@donny-laptop:/$ ndiswrapper -l

WARNING: /etc/modprobe.d/blacklist line 46: ignoring bad line starting with 'blacklist'

netathrx : driver installed

	device (168C:002A) present

WARNING: /etc/modprobe.d/blacklist line 46: ignoring bad line starting with 'blacklist'
netathw : driver installed
	
device (168C:002A) present
WARNING: /etc/modprobe.d/blacklist line 46: ignoring bad line starting with 'blacklist'

netathwx : driver installed

	device (168C:002A) present
donny@donny-laptop:/$

---

