---
title: "Netmask and IP range"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by viralmeme on 2010-10-20
A NATed network uses a netmask of 255.255.255.0 on the clients, yet I see IP addresses in the range, 192.168.2.x and 192.168.3.x . What gives, I thought they all had to be of the form 192.168.2.xxx ..

---

### Post by marc.verwerft on 2010-10-20
I'll try to explain a bit (simplified). Suppose you have one computer with one ethernet connection.
That card has an IP address and a netmask. When you start browsing e.g. your computer has to know how to get to that other computer. The first step the computer takes is to ask: is that other computer 'next' to me or not? The way he answers this question is to take the address of the other computer and apply the netmask.
Suppose you computer's address is 192.168.2.12 and netmask 255.255.255.0. The other computer is 10.20.30.40.
First step:[COLOR=#000000][FONT=monospace]
[/FONT]Address:         [/COLOR][COLOR=#0000ff]192.168.2.12                            [/COLOR][COLOR=#909090]11000000.10101000.00000010 .00001100[/COLOR][COLOR=#000000][FONT=monospace]
[/FONT]Netmask:        [/COLOR][COLOR=#0000ff]255.255.255.0 = 24             [/COLOR]11111111.11111111.11111111 .00000000
[COLOR=#000000]Address:   [/COLOR][COLOR=#0000ff]10.20.30.40           [/COLOR][COLOR=#909090]00001010.00010100.00011110 .00101000[/COLOR]
[COLOR=#000000]Netmask:   [/COLOR][COLOR=#0000ff]255.255.255.0 = 24    [/COLOR][COLOR=#ff0000]11111111.11111111.11111111 .00000000[/COLOR]Everywhere you see '255', the original bits from the address are kept. Simply said, the PC compares
10.20.30 to 192.168.2 and sees that they are different. So they do not belong to the 'same' network.
Next step is that the computer goes to the gateway and says: can you find this ip address for me?

Going back to your question, the netmask is used to filter out the first part (or network part) of ANY ip address just to know whether it is local (i.e. within the same network) or remote. It has nothing to do with restricting the IP address of the computer (as you implied with your question)

More info on:
[http://www.faqintosh.com/risorse/en/guides/net/tcp/basic/](http://www.faqintosh.com/risorse/en/guides/net/tcp/basic/)
[http://en.wikipedia.org/wiki/Subnetwork](http://en.wikipedia.org/wiki/Subnetwork)

Regards,

Marc
[COLOR=#ff0000]
[/COLOR]

---

### Post by viralmeme on 2010-10-21
> **marc.verwerft said:**
> the netmask is used to filter out the first part (or network part) of ANY ip address just to know whether it is local (i.e. within the same network) or remote. It has nothing to do with restricting the IP address of the computer
That's the clearest explanation I've seen, thanks for the response ..

---

