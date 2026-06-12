---
title: "Anyone manage to get RealTek RTL8111 wireless working on 10.10?"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by TBABill on 2010-10-20
The Realtek RTL8111 wireless does not work in Mint 10 or Ubuntu 10.10. Works perfectly in Mint 9 and Ubuntu 10.04. No proprietary driver necessary. Has anyone managed to get it working in Ubuntu 10.10? 
 
Symptoms: right after install the system sees available networks no problem. You can click the one you want to connect to and enter your security key. I just use WEP because it's easy. I enter the key and the system just tries to connect until it times out. You can repeat this process indefinitely. Wired works fine but after any available updates are installed, still no wireless capability. The computer is 15 feet from th
I have searched the Ubuntu forums and the Mint forums but have come up empty. Google hasn't helped much either. There have been suggestions, but no solutions posted as [SOLVED].
 
Any help is appreciated if you have seen this particular device working with either Ubuntu 10.10 or Mint 10.
 
Thanks!

---

### Post by dtkr on 2010-10-20
> **TBABill said:**
> The Realtek RTL8111 wireless does not work in Mint 10 or Ubuntu 10.10. Works perfectly in Mint 9 and Ubuntu 10.04. No proprietary driver necessary. Has anyone managed to get it working in Ubuntu 10.10? 
 
Symptoms: right after install the system sees available networks no problem. You can click the one you want to connect to and enter your security key. I just use WEP because it's easy. I enter the key and the system just tries to connect until it times out. You can repeat this process indefinitely. Wired works fine but after any available updates are installed, still no wireless capability. The computer is 15 feet from th
I have searched the Ubuntu forums and the Mint forums but have come up empty. Google hasn't helped much either. There have been suggestions, but no solutions posted as [SOLVED].
 
Any help is appreciated if you have seen this particular device working with either Ubuntu 10.10 or Mint 10.
 
Thanks!

Have you tried lspci in the Terminal? Send the output here.

---

### Post by TBABill on 2010-10-20
Yes I have. That's where I got the model number RTL8111. The system sees the card, sees my networks (mine and my neighbor's), but will not connect. This is affecting cards of all types in the exact same way so I was hoping someone has found the fix. It will just try to connect indefinitely in Ubuntu 10.10 and in Mint 10, which is based on 10.10. The behavior is identical in both, but in Ubuntu 10.04 or Mint 9 (or any other distro and version). It's not the card driver that is at fault since my card is affected along with Intel cards and others.

---

### Post by TBABill on 2010-10-21
Anyone?

---

