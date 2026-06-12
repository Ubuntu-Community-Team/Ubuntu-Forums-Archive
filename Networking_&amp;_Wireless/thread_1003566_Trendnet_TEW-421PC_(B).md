---
title: "Trendnet TEW-421PC (B)"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by sam1993 on 2008-12-06
Hi there guys,

I have been reading that it isn't as simple as installing Wifi cards on Linux.
Could someone tell me the steps to installing the Trendnet TEW-421PC (B) on my laptop please. I need to know each step and how to do each step. I obviously know how to run a install application, .exe, but does Linux support .exe files? I need to know how to do the tricky bits really, well from step 1 to the finish step would be best as I dont know about installing applications/software on Linux as I am a linux novice.

I would be very grateful if someone could tell me how to do this. Once I know how to install Wifi cards, I will then now how to install my Buffalo Adapter I am going to order for my laptop.

---

### Post by Fireblazer on 2008-12-06
Hi,

I just installed a TEW-423PI on an Ubuntu system.
To get it working I had to follow the instructions on this page exactly.
[WiFiDocs/Drivers/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

Hope it helps,
Fireblazer

---

### Post by sam1993 on 2008-12-06
> **Fireblazer said:**
> Hi,

I just installed a TEW-423PI on an Ubuntu system.
To get it working I had to follow the instructions on this page exactly.
[WiFiDocs/Drivers/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

Hope it helps,
Fireblazer

Cheers :) I will try it out.

---

### Post by *supaSTAR* on 2008-12-16
> **Fireblazer said:**
> Hi,

I just installed a TEW-423PI on an Ubuntu system.
To get it working I had to follow the instructions on this page exactly.
[WiFiDocs/Drivers/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

Hope it helps,
Fireblazer


It didnt work for me. i tried it and it said invalid driver.

this is the net8185.inf driver the windows 2000.

Who is used a different driver?

---

### Post by hockeyshifter on 2008-12-27
when you install the drivers i installed all that were present and i transfered them to a folder on the HDD... i did have to reboot to get mine to work but i still do not know how it happened. 

in a terminal type

lspci   list if computer see the card

ifconfig   will tell you were the card is located.

---

### Post by Steve J on 2012-02-03
> **Fireblazer said:**
> Hi,

I just installed a TEW-423PI on an Ubuntu system.
To get it working I had to follow the instructions on this page exactly.
[WiFiDocs/Drivers/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

Hope it helps,
Fireblazer

This was the tip that finally solved my problem!
[INDENT]Ubuntu 10.04 LTS
Dell Inspiron 4150
Trendnet TEW 421PC
[/INDENT]
This is where I got the driver:
Driver: Driver for the Airlink+ 802.11g Model AWLH3025 ([http://www.airlinkplus.com/driver/11g/awlh3025_v6_0_5_30_xp.zip](http://www.airlinkplus.com/driver/11g/awlh3025_v6_0_5_30_xp.zip)) works very well including WEP. 

Driver link found here:
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Trendnet_TEW-421PC](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Trendnet_TEW-421PC)

---

