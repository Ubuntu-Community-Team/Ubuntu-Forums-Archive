---
title: "Unable to set ESSID and KEY"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by jxbrown on 2009-01-25
I have just purchased a Via ARTiGO A2000 from Logic Supply to use as a music server.  I purchased it with Ubuntu 8.10 pre-loaded.  I have no experience with Ubuntu, but had no trouble slapping a copy of Debian on my old Pentium II last year and have had relatively solvable problems on installs of SuSe and Red Hat over the years.  This Ubuntu has me stumped.

When I run iwlist scan I get:
ra0   Scan completed :
      Cell 01 - Address: 00:19:E4:B4:48:21
      ESSID:"oneill"
      Mode:Managed
      Channel:1
      Quality:81/100 Signal level: blah, blah, blah
      Encryption key: on
      etc.

But when I run iwconfig ra0 I get:
ra0   RT2870 Wireless ESSID:"" Nickname:"RT2870STA
      Mode:Auto blah, blah, blah
      Encryption key: off
      etc.

Nothing that I have tried will set the ESSID and the encryption key.  I've used the GUI Network Settings box, I've tried iwconfig commands, and I've hand edited /etc/network/interfaces.  I've ifup/ifdown'ed and rebooted multiple times.  I get no error messages.  Clearly, since iwlist shows all of the available networks, the box is recognizing the wireless card, it just can't seem to control it.  None of these will change the essid shown by iwconfig although the GUI shows 
Wireless connection 
essid: oneill Address: dhcp

Any ideas where to look next?  Or should I just install a Debian distro from a flipping thumb drive?  I thought that buying a pre-loaded box would be just like pulling a Windows PC out of the box and turning it on.  Guess not.

---

### Post by jxbrown on 2009-01-25
When I try
dmesg | grep -e ndis -e wlan

I get:
[   46.878003] I/F(ra0) Key1Str is Invalid key length! KeyLen=0!
[   46.878037] I/F(ra0) Key2Str is Invalid key length! KeyLen=0!
[   46.878069] I/F(ra0) Key3Str is Invalid key length! KeyLen=0!
[   46.878102] I/F(ra0) Key4Str is Invalid key length! KeyLen=0!
[  101.439338] ra0: no IPv6 routers present

---

