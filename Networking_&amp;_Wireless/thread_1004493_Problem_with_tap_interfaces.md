---
title: "Problem with tap interfaces"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by chomique on 2008-12-07
Hello!

I have a strange problem with tap interfaces on ubuntu 8.10. I'm trying to develop some simple network emulation software based on tap interfaces. For a start I'd like to disable connectivity beetween two tap interfaces. I have following configuration:

tap0 10.0.10.0 netmask 255.0.0.0 broadcast 10.255.255.255
tap1 10.0.10.1 netmask 255.0.0.0 broadcast 10.255.255.255

For network connectivity checking I use following commands:
Listening on tap0: netcat -l -s 10.0.10.0 -p 6777
Connecting from tap1: telnet -b 10.0.10.1 10.0.10.0 6777

For the moment everything works fine. Now i'd like to disable the connectivity in the most easy manner with issuing following command:

Bring tap0 down: ifconfig tap0 down

As I suppose the tap0 interface is down, and it's not visible while listing interfaces with ifconfig.

Here comes the strangest thing. The conectivity with netcat and telnet still works despite tap0 interface is down. How is that possible? The next interesting thing is that traffic that flows through tap interfaces is only seen on lo interface. Issuing tcpdump -i tap0 while connecitivity shoud be on shows no traffic. Hovever issuing tcpdump -i lo shows all traffic that flows throug tap interfaces.

Please help!

---

