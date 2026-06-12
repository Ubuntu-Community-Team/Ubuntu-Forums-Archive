---
title: "Isc-dhcp-server help"
date: 2012-07-12
forum: Networking &amp; Wireless
---

### Post by jwsicomputing on 2012-07-12
Hi there,

I have isc-dhcp-server up and running perfectly, but the thing is none of the clients are able to get internet access. I think the problem lies in my iptables which i think i have messed up:

my ip tables photo is attached if you could look and identify any errors that would be great.


Basically internet/WAN is on eth1 and DHCP clients are on eth0

If you need any other info don't hesitate to ask.

Many thanks,
James

---

### Post by Kirk Schnable on 2012-07-13
Can you please post the output of "route -n" and "ifconfig" on your client?

If your clients can ping the IP of eth0 on your server, then it's not a DHCP issue, it's either going to be iptables rules on your server not doing their job, or an incorrect default gateway set on the client. 

Kirk

---

