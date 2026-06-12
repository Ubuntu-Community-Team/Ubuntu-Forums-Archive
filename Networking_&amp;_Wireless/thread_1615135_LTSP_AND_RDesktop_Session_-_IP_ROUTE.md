---
title: "LTSP AND RDesktop Session - IP ROUTE"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by jtwood on 2010-11-06
I have set up an LTSP server and I have successfully booted into LDM.

Not necessarily a newbie to Linux, just been away for way too long.  Unfortunately, that hasn't posed as much of a problem as my weak knowledge of networking.

The machine I have has 2 NICS

eth0 dhcp on 192.168.83.0

eth1 static 192.168.0.1

When I boot the thinclient from the LTSP server I would like to go right into an Rdesktop connection to a server on 192.168.83.0 on eth0

(As most people know - Windows Users panic at the thought of LINUX and anything without a start menu...:))

The thinclients are booting on 192.168.0.0 on eth1

I am positive that my problem stems from the fact that the request going to 192.168.83.10 (the Win TS) is not getting from 192.168.0.0 (eth1) to 192.168.83.0 (eth0).  I have looked at route add but I am having one heck of a time trying to decipher it all.  I know just enough about networking to get into trouble but not to get back out of it.

I tried doing a quick fix using firestarter and ics but quickly ran into more problems than I needed with the dhcp and tftp servers on the LTSP server.

This is a test setup so it does not have to be set up in any secure fashion.  I do need to keep the interfaces setup as they are because of the existing 192.168.83.0 network is a production setup as well as the WIN TS server.

In the production setup I will let one of our other net admins know what I need and he will set it up in the dhcp server.

Additionally, any traffic would probably have to be NATed through the LTSP server because of our network config.  IE: Anything coming from the 192.168.0.0 net to 192.168.83.10 would have to look like it came from 192.168.83.0

Thanks in advance

---

