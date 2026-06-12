---
title: "Problem with ipredator VPN routing on 10.04 lucid"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by neg3v on 2010-10-23
Hi,

I'm going crazy trying to figure this out.  I had this working fine on Centos 5.5 but since switching to ubuntu I can't seem to make it work.

This is a server and I don't have X installed so none of the guides for desktops are relevant.

I have my ipredator pptp vpn configured correctly and it comes up fine.  I can ping the endpoint, and if I add a route to say google:

# host google.co.uk |grep has
google.co.uk has address 173.194.36.104

# ip route add 173.194.36.104 via <vpn ip address>

I can ping the host no problem.  All fine and good.

Now I want to have one non-root user (lets call him bob) for whom ALL traffic will go over the vpn.  To do this I have marked the user's packets in the iptables mangle table:

*mangle
:PREROUTING ACCEPT [444:43563]
:INPUT ACCEPT [444:43563]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [402:144198]
:POSTROUTING ACCEPT [402:144198]
-A OUTPUT -m owner --uid-owner bob -j MARK --set-mark 0x1
COMMIT

I also masquerade traffic coming out of ppp0 in the nat table so that the source ip address is correct:

*nat
:PREROUTING ACCEPT [127173:7033011]
:POSTROUTING ACCEPT [31583:2332178]
:OUTPUT ACCEPT [32021:2375633]
-A POSTROUTING -o ppp0 -j MASQUERADE
COMMIT

BTW - all traffic in and out of ppp0 (including FORWARD) is -j ACCEPT for the purposes of debugging, so I don't think iptables is the problem.

Then I created a routing table for the user:

echo 201 bob >>/etc/iproute2/rt_tables

then i created a rule to pass traffic for bob into the alt routing table:

ip rule add fwmark 0x1 lookup bob


# ip rule
0:	from all lookup local 
32762:	from all fwmark 0x1 lookup bob
32766:	from all lookup main 
32767:	from all lookup default 


Now at this point, bob has an empty routing table and can ping out and connect to hosts via tcp with no problems.

I then add a default route for bob to the new routing table:

# route add default dev ppp0 table bob

Now bob cannot talk to any internet hosts at all.  If I tcpdump the traffic when bob tries to telnet to [www.google.co.uk](www.google.co.uk) port 80, I can see the SYN going out and the SYN/ACK coming back in, but there it stops.  Somehow the SYN/ACK doesn't get noticed by the calling program.

What's even weirder is if I now add a static route to the host bob was trying to connect to, to the main routing table, to go over ppp0, suddenly bob can talk to the host.

I've compared the tcpdump output from before and after adding this last rule to the main table and I can't see any discernable differences other than the fact that the second one gets further, i.e. the tcp 3way handshake completes.

What am I missing here?

---

### Post by neg3v on 2010-10-25
bump...

---

