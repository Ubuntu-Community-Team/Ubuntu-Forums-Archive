---
title: "Have MAC add.Don't know i.p., how can I find it.."
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by VipX1 on 2009-08-17
We have a problem in work. An i.p. device isn't showing up and we can't connect to it either. I looked for it on eth0 with EtherApe and I can't see an i.p., I think the device is broken. I rang my manager and he said he'll use ARP on a windows laptop when he gets back this afternoon.

I can see the man entry for ARP in Ubuntu. How do I find an i.p. address when I have the MAC address using ARP?

I want to score one for my Ubuntu... Thanks for any help..

---

### Post by BbUiDgZ on 2009-08-17
you could try [http://www.wireshark.org/](http://www.wireshark.org/) although im no networking expert

---

### Post by Iowan on 2009-08-17
I was recently reading about **arping** (haven't tried it, though)...

---

### Post by jonobr on 2009-08-17
Hello

The arp table  is usually only populated when the machines know the mac and associated IP address/hostname

or if you manually populate it yourself.
Arping and mac addresses are all done at layer 2 so if your device is on a different subnet you wont see it on the ARP table,

one way you can populate your arp table is to pinging the broadcast address and get all devices withing the subnet to respond, but that will generate a bit of traffic.


Anyway, getting back to your issue, it looks as if its something to do with  the device being down, disconnected or something like that. IM not sure what your boss is refeerring to by using the arp.

Unless there is some issue where by he is clearing or flushing arp caches and hoping the devices restores.
I have seen this before on Layer 2 switches or bridges where the ARP table gets messed up and needs to be cleared, however that was more to do with devices then machines.
If thats what he is doing then that can be done from any OS


Cheers


PS , I love the avatar,
Makes me want to throw out a verse from Irelands call or Sin a fianna fail....

PPS- I should mention Im part of the diaspora living in California.

---

### Post by VipX1 on 2009-08-20
> **jonobr said:**
> 
Anyway, getting back to your issue, it looks as if its something to do with  the device being down, disconnected or something like that. IM not sure what your boss is referring to by using the arp.


I just thought I'd finish the story:
The device was faulty or at least we came to that conclusion and we have sent it back to the manufacturer, they'll confirm our prognosis .
My manager didn't achieve any more success than me using the 'arp' command when he came back to the office in the afternoon. It worked out much the way you have out-lined jonobr, Thanks.
* I plan to educate myself futher in tcp/ip networking

---

### Post by jonobr on 2009-08-20
Mo Chara


Go raibh mile maith agat for the follow up post

Slan agus beannacht

jonobr

---

