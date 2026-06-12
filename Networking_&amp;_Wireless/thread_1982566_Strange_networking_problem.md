---
title: "Strange networking problem"
date: 2012-05-18
forum: Networking &amp; Wireless
---

### Post by NiksaVel on 2012-05-18
Hey all,

I have recently changed my home routers and came to a need to use a fixed IP for the first time. 

So I went and set up a new connection in network-manager and got the assigned values.

Now here is the strange part...  if I use the manually assigned fixed IP I have local network connectivity, but no internet. If I use DHCP I have both (but my local shares dont work if I keep changing the IP - hence the need for a fixed one).

Looking that the ifconfig output I get completely identical output, wether I use DHCP or manual...   but on manual no internet.

(checked and triple checked that gateway, subnet and DNS settings indeed are identical).

Anyone got any ideas?

---

### Post by papibe on 2012-05-18
Hi NiksaVel.

A few thoughts.

Some routers only support static LAN IPs in a predetermined range. Be sure your IP is in that range.

When setting an static IP, you also need to set the DNS servers manually. I image that your own router serves as a DNS for the LAN.

The simplest solution would be to setup DHCP revervation on your router rather that deal with the configuration on the machine. Check if your router supports that functionality.

Regards.

---

### Post by NiksaVel on 2012-05-19
Hi,

thanks for the quick reply:

1. I used DHCP reservation on my previous router (used IPcop on an old P1 compoter, but due to age it started breaking down all the time)...  the new one is a Linksys WAG120N and it doesn't appear to support that function...  hence my troubles with static IPs

I have set manually all the fields...  gateway, subnet, dns...   and my ifconfig output appears the same wether I use DHCP or static....

I even tried using the same IP address that was assigned to me by DHCP... as soon as I switched to static same behaviour.

One more thing I noticed is that my torrents download either way. Which just adds to my confusion...

---

### Post by steeldriver on 2012-05-19
what other devices do you have on the LAN? are they also static?

if you are using static ANYWHERE and you can't reserve those addresses on the router (i.e. stop its DHCP server from potentially handing out conflicting addresses) then really you should disable DHCP and go static everywhere

however I don't know why that would give your particular symptoms - what diag have you done? what do you see if you try to 'traceroute google.com' or similar when it's not working versus when it's working?

---

### Post by papibe on 2012-05-19
> **NiksaVel said:**
> I even tried using the same IP address that was assigned to me by DHCP... as soon as I switched to static same behaviour.

That may be the problem. You usually can't use the same address because of the limitation on the routers range.

Take a look at this [thread]("http://homecommunity.cisco.com/t5/Cable-and-DSL/WAG120N-DHCP-Reservation/td-p/384941") on the Cisco forums (post #5 - with the workaround). Basically it says:
[LIST]
[*]Define the range for static IPs on your router.
[*]Choose an IP on that range to set your local machine settings.
[/LIST]
I hope that helps, and tell us how it goes.
Regards.

---

### Post by NiksaVel on 2012-05-20
Hello again,

I just wanted to mark this as solved...

this router model does not support DHCP reservation, but you can specify a DHCP range...  this does not help me in any way however since my problem was related to my own mistake...   I specified my ISP DNS server in the network-manager.  As soon as I entered my router's local address everything started working fine.

Strage symptoms in any case...

thanks to everyone for the help!

---

