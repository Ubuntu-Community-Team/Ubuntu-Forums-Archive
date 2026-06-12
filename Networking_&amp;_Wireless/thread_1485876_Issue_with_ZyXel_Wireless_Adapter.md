---
title: "Issue with ZyXel Wireless Adapter"
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by berilac on 2010-05-17
I have ZyXel ZyDas ZD1212B Wireless card (see below lspci):

00:0a.0 Network controller: ZyDAS Technology Corp. ZD1212B Wireless Adapter (rev 01)

I am running fresh install of Lucid 10.04.

So, it recognises the card, but doesn't have driver installed (possible?)
The main problem is that though the card is "recognised" there is no 'wireless' option in my network connections list, just 'wired networks' and vpn stuff...

Anyone have any advice as to where to begin? Is this driver issue...?

Any questions, or you need more info. Please ask.

Thank you

---

### Post by berilac on 2010-05-18
hoping someone might at least point me in right direction...

i have read through so many posts and threads, but most seem quite outdated, and either i'm doing something wrong or lucid may not be compatible with certain "solutions"...

is this perhaps lost cause, in which case i'll ask manager to buy new wireless card; then i can assure compatibility...


sorry, one other thing...this is my lshw output (for this adapter) :

```

        *-network:0 UNCLAIMED
             description: Network controller
             product: ZD1212B Wireless Adapter
             vendor: ZyDAS Technology Corp.
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=32 maxlatency=66 mingnt=2
             resources: memory:dfffb000-dfffbfff

```

---

### Post by dragon6977 on 2010-06-13
I also have a Zyxel card but it is a G302 and I can not get Ubuntu 10.04 to recognize that I have the card in the computer.  I tried going to the System / admin / Hardware  Drivers and it does not see it.  I really want to get my wireless card working.

---

