---
title: "iptables, running two separate MASQUERADEs"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by jwatte on 2009-01-01
I'm needing some help with iptables and MASQUERADE.

I have a mostly headless server running x86-64 8.04 server with LTS. (It has previously been running LFS since... 1997? Something like that. It's like the 1,000 year old axe that's had 8 new handles and 3 new heads :-)

Anyway, my home network currently looks like:

DSL with public IP
-
eth1 on Linux box as public IP
eth0 on Linux box as private IP (10.0.x.y range)
-
zone with 10.0.x.y network devices, mixed static and DHCP (different subneets)
-
eth0 on wireless gateway, using 10.0.x.y static IP
WLAN on wireless gateway with NAT, (192.168.1.x range)
- 
zone with 192.168.1.x network devices, DHCP served from the wireless gateway

The wireless gateway has a static IP in the 10.0 range.

Now, I would like to add another public IP, on the top side, coming from Comcast. Clearly, important stuff can't go on that interface, but things like streaming Netflix to my Xbox, and my family's wireless web surfing, can probably go there to great effect, leaving the DSL for more serious work :-)

No, I believe I need to do a few things to make this work, but I'm not quite sure how to go about them.

1) I will create a new logical interface, called eth1:1, which gets a DHCP address from the Comcast cable modem. The physical wiring from the linux box to the DSL (and cable modem) is through a simple hub. Because the DSL is static IP, and my DSL provider does not run a DHCP server on my subnet, that should work alright (fingers crossed).

2) I currently have an iptables rule that says something like:
-A POSTROUTING -s 10.0.0.0/255.255.0.0 -o eth1 -j MASQUERADE
I will need to restrict that down to a smaller subnet. I can then create a second rule that says something like:
-A POSTROUTING -s 10.1.0.0/255.255.0.0 -i eth1:1 -j MASQUERADE
This will cause data from 10.1.x.y through eth1:1 (cable) to be masqueraded separately from 10.0.x.y going through eth1 (DSL).

Now, I'm not sure this is enough. How does the routing in the box "know" that 10.1.x.y data should go through eth1:1, but 10.0.x.y data should go through eth1?
My guess is that I also need to add two static routes. Something like:
"if arriving from 10.0.x.y, route it through gateway DSL on eth1"
"if arriving from 10.1.x.y, route it through gateway Comcast on eth1:1"

Unfortunately, "route" seems to only want to take destination into effect, not source.

Is the second iptables MASQUERADE line (mentioning -i eth1:1) enough to make sure that 10.1.x.y traffic wants to go out on eth1:1, while 10.0.x.y traffic goes out on eth1? Or do I need to do something else?

---

### Post by mpokrywka on 2009-01-01
iptables "-i" parameter cannot be used in POSTROUTING - selecting by source IP should suffice.
Routing problem can be solved using routing "rules":
Add some additional routing table, i.e.
```

echo "10 comcast-route" >> /etc/iproute2/rt_tables

```
Add routing rule - allows selectors by input interface and source ip:
```

ip rule add iif eth0 from 10.0.0.0/16 table comcast-route

```
Add default route to "comcast-route" table
```

ip route add default via COMCAST-GATEWAY table comcast-route

```
but this part is tricky - dhcp from comcast will advertise gateway, but you do not want it to be your default gateway. You need to configure dhcp client not to request "routers" option (**man dhclient.conf**) - gateway will always be the same, but you should add script that makes sure gateway is filled (**man dhclient-script**) - default route can be set when interface is up.

I am not sure though if dhcp+static ip will work - why add yourself additional troubles that 7$ of hardware saves? Upgrade your 1000-year old axe by adding additional head... I mean - put in one additional realtek pci card, and each network connection will have its own interface.

---

### Post by jwatte on 2009-01-02
OK, there's one additional gnarl I conveniently forgot to mention: I have a printer on the "wireless" network, which wireless clients can see in the same zone, but wired clients have to set up manually, because I have a tunnel in the wireless gateway (that does NAT from internal 1 to internal 2) to the printer.

The issue is not an additional network card. The issue is drivers :-) At least half a year ago, my motherboard gig-E was still not well supported; it would die after an hour or two. Thus, I had to put in cards for both eth0 and eth1. And then I have a RAID controller card, because this box also serves a few terabytes of RAID-1 storage, and with RAID-1 you run out of channels in a hurry, and upgrading THAT would cost real money.

And, with uATX, I can't get more cards into the machine than what are already there. I do have a USB adapter of some sort laying around, but I'd really rather not trust a 24/7 set-up to that kind of shenanigan. Much better to solve it in software in this case.
And, even with an additional card, the question of DHCP on one interface but not another isn't that different between two hardware interfaces, and two logical interfaces (at least in my case, where there is no other DHCP server anyway).

Anyway: the magic words were "ip rule" -- that looks like it will solve the problem I was describing above. Thank you!

---

