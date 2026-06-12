---
title: "How do I prevent people from connecting to LAN with routers ?"
date: 2011-03-16
forum: Networking &amp; Wireless
---

### Post by FiFE on 2011-03-16
Hi,

There are a lot of users in my LAN and I have to use DHCP. The problem is that some of them are connecting their routers (usually wireless) to the LAN in the incorrect port and as a result that router issues IP addresses. 
Is there a solution to this problem ?

---

### Post by SeijiSensei on 2011-03-16
I don't think there's much you can do other than establishing a "no-routers" policy and enforcing it by denying service to people who violate the policy.  If you can't set a network policy and enforce it on endusers, you'll never be able to resolve this issue.  There's no technical fix at the dhcpd end other than banning discovered routers by MAC address, but that quickly becomes a game of "[Whac-a-Mole]("http://en.wikipedia.org/wiki/Whac-A-Mole")."

---

### Post by FiFE on 2011-04-07
Thank you for the reply. 
A solution that someone mentioned was the manipulation of the TTL. Is that viable ?

---

