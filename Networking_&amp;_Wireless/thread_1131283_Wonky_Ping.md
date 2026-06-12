---
title: "Wonky Ping"
date: 2009-04-20
forum: Networking &amp; Wireless
---

### Post by heckflosse230 on 2009-04-20
Hi,

I have a problem with ping running on a Freescale MPC8313 board with Linux version 2.6.20.

DHCP appears to work fine:

~ # udhcpc -i eth1
udhcpc (v0.9.9-pre) started
udhcpc[796]: udhcpc (v0.9.9-pre) started
Sending discover...
udhcpc[796]: Sending discover...
Sending select for 192.168.1.207...
udhcpc[796]: Sending select for 192.168.1.207...
Lease of 192.168.1.207 obtained, lease time 86400
udhcpc[796]: Lease of 192.168.1.207 obtained, lease time 86400
deleting routers
SIOCDELRT: No such process
adding dns 64.59.144.18
adding dns 64.59.144.19

BTW Does 'SIOCDELRT: No such process' mean anything ominous?

The problem is that I can't ping anything on the local network, either at home or at work.

And I can't ping the board with my PC.

I tried another board that hasn't been worked on before and same issue again.

Last week the board, PC and the virtual Suse machine were pinging each other back and forth.

I can however ping outside the network. I've tried [www.asp.net](www.asp.net), yahoo.com, spiegel.de and google.com and those work fine.

msn.com and microsoft.com fail, though the IP address is resolved.

I can't ping one of the DNS servers.

I've been read and asking various people but I can't figure out what's wrong.

How do I diagnose this?

Thanks,
Chris Plasun

---

