---
title: "Netgear DGN2200"
date: 2013-05-26
forum: Networking &amp; Wireless
---

### Post by Y^2om&amp;#7sgP on 2013-05-26
Not sure if this is the correct part of the forum as this is a strange problem (to me anyway)
I have a desktop PC and laptop both (were) running Xubuntu 12.04
Attached to the desktop PC is a 2tb usb drive, containing movies/music etc.
The connect to the internet using a Netgear DGN2200 router (desktop via ethernet cable, laptop wireless)
Shares setup using Nautilus share, and 'were' accessable from the laptop.
Then.....a couple of days ago, the laptop stopped 'seeing' the desktop PC or the usb drive.
I connected the usb drive via cable directly into the router (it has a usb port in the back for doing just that) and neither computer could see it.
I at first figured that the router was faulty and had it replaced by my service provider....they checked the old one and it worked just fine.
New router...installed all working except...couldn't see the drive or shares.
Just rebuilt my laptop with (sorry) Windows 7 and it can see the drive and shares..
Has anyone come across anything like this, and if so....how to fix it 'cause I really can't be bothered with M$ :mad:
As the router is happy with Windows I suspect that a kernel update or dependency has caused this.  I have tested though by booting the laptop with a live Xubuntu usb stick and that has the same problem.

---

### Post by 2F4U on 2013-05-26
Are both machines able to "see" each other (not considering the share at the moment, just basic TCPIP functionality), are you able to ping the other machine? Do you have firewalls installed on any of the machines, and, if yes, are the respective ports open?

---

### Post by Y^2om&amp;#7sgP on 2013-05-26
They can ping each other, but clicking on the 'Browse Network' item in Nautilus only shows two items....'Video' and 'Windows Network'  if I try and open either of these, after 30 seconds or so get the message 'unable to open /'
No additional firewall installed on either machine.
This was working just fine (for at least the last year) and only failed two days ago.  Nothing has been changed apart form updates when they've been alerted in the update manager.

---

