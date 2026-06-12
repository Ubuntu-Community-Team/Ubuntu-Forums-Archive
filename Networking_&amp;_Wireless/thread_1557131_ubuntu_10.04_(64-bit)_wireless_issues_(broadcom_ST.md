---
title: "ubuntu 10.04 (64-bit) wireless issues (broadcom STA driver)"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by bbb125 on 2010-08-20
hi all,

I'm having a problem with getting my wireless connection to work on my Dell Studio 1537 laptop with Ubuntu 10.04 (**64-bit**). I have installed the Broadcom STA driver under System > Administration > Hardware Drivers. My wireless network is detected, and I can connect to it. However, even though it says I'm connected, I can't go to any websites or access anything. I don't think it is a DNS problem, because I can't even ping an IP address (such as yahoo) or even the router itself. It will say "Network is unreachable".
[B]
Note: I do not have this problem when I boot from the LiveCD for the 32-bit version.[/B]


A couple things I noticed:
TX packets:18 **errors:21** dropped:0 overruns:0 carrier:0
Not sure what this means exactly, but I'm guessings errors aren't a good thing.

And also, iwconfig says:
**Encryption key:off**

I have set the encryption key using the Wireless Security tab when I set up the network. Anyone have any ideas? Could this be a problem specific to the 64-bit driver? Again, I don't have this problem when I boot from the 32-bit LiveCD.

Thanks!

---

### Post by bkratz on 2010-08-20
This is actually probably the problem (or at least one!)

[COLOR="Red"]Mode:Ad-Hoc[/COLOR] Frequency:2.412 GHz Cell: 8A:2E:34:40:20:21

I have to google a little to find how to fix, but it should be easy--back soon.

---

### Post by bkratz on 2010-08-20
Ad-hoc is used between computers, try

sudo iwconfig eth1 mode Managed

then redo your tests.  By the way the sudo will require your password which will not be echoed (not even ***) just hit enter when done.

---

### Post by bbb125 on 2010-08-20
> **bkratz said:**
> Ad-hoc is used between computers, try

sudo iwconfig eth1 mode Managed

then redo your tests.  By the way the sudo will require your password which will not be echoed (not even ***) just hit enter when done.

Looks like that was the problem. It's working now. Thanks a ton!

---

### Post by bkratz on 2010-08-20
> **bbb125 said:**
> Looks like that was the problem. It's working now. Thanks a ton!

Glad I could help and thanks for marking it solved!

---

