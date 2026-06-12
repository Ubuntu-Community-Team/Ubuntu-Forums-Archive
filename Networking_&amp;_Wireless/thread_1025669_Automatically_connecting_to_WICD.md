---
title: "Automatically connecting to WICD"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by jozmoz on 2008-12-30
Hi,
I can't get WICD to automatically connect to my wireless, even though I have ticked 'automatically connect to this connection'. Everytime I start my laptop up i'm having to go into WICD and manually connect my wireless, otherwise it just won't connect.

any ideas? thanks very much.

---

### Post by CAPLinux on 2008-12-30
Jozmoz,

I had the same issues with WICD after I upgraded to 8.10.  For the longest time I had never had any luck using the network-manager tool, but I am happy to say that with 8.10 whatever was broke on Network Manager is now fixed.  I have a WPA-secured wireless network at home that Network manager now connects to automaticly.  

BTW, I am using a Broadcom 4318 wireless card, so I have to use NDSWrapper, and the new Network Manager works great.  Give it a try.

---

