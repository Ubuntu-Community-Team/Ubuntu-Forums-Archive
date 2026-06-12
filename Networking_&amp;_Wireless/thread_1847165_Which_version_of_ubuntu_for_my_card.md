---
title: "Which version of ubuntu for my card?"
date: 2011-09-20
forum: Networking &amp; Wireless
---

### Post by kingsizepsc on 2011-09-20
Can someone tell me which version of ubuntu is good for my wireless card - Dell Wireless 1390 WLAN Mini-Card , because i don't want to install any drivers for that wireless card...
Thanks in advance

---

### Post by chili555 on 2011-09-20
Without more details about your card, we can't tell you. If it is, as I expect, a Broadcom, you probably won't have to install any drivers, but will have to install firmware. If you can get a wired ethernet connection, it is a three minute process.

Please open a terminal and run and post:```
lspci -nn | grep 0280
```We'll be glad to tell you more once we know the card.

---

### Post by josephmills on 2011-09-20
> **chili555 said:**
> Without more details about your card, we can't tell you. If it is, as I expect, a Broadcom, you probably won't have to install any drivers, but will have to install firmware. If you can get a wired ethernet connection, it is a three minute process.

Please open a terminal and run and post:```
lspci -nn | grep 0280
```We'll be glad to tell you more once we know the card.

remember the dreaded hotkey for dell what is it alt+f4 ? 

also what is 0280 <-- ?? is that some thing that you can grep out for all wireless cards? or just broadcom ?

thanks chili glad to see you back and hope you had a good vacation

---

### Post by chili555 on 2011-09-20
> also what is 0280 <-- ?? is that some thing that you can grep out for all wireless cards? or just broadcom ?Yes, in 98% of cases. Try it yourself:```
lspci -nn
```On my system, it yields:> <snip>
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility X1400 [1002:7145]
02:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a]
03:00.0 Network controller [[COLOR="Red"]0280[/COLOR]]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
15:00.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]As you can see, 0200 is also helpful!!

We all learn something new every day, don't we?

---

### Post by josephmills on 2011-09-20
> **chili555 said:**
> Yes, in 98% of cases. Try it yourself:```
lspci -nn
```On my system, it yields:As you can see, 0200 is also helpful!!

We all learn something new every day, don't we?

yes we do and thanks I have 0200 for me a sweet egrep for this would be great for the fourms some thing like ```
lspci -nn | egrep 0200\|/0280 
```
I could be wrong though I do not have a 0280 does it work on yours ?

---

