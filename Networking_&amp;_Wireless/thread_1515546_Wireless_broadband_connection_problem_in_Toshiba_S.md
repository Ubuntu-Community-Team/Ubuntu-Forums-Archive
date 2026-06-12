---
title: "Wireless broadband connection problem in Toshiba Satellite Laptop"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by santaprosad on 2010-06-22
Dear all,
I'm facing problems while connecting my laptop to internet via wireless. I'm using BSNL provided broadband connection. Modem is SL2_141 from Siemens with wi-fi support. After installation of Ubuntu 10, available networking is shown in the taskbar. Auto Default connection is created for wireless. It get's connected via eth1. But I couldn't provide the dial-up information (i.e. login and password) there to get connected to internet. If I edit the settings it becomes disconnected. I've tried with creating another wireless connection profile. But it also failed.

Lastly I've succeeded with *pppoeconf* command. It got connected. I've browsed for that session. But after shutting down and restarting the laptop it's not working. Also, no icon for networking in the taskbar also. I've tried with *sudo service networking start*. But no result. It's showing networking busy/stop.

Please help to get rid of this problem.

---

### Post by dineshs on 2010-06-23
Please try this
To bring NM icon back.type this in a terminal
```
sudo gedit /etc/network/interfaces
```
the file should contain only this
```
auto lo
iface lo inet loopback
```
commentout all other lines (put a # before all other lines) or modify the file after making a backup then save
Now restart the machine
If your NM is back configure the connection via the DSL tab in NM and do not attempt to use pppoeconf command.While doing this tick the option [COLOR="Blue"]Available to all users[/COLOR] PL see the attachment

_Another method_ which does not require a connect/disconnect process.If you do this the connection will be always on.
Open  Firefox
Type [COLOR="Blue"]192.168.1.1[/COLOR] in Address bar. Click GO
Enter both Username and Password as [COLOR="Blue"]admin[/COLOR]
Click OK
Click ADSL
Click WAN
Click edit at the right end of the line having 0/35 as VPI/VCI value
Click Next
select PPP over Ethernet and click next
Enter  PPP Username and PPP Password as allotted by BSNL in the respective fields 
Click Next
Click Next again
Click save
Click save/reboot
wait till reboot complete (3 minutes)

---

### Post by fire.for.effect on 2010-06-26
question...

what about the service? the tech support dude from earthlink says i don't need that to connect to their wireless broadband connection. i'm feelin that may be a part of my problem but i don't know.

perhaps the settings you input to firefox cured that issue? not tracking here and all of this sounds like what i need to do but just thought i would ask.

thanks in advance.

---

