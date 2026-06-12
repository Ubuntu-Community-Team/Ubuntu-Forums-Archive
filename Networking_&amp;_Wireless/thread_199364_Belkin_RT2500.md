---
title: "Belkin RT2500"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by pcbodger on 2006-06-18
Hi all

I've loaded Dapper onto my second drive no problems and it detects my Belkin Rt2500 card as eth0 (inactive) on System > Admin > Networking but as that can only handle WEP I tried the RT2500 WPS-PSK Howto from the Wiki.

I set /network/interfaces as per instructions and when I tried sudo ifup eth1 I got:

SOICSIFFLAGS: No such file or directory
Failed to bring up eth1

Variations on the interface content cause other similar failures.

I really don't want to have to reroute my NTL cable up the outside of the house so any suggestions would be gratefully received!

Thx

PCBodger

---

### Post by pcbodger on 2006-06-21
No responses here so I STFW'd and found

[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+dapper]("http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+dapper")

As long as you have a long enough RJ45 cable and can read it should sole a lot of problems.

No arsing around with config filers or anything just a few downloads, a few package applications, a couple of extracts, a reboot and off you go!

---

