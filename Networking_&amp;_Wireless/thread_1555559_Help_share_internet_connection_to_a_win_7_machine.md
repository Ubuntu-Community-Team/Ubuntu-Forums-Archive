---
title: "Help share internet connection to a win 7 machine"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by damnated on 2010-08-18
I want to share my internet connection with my netbook which has a Win 7 starter OS. 

This is what I did: in Network Connections I set the IPv4 Setting of my network card to shared with other computers, plugged in the network cable into both machines, and now they both see a connection.
But. Win 7 only sees the connection as *Unidentified network* with "No internet access". What should I do?

---

### Post by Iowan on 2010-08-18
My machines (10/100 NIC's) would require a crossover cable. 
Have you seen [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page?  It'll need some tweaking to work with wireless...

---

### Post by dmizer on 2010-08-19
> **damnated said:**
> Win 7 only sees the connection as *Unidentified network* with "No internet access". What should I do?

This is a configuration problem with Windows, not Ubuntu. I really had a hard time getting Win7 to get past that UAC regulated "Unidentified Network". There are many possible solutions for this, so I highly suggest you start with a google search like this:

Win7 "Unidentified network"

Let us know when you find the solution!

---

### Post by damnated on 2010-08-19
> **Iowan said:**
>  
Have you seen [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page? 

I did, I even configured the Win 7 similarly to that (default gateway, static IP, DNS address etc.). After that I entered the MAC address of my card as the network address at win 7, nothing changed however. 
I'm getting a feeling it can't be done, seeing how many people have had troubles with this. (googled win 7 unidentified network :lolflag:).
I'll keep searching though, maybe something comes up.

---

