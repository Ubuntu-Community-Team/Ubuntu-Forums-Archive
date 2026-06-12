---
title: "Wireless adaptors"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by \billnewbie on 2009-01-22
On searching the net for adapters that work with Linux I found one that is purported to work "straight from the box" namely: TP-Link TL-WN620G 108M Wireless USB Adapter. I therefore bought one and plugged it in to my HP Pavilion Laptop sitting in easy linking distance from my wireless router. Nothing happened.I have Ubuntu 8.10 installed. I opened System/Preferences/Network Configuration but found no clues ther as to how to proceed. I've only been on line and using Linux since October 08 so am still very much a newbie but I'm learning fast thanks mainly due to incredibly helpful assistance from the community. Can anybody guide me now please?

---

### Post by steeleyuk on 2009-01-22
Can you open a terminal and type:

lspci

Generally, the chipset gives us more information than the make and model of the card itself. Some manufacturers, and this happens alot with webcams (but wireless cards can be a problem), is that they give the same model number to two cameras that might have completely different chipsets. It can often be the cause of one person reporting a webcam as working and another person saying it doesn't.

---

