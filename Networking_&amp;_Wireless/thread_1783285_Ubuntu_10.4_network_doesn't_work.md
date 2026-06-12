---
title: "Ubuntu 10.4 network doesn't work"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by Floepsa on 2011-06-15
Hey guys,

i'm kinda new with ubuntu and now i've installed it on my parents old computer, mostly for downloading. But wired internet did work all the time but then i had to reset our router because of some problems and now it doesn't work anymore!

But the strange thing is, if i put the cable on my own laptop with windows on it, then it works as normal.

So i guess its some kind of DNS problem, but i'm very new with ubuntu and also not so good with computers. Our network is simple just an modem connected to an router: Sitecome WL-341. If just anyone could help me, that would be great!


(PS Sorry for my bad english :roll:)

---

### Post by Floepsa on 2011-06-16
Anyone? Im pretty desperate...

---

### Post by Floepsa on 2011-06-21
Can no one help me?

---

### Post by Iowan on 2011-06-21
In a terminal (Applications>Accessories>Terminal), check **ifconfig -a** to see if the machine gets an IP address (post results). 
If it has an address, **route -n** will provide routing information.

---

### Post by Floepsa on 2011-06-21
I already fixed the problem, it seems that i just had to edit the connection into manual and put my router information in there.

---

