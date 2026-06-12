---
title: "DNS problem?"
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by dakaling on 2006-07-14
Let me start off at saying that I'm a complete n00b to linux. That being said, I just installed Ubuntu 6.06 on my laptop and after a little tinkering I got my wireless card (Linksys WPC54GS) to work at home.

I brought my laptop to work (a hotel) where we have wireless access, and suprise it didn't work. There is no encryption, its a completely open network. I was able to ping just fine, but when I would type an address into the browser nothing would work. After tinkering with it I found out I if I used a numerical adrress (ex. 64.233.179.99 for google) it would work. The windoze machine in the lobby is working fine though.

Anyone have any ideas as to what may be the problem?

---

### Post by CasperGasper on 2006-07-14
Yep, you're right that is almost certainly a DNS problem.  I take it your default gateway is your wireless AP?  Just make your DNS server the same as that, and it should be fine.

 Goto System/Administration/Networking, type in your password and find the DNS tab.  


Casper.

---

### Post by bigken on 2006-07-14
I had a similar problem with a safecom router and got round it by typing about:config in the firefox browser and changing network.dns.disablepv6
from fales to true ;)

---

### Post by GuitarHero on 2006-07-15
its not just firefox

---

### Post by VoodooSmurf on 2006-07-15
I had the same problem u did.  I work at a hotel as well and I called tech support and they didn't have global DNS installed.  They installed it and it works now...  give that a try.  I was able to ping we sites, even visit using the IPs, just couldn't get any name resolution.  works fine now.

---

