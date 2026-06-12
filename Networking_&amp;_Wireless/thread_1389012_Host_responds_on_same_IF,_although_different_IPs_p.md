---
title: "Host responds on same IF, although different IPs pinged"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by ripeart on 2010-01-23
Strange issue going on here...

I have two machines, one has a wireless connection to my LAN [client], the other a wireless and wired [host]. I've configured /etc/network/interfaces as such:
[INDENT][FONT=Microsoft Sans Serif]# Primary Interface[/FONT]
[FONT=Microsoft Sans Serif]auto eth0[/FONT]
[FONT=Microsoft Sans Serif]iface eth0 inet static[/FONT]
[FONT=Microsoft Sans Serif]address 192.168.1.2[/FONT]
[FONT=Microsoft Sans Serif]gateway 192.168.1.1[/FONT]
[FONT=Microsoft Sans Serif]netmask 255.255.255.0[/FONT]
[FONT=Microsoft Sans Serif]network 192.168.1.0[/FONT]
[FONT=Microsoft Sans Serif]broadcast 192.168.1.255[/FONT]

[FONT=Microsoft Sans Serif]# Wireless[/FONT]
[FONT=Microsoft Sans Serif]auto eth1[/FONT]
[FONT=Microsoft Sans Serif]iface eth1 inet static[/FONT]
[FONT=Microsoft Sans Serif]address 192.168.1.3[/FONT]
[FONT=Microsoft Sans Serif]gateway 192.168.1.1[/FONT]
[FONT=Microsoft Sans Serif]netmask 255.255.255.0[/FONT]
[FONT=Microsoft Sans Serif]network 192.168.1.0[/FONT]
[FONT=Microsoft Sans Serif]broadcast 192.168.1.255[/FONT]
[/INDENT]On the client machine I'm ssh'ed into the host and watching bmon. Looking at bmon and issuing ping 192.168.1.2 -s 9999 from the client I can see 10k packets on host RX of eth0. However issuing the same command to .3 responds on eth0 as well!  Unplugging the host ethernet cable causes ping (.3) to not respond. How could this be happening?   :-?

Additionally, the wired/wireless is running a fresh install of 9.04 minimal, and I have not joined it to the WLAN.

Thanks you!

---

### Post by Iowan on 2010-01-24
Having both interfaces in the same subnet may be confusing the machine. I presume the gateway is connected to eth1. **route -n** will (might) tell you where the packets are *supposed* to go.

---

