---
title: "Dialup isp's??"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by darknoobie on 2010-01-13
Im new to ubuntu and I have been playing around with server edition. Im trying to learn all i can bout networks. So far ive learned how to use bind9, apache2, openssh,quota,iptables, and many other've been looking at ppp which is dial up correct? Ive also learned how to share my internet connection with other computers in my network. What im really asking is is there a way others can dial into ubuntu server and share my internet connection with them. I have broadband connection to the internet and id like for other users to dial into my pc and use my internet.

---

### Post by darknoobie on 2010-01-13
No ones responded to this post. I posted it on many forums. no one seems to know how it works.

---

### Post by adam814 on 2010-01-13
I've never done it, so I'm mostly just taking a stab in the dark here.  I'd think any modem Ubuntu recognized would just appear as another interface.  You'd have to do IP Masquerading just like you would using the machine for an ethernet router.  As for the actual dialup authentication I think RADIUS will do that for you.

---

### Post by darknoobie on 2010-01-13
Ty so much for replying.

---

### Post by cascade9 on 2010-01-13
> **darknoobie said:**
> What im really asking is is there a way others can dial into ubuntu server and share my internet connection with them. I have broadband connection to the internet and id like for other users to dial into my pc and use my internet.

You want to use your 56K modem to share your internet? Dont bother. 

Its a security risk....and 56K uploads at 2-3K/sec, maximum. Its bad enough using 56K for your own use, at 5-6K/sec download (typical speed). IT would be super painful at 2-3K/sec download speeds.

---

