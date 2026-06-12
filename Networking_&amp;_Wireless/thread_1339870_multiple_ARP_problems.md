---
title: "multiple ARP problems"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by andytof47 on 2009-11-28
Hi Guys, I have a static IP address assigned to one of my wireless cards, I have got rid of network manager too.

I can successfully associate with one of my AP's but when i try to connect to the net it just times out.

I can ping from the command line my internet nameserver......

so there is outside connectivity.

I have manually played with some of my netowrk files but anyhow when I wireshark what's going on. 

I watch my traffic and the NIC is asking one of the old gateways who has google.com.


So How do I flush the arp tables?  cheers guys

---

### Post by Yoann Juet on 2009-11-28
> **andytof47 said:**
> I can ping from the command line my internet nameserver......

so there is outside connectivity.

ok, you have at least a valid gateway to join the nameserver.

> I have manually played with some of my netowrk files but anyhow when I wireshark what's going on. 

I watch my traffic and the NIC is asking one of the old gateways who has google.com.

what do you mean by old gateway ? Have you played with static arp entries and/or static routes (except the default route !)

> So How do I flush the arp tables?

print arp table : arp -a
delete an entry : arp -d xxxxxx

---

### Post by andytof47 on 2009-11-29
> 
Quote:
So How do I flush the arp tables?
print arp table : arp -a
delete an entry : arp -d xxxxxx 

thanks for that.


And as for the default gateway it's a bit like this.

I have static address assigned to this wireless nic. It attaches to one of my 1st gateway on a DMZ zone 10.0.0.1/24 i use this for torrents etc.

but my 2nd one for work is a different connection and a different router on a diferent subnet 192.168.1.1/24

so naturally my default GW is different, but that's about all I add/change

It's been a while since i've needed my (at least 2 days) tplink router.. yet the router is still persistent in wireshark....arrrrgg

I will research the arp command.

thanks very much for your help

---

