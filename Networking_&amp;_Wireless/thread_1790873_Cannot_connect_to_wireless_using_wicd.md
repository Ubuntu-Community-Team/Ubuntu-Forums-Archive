---
title: "Cannot connect to wireless using wicd"
date: 2011-06-25
forum: Networking &amp; Wireless
---

### Post by tomns on 2011-06-25
I am running Natty on a Lenovo T410.  I can connect to wireless with no problem using the panel applet but not using wicd.  syslog shows it trying to get a DHCP address and finally timing out with no lease offers.   I think a big clue is that if I monitor wlan0 using wireshark I get no traffic at all when it tries to connect, whereas with the applet I see the dhcp traffic.  It seems as though wicd is connecting to the wrong wlan0.  Running "dhclient wlan0" directly gives the same behavior as wicd.  I need to use wicd because I typically run enlightenment so can't use the ubuntu applet. 

Any suggestions?  Thanks.

---

### Post by chili555 on 2011-06-25
> I can connect to wireless with no problem using the panel applet but not using wicd.I rather suspect that they conflict; sort of like four hands on the steering wheel. I suggest you remove the panel applet altogether:```
sudo apt-get remove --purge network-manage*
```Reboot, click Wicd and smile.

---

### Post by trizrK on 2011-06-25
terminal:
start networking
(or maybe thats backtrack...)
:p

---

### Post by chili555 on 2011-06-25
> **trizrK said:**
> terminal:
start networking
(or maybe thats backtrack...)
:pAre you running Ubuntu? Please try it and let us have your report.

---

### Post by tomns on 2011-06-25
Bingo!  start networking did it.  I can't believe it was that simple after all I've tried ..

Thank you very much.

---

### Post by trizrK on 2011-06-25
> **tomns said:**
> Bingo!  start networking did it.  I can't believe it was that simple after all I've tried ..

Thank you very much.
No problem. 
And if your wireless connection wont start automatically when you login try this:
go to **System>Preferences>Startup Applications** (This is if you're running GNOME or 'ubuntu classic', if you're running Unity the defult window program just type in startup applications on the top left search bar) then click "Add" name it something like 'network startup' and add this command: **networking start** . Hope that helps
cheers

---

