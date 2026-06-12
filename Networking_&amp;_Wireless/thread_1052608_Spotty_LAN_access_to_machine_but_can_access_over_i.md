---
title: "Spotty LAN access to machine but can access over internet reliably"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by Falklian on 2009-01-27
I set up Intrepid on my laptop about a month ago (Inspiron 1525) and have Apache and SSH running.  The laptop has a static IP address and it seems that I can access it sporadically throughout the day through my local network.  I can SSH in just fine from my desktop PC occasionally, but I can and will lose connection at any time.  It won't respond to pings, but I can go out to my laptop and ping my desktop fine and I have internet access.  I also verified that the other desktop belonging to my fiance cannot access the laptop either and again, the laptop can at least ping her machine and has internet access.  Earlier today, I decided to forward some ports on my router (Linksys WRT-54Gv6) and had a friend SSH into it from his workplace.  He was able to get in fine while the other computers on my LAN could not access nor ping the laptop.

Some things I've tried/noted:
[list]
[*]Static IP doesn't seem to change, it's set as 192.168.1.10.  DHCP is enabled on the Linksys router though.
[*]I've tried restricted and non-restricted WLAN drivers and both do the same thing.
[*]This [workaround]("http://ubuntuforums.org/showthread.php?t=974382").
[/list]

I originally thought it might just be a WLAN issue, but I never had this much trouble when the machine was running Windows.  The wireless router is about 15 - 20 feet away from the laptop and the signal is going through one wall, signal strength is very strong.

If anyone has any insight it'd greatly be appreciated.

---

### Post by Falklian on 2009-01-28
Friendly /bump before I go to bed.

Wireless in the laptop is a Broadcom BCM4312 by the way.  I can try the ndiswrapper stuff tomorrow if no one else has any ideas.

Thanks

---

