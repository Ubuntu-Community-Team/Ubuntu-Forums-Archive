---
title: "File transfers lock up the OS"
date: 2012-04-08
forum: Networking &amp; Wireless
---

### Post by TechSupportx86 on 2012-04-08
I'm not sure if this goes here, or in the server section, but i think it's network related so here we go.

I am having trouble transferring files to my server. It is running ubuntu server 11.10 x86. I am using 2 onboard gigabit ethernet ports (my whole network is gigabit), and i am using a 3ware 9500s x-8m raid card with 6 drives all set as single drives.

I have tried transferring over SMB from my PC and using WGET to download a 5G file off of my local web server. Both times it locks up around 18% and it is a total lock-up, CTRL-D/C does nothing.

Rest of the specs (everything i know ATM)
2x AMD Opteron 250 Processors @2.4Ghx
4GB ECC (ECC is currently disabled)
3ware 9500 x-8m raid card (6 drives total)
I do not know what motherboard it is other than it's a TYAN

I am sitting here with an SSH connection, and the thing is about 15 feet from me. If you need more information, feel free to ask. Thanks

---

### Post by TechSupportx86 on 2012-04-12
Fixed it myself... For anyone having a similar issue in the future:

Check the specs on the RAID card. Apparently my card _***ONLY***_ supports SATA 1 Drives. So it would bottleneck at the card and lock up the entire system. Switching the jumper on the back of each drive to SATA 1 fixed my problem.

---

