---
title: "Can't get connected- wireless ar5211 chipset"
date: 2005-02-07
forum: Networking &amp; Wireless
---

### Post by Dolgan on 2005-02-07
I just installed Ubuntu and it apparently detected my D-Link wireless card and configured it as ath0.  It shows as having the ar5211 chipset.  I have set the IP on the card and can ping it just fine.  I am unable to ping my wireless router, however.  I have DHCP disabled and am using static IP's.  Please note that this setup is working fine from another Win2k box.   This is an 802.11a card and I'm (trying) to use a 152bit wep key.   When I iwconfig ath0 it shows that it's picked up the eeid and the mac address from my router.  I haven't tried disabling wep yet as I'm currently at work but I thought I'd try to get some feedback.  Thanks in advance!

---

### Post by Shaggy on 2005-02-07
I would try either disabling or lowering your wep key.

If that didn't work I'd disable wep all together and enable dhcp on the router to see if it would get an IP on it's own.  I usually go that route just to make sure it works properly, then go about making systems secure.

---

### Post by Dolgan on 2005-02-09
Thanks for your help.  Changing from a 152 bit WEP key to a 128 bit WEP key got me connected.  This seems to be a good group of people on the forums- keep it up!

---

