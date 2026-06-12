---
title: "Edimax EW-7711 xxx HowTo"
date: 2010-08-09
forum: Networking &amp; Wireless
---

### Post by gregoryj on 2010-08-09
I had problems getting my Edimax EW-7711usn device working on 10.04
I contacted Technical support at Edimax, and they sent me an updated driver (v2.3.0.2) and a comprehensive "HowTo" with pictures & screenshots
There is now a link on the Edimax website to the "HowTo" and Driver download specific to Ubuntu 10.04
Here.
[FONT=Helvetica-Bold][SIZE=3][COLOR=#ff0000][FONT=Helvetica-Bold][SIZE=3][COLOR=#ff0000][FONT=Helvetica-Bold][SIZE=3][COLOR=#ff0000][**[SIZE=2]http://www.edimax.co.uk/en/support_detail.php?pl1_idSelect=support.php?pl1_id%3D1%26mwsp%3D1&pl1_id=1&pd_id=291&button=Go[/SIZE]**]("http://www.edimax.co.uk/en/support_detail.php?pl1_idSelect=support.php?pl1_id%3D1%26mwsp%3D1&pl1_id=1&pd_id=291&button=Go")[/COLOR][/SIZE][/FONT]
 
[SIZE=3][FONT=Helvetica-Bold][COLOR=#ff0000][SIZE=1][COLOR=black]The driver did not appear to work at first, but after physically disconnecting the device and doing a complete shutdown, reboot and reconnecting the device, it worked well.[/COLOR][/SIZE][/COLOR][/FONT]
 
[COLOR=#ff0000][FONT=Helvetica-Bold][SIZE=1][COLOR=#000000]I have found for me that "Wicd" works better than the default Gnome "Network Manager"[/COLOR][/SIZE][/FONT]

[FONT=Helvetica-Bold][SIZE=1][COLOR=#000000]Thanks to Edimax Technical Support for their help ![/COLOR][/SIZE][/FONT]
[/COLOR][/SIZE][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by totallynew on 2010-11-22
the guide has some very small issues like "destop" instead of desktop
i'm sure most will spot it.
however didn't work for me using vm though even after fine tooth combing the guide

---

### Post by gregoryj on 2011-08-18
The Guide on the Edimax website is now out of date and rather confusing...! I did inform Edimax support and ask them to update it, but they did not.
However, the current driver link is good for the later 3x kernel series in Lucid 10.04 , You will still have to blacklist the old rt2800 drivers as per the guide and make mods to the config as described in the "read me" file in the driver folder for it to work with Gnome Network Manager

---

