---
title: "obtain new ip from dhcp server"
date: 2011-12-25
forum: Networking &amp; Wireless
---

### Post by hg088 on 2011-12-25
hi

in order to do this im trying this:
```
sudo dhclient eth2 -r -v && sudo rm /var/lib/dhcp/* && sudo dhclient eth2 -v
```and the output:
```
Internet Systems Consortium DHCP Client 4.1.1-P1
Copyright 2004-2010 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth2/00:30:0a:19:6e:ff
Sending on   LPF/eth2/00:30:0a:19:6e:ff
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client 4.1.1-P1
Copyright 2004-2010 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth2/00:30:0a:19:6e:ff
Sending on   LPF/eth2/00:30:0a:19:6e:ff
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 3
DHCPOFFER of wan-ip1 from wan-ip2
DHCPREQUEST of wan-ip1 on eth2 to 255.255.255.255 port 67
DHCPACK of wan-ip1 from wan-ip2
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload smbd
RTNETLINK answers: Numerical argument out of domain
bound to wan-ip1 -- renewal in 1498 seconds.

```but this is not working for me. im conected to the modem via usb

in windows xp, on the same machine, i can run this .bat file in order to succesfully obtain a new ip:
```
@echo off
ipconfig /release
netsh interface IP set address "Internet" static 1.2.3.4 255.0.0.0 1.2.3.5 20
netsh interface ip set address name="Internet" source=dhcp
ipconfig /renew 
```so, i was hoping tha someone tells me what im doing wrong in linux

---

### Post by hg088 on 2012-01-07
ive finally managed to find a way to get a new ip without changing my mac.
apparently  the trick was to ask the dhcp server for an specific ip and  this forces  it to give me a different ip. dont really know why since im  a total  noob [IMG]http://crunchbanglinux.org/forums/img/smilies/sad.png[/IMG]
this can be done using the send option in the dhcilent.conf file
so every time i want to get a new public ip i just have to run this bash script i made

     ```
sudo dhclient -r -v eth2 && sudo rm /var/lib/dhcp/*
sleep 1
sudo sh -c "echo 'interface \"eth2\" { send dhcp-requested-address 1.2.3.4;}' >> /etc/dhcp/dhclient.conf"
sleep 1
sudo dhclient -v eth2 &
sleep 1
sudo sed -i '$ d' /etc/dhcp/dhclient.conf
sleep 3
sudo killall dhclient
sleep 6
sudo dhclient -v eth2
```

---

