---
title: "autonegotiation"
date: 2006-02-14
forum: Networking &amp; Wireless
---

### Post by dannemil on 2006-02-14
I am having trouble with my wired ethernet connection running very, very slowly. Here are some diagnostics

>mii-tool eth0
eth0: no autonegotiation, 10baseT-HD, link ok

Can someone help me with the no autonegotiation setting? Should it be set to negotiate?

dannemil@InvisionUbuntu:~$ dmesg | grep eth0
[4294704.678000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:11:43:74:77:4e
[4294776.268000] b44: eth0: Link is down.
[4294779.268000] b44: eth0: Link is up at 10 Mbps, half duplex.
[4294779.268000] b44: eth0: Flow control is off for TX and off for RX.
[4294790.522000] eth0: no IPv6 routers present
[4294940.196000] b44: eth0: Link is up at 10 Mbps, half duplex.
[4294940.196000] b44: eth0: Flow control is off for TX and off for RX.
[4294950.196000] NETDEV WATCHDOG: eth0: transmit timed out
[4294950.196000] b44: eth0: transmit timed out, resetting
[4294950.197000] b44: eth0: Link is down.
[4294954.197000] b44: eth0: Link is up at 10 Mbps, half duplex.
[4294954.197000] b44: eth0: Flow control is off for TX and off for RX.
[4294965.428000] eth0: no IPv6 routers present


It says that flow control is OFF for transmit and receive. Shouldn't this be set to ON?

Thanks, Jim

---

### Post by mips on 2006-02-14
Is the hardware good, adapter, cable, switch/router ?

Does the duplex & speed settings on both sides match ? Try hard coding them.

Post output of sudo **mii-diag** here.

---

### Post by dannemil on 2006-02-14
[QUOTE=mips]Is the hardware good, adapter, cable, switch/router ?

Does the duplex & speed settings on both sides match ? Try hard coding them.

Post output of sudo **mii-diag** here.[/QUOTE]


I am pretty sure all of the hardware is working OK. It is just that the connection is incredibly slow only when I am on the wired interface. I have tried setting the dns nameservers in resolv.conf thinking that it might be a dns problem, but that doesn't seem to help at all. 

Here is the output if mii-diag.

dannemil@InvisionUbuntu:~$ mii-diag
Using the default interface 'eth0'.
SIOCGMIIPHY on eth0 failed: Operation not supported

What's up with that?

---

### Post by mips on 2006-02-14
[QUOTE=dannemil]
What's up with that?[/QUOTE]

Hmm, my pc responds exactly the same.

---

