---
title: "DWA-652 Can't Access Network"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by BlackAce on 2009-01-07
I am trying to use my D Link DWA-652 N Draft card. From what I have read is that I uses the Atheros AR5416 chipset. It seems that the device was detected but for some reason I was unable to get it work. I was able to see the network but I could not connect. So then I decided to see if it would work with ndiswrapper instead.

I followed this link 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

and blacklisted my internal wireless broadcom driver and also disabled and it my bios.

I then used ndiswrapper but did not have the network configuration tool installed. So I installed the gnome-network-admin. I then followed the instructions for ndiswrapper from the link above. Now it seems that it sees my network but I am unable to connect to it. I am using WPA2 on my network and also tried WPA and and neither can connect. I get a message stating that it's using a key and to enter the key to connect, I do but it just keeps trying to gain access but then get the message again. My card supports both WPA and WPA2. The signal strength is great and it sees other networks that are also in my area. 
 
I then used ndiswrapper to see if the driver was installed ( ndiswrapper -l ) and it states that net5416 is installed. 

I am not really sure what to do now and tried everything I could think of, which isn't much. LOL!

BTW I am using 8.10

---

### Post by awwong on 2009-04-21
The 8.10 kernel is buggy with the D-Link DWA-652.  I updated my ath9k drivers following the instructions at the Linux Wireless site here:

[URL="http://linuxwireless.org/en/users/Drivers/ath9k"]http://linuxwireless.org/en/users/Drivers/ath9k
[/URL]
9.04 should work better with the DWA-652 but I haven't tried it yet.  The final version is due out in a few days.

---

