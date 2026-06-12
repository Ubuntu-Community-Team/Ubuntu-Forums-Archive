---
title: "Can't connect to wireless AND mobile concurrently"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by demonboy on 2010-11-25
Hi,

I connect to the internet via mobile GPRS dongle, which works fine. I've also created my own ad hoc wireless network to get the local machines to talk to each other, which also works fine. However I can't connect to both items at the same time. I can always connect to the wireless network but when I do I lose connection to the internet via mobile dongle.

I have my ad hoc network configured thus:

> 
IPv4 settings:
Address: 192.255.0.1
Netmask: 255.255.255.0
Gateway: 1.1.1.1

RequireIPv4 addressing for this connection to complete is unticked.
Band and MTU are automatic


Any clues as to why they both can't connect concurrently? I know this is possible as another forum user has the same set-up but wasn't able to identify how he did it.

---

### Post by demonboy on 2010-11-28
Anyone?

---

### Post by demonboy on 2010-11-28
Follow-up in case anyone else has the same problem:

Thanks to [Spiky001]("http://ubuntuforums.org/member.php?u=915355") I was able to compare my set-up with someone who had this configuration working successfully. It transpires that the Wireless Network IPv4 METHOD of connecting isn't Automatic, but 'Shared to Other Computers'. I'm not sure this is explained in the official documentation but that is the solution that works for me.

Thanks to Spiky for his time.

---

