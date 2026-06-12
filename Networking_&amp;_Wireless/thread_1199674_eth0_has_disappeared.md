---
title: "eth0 has disappeared"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by robforrest25 on 2009-06-29
Hi all,

I'm completely baffled by what has happened so I'm hoping that one of you might be able to suggest something.

I very recently installed a server running Ubuntu 8.04 (LTS) and had got everything set up perfectly.  On deploying the server in the office eth0 came up alright.  Foolishly on my part there was an IP address conflict, without thinking about it I had assigned the new server the same IP address as the current DHCP server.  Anyway, I changed that in the static IP address list in dhcpd.conf and went to reset the new server.  Now for some reason, eth0 seems to have disappeard.

ifconfig shows nothing for eth* only 'lo'.
/etc/init.d/networking restart gives the following
>  * Reconfiguring network interfaces
eth0: Error while getting interface flags: no such device
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
...
...
...
...
SIOCSIFADDR: No such device
eth0: Error while getting interface flags: no such device
eth0: Error while getting interface flags: no such device
bind socket to interface: no such device
Failed to bring up eth0as suggested by others I did a dmesg | grep -i eth0 but that produces nothing.

Physically the network cable is definately still connected with lights flashing on the back of the network card and on the hub.

I've using the onboard network adapter on a Gigabyte EX58-UD4P Motherboard

Any help would be greatly appreciated.

Many Thanks

Rob

---

### Post by robforrest25 on 2009-06-29
Please ignore this, seemingly after powerering down the system for the nth time, it transpires that udev shifted eth0 to eth1.  Now I'm just using eth1 instead.

Thanks all the same for providing a great support forum full of usefull information.

Rob

---

