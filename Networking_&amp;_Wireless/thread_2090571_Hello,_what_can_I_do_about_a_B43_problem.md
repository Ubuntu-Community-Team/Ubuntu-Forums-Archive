---
title: "Hello, what can I do about a B43 problem?"
date: 2012-12-02
forum: Networking &amp; Wireless
---

### Post by Osd1000 on 2012-12-02
So, I have heard that if you have a wireless b43 LAN card, Ubuntu 12.04 LTS will hang up.
I am planning on installing this OS alongside Windows 7, is there anything I can do to resolve this issue?
Windows 7 64-bit
802.11n Wireless LAN Card
Can I do anything else to resolve any further issues with this?
Will there be any complications after I fix this issue?
Thanks, if you can help. :confused:

---

### Post by Osd1000 on 2012-12-02
Oh yeah, I have a HP slimline s5-1200z, 4 GB of RAM, and a 500 GB HDD.

---

### Post by oldos2er on 2012-12-03
Moved to Networking & Wireless.

---

### Post by chili555 on 2012-12-03
> **Osd1000 said:**
> So, I have heard that if you have a wireless b43 LAN card, Ubuntu 12.04 LTS will hang up.That's not true, as far as I know, and, evidently I know a lot! Not all Broadcom cards use b43. The exact driver depends on your card details. Please run the install CD live, that is, Try Ubuntu, and see if it works. If not, open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

It is remarkable the lore, urban legend and myth that gets spread around on the internet!

---

### Post by haqking on 2012-12-03
> **chili555 said:**
> That's not true, as far as I know, and, evidently I know a lot! Not all Broadcom cards use b43. The exact driver depends on your card details. Please run the install CD live, that is, Try Ubuntu, and see if it works. If not, open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

It is remarkable the lore, urban legend and myth that gets spread around on the internet!

Linux and Wireless issues are a bigger Internet Meme than rick rolling ;-)

---

### Post by chili555 on 2012-12-03
> It is remarkable the lore, urban legend and myth that gets spread around on the internet!I was actually going to use another term until I re-read the Code of Conduct! No Resolution Centre for me!

---

### Post by haqking on 2012-12-03
> **chili555 said:**
> I was actually going to use another term until I re-read the Code of Conduct! No Resolution Centre for me!

ha yeah i spend more time in the Jail than on the public forum...LOL

---

### Post by Osd1000 on 2012-12-03
> **chili555 said:**
> That's not true, as far as I know, and, evidently I know a lot! Not all Broadcom cards use b43. The exact driver depends on your card details. Please run the install CD live, that is, Try Ubuntu, and see if it works. If not, open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

It is remarkable the lore, urban legend and myth that gets spread around on the internet!

Thank you, I will now try and install this.

---

