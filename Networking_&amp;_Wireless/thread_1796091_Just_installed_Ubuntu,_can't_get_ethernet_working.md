---
title: "Just installed Ubuntu, can't get ethernet working"
date: 2011-07-03
forum: Networking &amp; Wireless
---

### Post by wannagotopopeyes on 2011-07-03
Hi all, having some trouble getting connected to the internet. I have no wireless card, just plugging in the ethernet cord, but it won't connect/detect any settings. I thought it was just supposed to "work" but I seem to be having some issues. I'm a real linux newbie so hopefully this is an easy fix for some of you! Thanks for the help

---

### Post by wannagotopopeyes on 2011-07-03
Also, I ran the lspci command and see nothing on the output about any ethernet/network things... I'm guessing thats not supposed to happen? :(

---

### Post by chili555 on 2011-07-03
> lspci command and see nothing on the output about any ethernet/network thingsI'll bet it's hiding. Please run and post:```
lspci -nn | grep 0200
```Thanks.

---

