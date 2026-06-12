---
title: "Broadcast traffic sources"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by Sarmacid on 2009-11-12
Hey, I'm in a network with a high amount of broadcast traffic, around 40% according to ntop and I was wondering what's the best way to determine the sources of the traffic and sort them by amount of broadcast traffic they send. So far I've captured with wireshark, exported to openoffice.org calc and trying to figure it out. Is there any simpler way to do this?

---

### Post by Logan1985 on 2009-11-12
How many devices are in your network?

Sometimes in Wireshark the MAC address get's summarized so that the first half is the Vendor ID...does that give you any clues?

How many devices are we talking about?

---

### Post by Sarmacid on 2009-11-12
On a capture running for just a few minutes I picked up at least 163 different IPs.

I don't see how your second line would help me, I basically want to know how much broadcast traffic are the devices generating. I already managed to pull it off with the method in my first post, but can't help but wonder if there's an easier way to do it.

---

### Post by Logan1985 on 2009-11-12
Well the idea was that if it's prefixed with the hardware manufacturer, it may help you to determine what devices are sending out all the traffic. Eg I see broadcast traffic on my network from 2wire:xx-xx-xx...so I know it's a 2wire device.

Perhaps I just misunderstood what you were trying to achieve. Initially you mentioned wanting to find out the source of the traffic, rather than how much there was. Apologies if I have got it wrong. 

Is this an office network? Is it switched? If so how are you seeing all that traffic? are you mirroring lots of ports? Is it ARP you are seeing?

Perhaps if you can give some more info you may get more answers. Of perhaps I am just missing the point...apologies if so.

---

### Post by Sarmacid on 2009-11-16
Thanks, for the replies, I already solved the problem, just needed to run some commands to the file with all the IPs.```
awk '{print $1}' file.txt | sort | uniq -c | awk '{print $2, $1, $1/'`wc -l file.txt | awk '{print($1)}'`'*100}'

```

Basically, what I do is capture traffic with wireshark, filter out the non broadcast traffic, save it as .csv and remove the fields that are not the IP address, then run the command. It shows how many packets which IP sent and what's the % over the total.

---

