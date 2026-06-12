---
title: "Shared internet help"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by aaronmarsh632 on 2009-05-24
Hi,

ok here's the situation. I have just moved house, no broadband, so im using next doors (its ok i have permission)

I cant connect my ubuntu pc using the wireless because its too far away, so I have connected my windows laptop to the wireless and shared the wireless connection. I have setup static ips on the ethernet connections of both the laptop and the ubuntu pc and connected them up via lan cable. But im not getting any internet on the ubuntu pc. however if I click places>network bla bla, the ubuntu pc can see my windows laptop.

Can anyone help me get the internet on the pc?

Thanks

---

### Post by Iowan on 2009-05-24
My first thought was that the cable needed to be crossover instead of straight - but if Ubuntu sees the Windows box...
Can Ubuntu **ping** Windows? (duh... it sees it).
Is gateway address set to Windows box?
Is /etc/resolv.conf configured for DNS server?

---

