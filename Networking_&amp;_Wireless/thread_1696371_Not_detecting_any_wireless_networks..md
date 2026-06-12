---
title: "Not detecting any wireless networks."
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by Azaz on 2011-02-27
First let me just say im a 100% linux noobie. First time ever switching from windows. Mainly doing this cause I though it would be fun to learn a new OS and see how it is.
From watching a few videos it looked like all I have to do is click on the wifi logo at the top of the screen and I would get my router and a bunch of others (does this on windows) but when I click on it I dont get anything. I think it might be that im running this on a laptop. My wifi card is: Standard Dell Wireless 1501 802.11 g/n
Its a new dell inspiron 5000 laptop i customized a little with more ram and a new video card. :KS

Im guessing I will need to provide more info but as I said at the start Im new to this and not sure how or what info I would need to provide. Please just tell me how I can get any data you need and il get right on it. (I used Wubi to install this, went off without a hitch)

---

### Post by Azaz on 2011-02-27
bump?

---

### Post by bkratz on 2011-02-27
From what I see on the Broadcom site in the readme file

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

 the 1501 uses the STA driver

 4313 2.4 Ghz	    0x14e4	0x4727 	Dell 1501

You should find the driver under system>>administration>>Hardware Drivers (or additional drivers) if you have an ethernet connection when you select this menu or go to this page for additional information (alternate methods).

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Azaz on 2011-03-05
umm thank you but I'm afraid I'm having a hard time understanding you. Iv never used linux or a laptop before (granted not the smartest idea but its all I have right now) and I just want to beable to connect to the internet so I can google info as I try and learn linux.
Could someone please explain how I can do that in a new user friendly way?
(sorry for the late reply iv been sick for a week :()

---

### Post by Birdman19 on 2011-03-05
lol im sorry to say this man but thats pretty darn simple. What the person recomended is about as simple as searching the hard drives in windows.

---

### Post by Azaz on 2011-03-06
> **Birdman19 said:**
> lol im sorry to say this man but thats pretty darn simple. What the person recomended is about as simple as searching the hard drives in windows.

O.O thats what he was asking me to do? After rereading it with that in mind now I understand it lol, I though he wanted me to download some stuff, do some codeing and install it at that location. thanks :)

Edit: when I go into that menu I just get a blank list. I will need to go to the library and print out that other page he linked. :(

---

### Post by Talon2 on 2011-03-06
[QUOTE=Azaz;10528662

Edit: when I go into that menu I just get a blank list. :([/QUOTE]

Use an ethernet cable and hook your system into a router that will give you internet access.  The list should not be blank then.  Once you have activated the driver, you can disconnect the ethernet and work wirelessly.

---

### Post by Spyderkid on 2011-03-06
go to system > administration > additional drivers, wait for it to search for drivers then when the big box pops up enable the wireless one.

---

### Post by Azaz on 2011-03-12
> **Talon2 said:**
> Use an ethernet cable and hook your system into a router that will give you internet access.  The list should not be blank then.  Once you have activated the driver, you can disconnect the ethernet and work wirelessly.

This worked but I had to hook it up, restart it, then hook it up again and it finally worked, thanks for that :D

---

