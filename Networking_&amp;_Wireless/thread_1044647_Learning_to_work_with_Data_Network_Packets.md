---
title: "Learning to work with Data Network Packets:"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by Priest Apostate on 2009-01-19
Anyone know of an area, book, or tutorial I can check out to learn how to read Data Packets?

---

### Post by Kebabman on 2009-01-19
Just start by installing ethereal and go from there. It really depends on what information you want to get from within the packets as to what resources you will need.

---

### Post by jonobr on 2009-01-19
Hi, 

The project was renamed wireshark due to trademarking problems.

Recommend you start looking at the rulebook where how packets are put together
THis is found in the "requests for comment" or RFC.
Also, general networking books will give you an idea how a packet is made up.
Once you know how a packet is made up you can use that to look at the packets in wireshark trace and understand what each layer does.
The OSI 7 layer model will also help you understand how each layer works with the next layer, and will show how something on a physical wire, makes it up the protocol stack to the application layer.

---

### Post by Kebabman on 2009-01-19
You'd think I should know that after writing a bunch of dissectors for it after the last few months.. Anyway wireshark is definately the way to go but 'reading data packets' is still a very generic description. It depends greatly on what exactly you are looking for, what protocols are being used etc.

---

