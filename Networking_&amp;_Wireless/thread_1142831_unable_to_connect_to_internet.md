---
title: "unable to connect to internet"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by rock_pec on 2009-04-29
Hi All,

After trying in vain to setup my netgear PCI wireless card (though I am not new to linux and followed the ndiswrapper guide word by word) dmesg shows [ndiswrapper could not initialize card error -22].

I gave up and tried another approach today. I have a small router that an also act as a wireless client .. it connects to my desktop using wired connection eth0. 

My router can see my home wireless network and connect to it. But my desktop cannot connect to the internet.

I setup the receiver router as the default gateway -

Machine IP - 198.168.1.4
Router IP - 192.168.1.1

I tried using OpenDNS and the router IP as my DNS servers. But nothing came. I can ping my router at 192.168.1.1 but apart from that nothing works.

My setup is like this 


Wireless router 1 ---wireless-- Wireless receiver --wired-- PC.


Can anyone please help.

Thanks.

---

### Post by tripolitan on 2009-04-29
According to your description, "technically" there are TWO routers in your network. WIRELESS ROUTER1 >> Wireless Router2->wire->PC.

So, you might have a routing problem.

Remove all OpenDNS IPs from both routers and PC, use dhcp for your client-router and dhcp for your PC
turn off all then restart your main wireless router, then (a minute later) your client-router then (a minute later) your PC

If that doesn't work, post ifconfig, route and your /etc/network/interfaces

Also, post your Wireless router1 IP (192.xxx) and your client-router2 IP and your machine's IP (assuming it is different from what you mentioned in  your question) and finally, what version are you using???

p.s. Have you tried installing the D-Link PCI card in a different PCI slot?

---

