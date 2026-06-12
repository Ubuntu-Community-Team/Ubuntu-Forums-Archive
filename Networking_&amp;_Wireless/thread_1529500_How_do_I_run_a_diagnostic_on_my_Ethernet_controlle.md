---
title: "How do I run a diagnostic on my Ethernet controller?"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by gregtheCdn on 2010-07-12
Hello,

I have been having trouble with my Ethernet (wired internet connection) on my Ubuntu 10.04.

It was working fine this morning, and now, there is nothing. The lights on the Ethernet controller don't even blink when the cable is plugged in. I have checked the cable and it works on all other computers. 

Logic dictates that this should be a hardware issue, but being new to Linux, I have no idea how to check to see if my Ethernet controller is working properly, so as to diagnose and fix the problem.

How do I run a diagnostic to determine if there is a hardware issue?

Cheers,

GtC

---

### Post by cj.surrusco on 2010-07-12
Show the output of this in a terminal.
```
lspci | grep Ethernet
```
That will show if Ubuntu recognizes the card.

---

### Post by gregtheCdn on 2010-07-12
> **cj.surrusco said:**
> Show the output of this in a terminal.
```
lspci | grep Ethernet
```
That will show if Ubuntu recognizes the card.

Heya,

When I type this into the terminal it gives me loads of information, but I can definitely see that it sees and recognizes the Ethernet controller. 

"02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)"

Is there any way to see what the specific controller is doing? or Why perhaps it has decided to stop working?

Thanks,

Gtc

---

