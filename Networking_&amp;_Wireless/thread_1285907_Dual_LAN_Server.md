---
title: "Dual LAN Server"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by SpiderMang on 2009-10-08
[FONT=Tahoma]I currently have a setup like this:
[/FONT][FONT=Tahoma] 
[/FONT]> [FONT=Tahoma]** Router 1 (69.11.#.#)** -[/FONT][FONT=Tahoma]**         192.168.0.69 (eth0)**
[/FONT] [FONT=Tahoma]**     Router 2 (71.17.#.#)**[/FONT][FONT=Tahoma]** - 192.168.1.71 (eth1)**
[/FONT][FONT=Tahoma]I host HTTP, DNS, SMTP, IMAP, etc. All of this goes through Router 1 except DNS which I want to go through both. Both routers are setup to forward the appropriate ports to the correct LAN  IP's. The problem is only 1 interface seems to work at a time. If I do **ifdown eth1** then DNS works on **eth0** and vise-versa. I know I have to setup **/etc/network/interfaces** with some routing and such but how do I do this? I have looked but I don't understand linux networking enough to do it. Here is my current configuration.
[/FONT][FONT=Tahoma] 
[/FONT]>  [FONT=Tahoma]**auto eth0**
[/FONT][FONT=Tahoma]** iface eth0 inet static**
[/FONT] [FONT=Tahoma]** address 192.168.0.69**
[/FONT] [FONT=Tahoma]**netmask 255.255.255.0**
[/FONT] [FONT=Tahoma]**network 192.168.0.0**
[/FONT] [FONT=Tahoma]**broadcast 192.168.0.255**
[/FONT] [FONT=Tahoma]**gateway 192.168.0.1**
[/FONT][FONT=Tahoma] 
[/FONT]  [FONT=Tahoma]**auto eth1**
[/FONT][FONT=Tahoma]** iface eth1 inet static**
[/FONT] [FONT=Tahoma]** address 192.168.1.71**
[/FONT] [FONT=Tahoma]**netmask 255.255.255.0**
[/FONT] [FONT=Tahoma]**network 192.168.1.0**
[/FONT] [FONT=Tahoma]**broadcast 192.168.1.255**
[/FONT] [FONT=Tahoma]**gateway 192.168.1.1**
[/FONT][FONT=Tahoma]I have tried removing [/FONT][FONT=Tahoma]**gateway 192.168.1.1 **but it didn't seem to help.
[/FONT][FONT=Tahoma] 
[/FONT][FONT=Tahoma] Also I have been thinking of trying this but I am not at home to do it right now. What do you think of trying this:
[/FONT][FONT=Tahoma] 
[/FONT][FONT=Tahoma] > 
** # Loopback NIC**
** auto lo**
** iface lo inet loopback**

** # Primary NIC**
** auto eth0**
** iface eth0 inet static**
**     address 192.168.0.69**
**     netmask 255.255.255.0**
**     post-up ip route add 192.168.0.0/24 dev eth0 src 192.168.0.69 table 1**
**     post-up ip route add default via 192.168.0.1 table 1**
**     post-up ip rule add from 192.168.0.69 table 1**
**     post-down ip rule del from 192.168.0.69 table 1**

** # Secondary NIC**
** auto eth1**
** iface eth1 inet static**
**     address 192.168.1.71**
**     netmask 255.255.255.0**
**     post-up ip route add 192.168.1.0/24 dev eth1 src 192.168.1.71 table 2**
**     post-up ip route add default via 192.168.1.1 table 2**
**     post-up ip rule add from 192.168.1.71 table 2**
**     post-down ip rule del from 192.168.1.71 table 2**
[/FONT]

---

### Post by SpiderMang on 2009-10-08
Didn't get many reads on this, is the question unclear?

---

