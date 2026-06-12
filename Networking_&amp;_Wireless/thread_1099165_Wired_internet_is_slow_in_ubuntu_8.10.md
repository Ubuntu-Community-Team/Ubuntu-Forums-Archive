---
title: "Wired internet is slow in ubuntu 8.10"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by friendsforravi on 2009-03-17
Hi,

Recently I have installed ubuntu 8.10 in my desktop system.

I have TATA-INDICOM WIMAX 256Kbps internet connection with static IP.

I have problem in browising. Its very slow when compared with my browising in windows xp.

but downloading is very good.(30-35 KB/s)

I found no problems in ubuntu 8.04 64 bit.

It have turned of the ipv6 for firefox also, but i found no improvement.

Please help me!!!!!!!!!

---

### Post by Beefeater on 2009-03-18
> **friendsforravi said:**
> Hi,

Recently I have installed ubuntu 8.10 in my desktop system.

I have TATA-INDICOM WIMAX 256Kbps internet connection with static IP.

I have problem in browising. Its very slow when compared with my browising in windows xp.

but downloading is very good.(30-35 KB/s)

I found no problems in ubuntu 8.04 64 bit.

It have turned of the ipv6 for firefox also, but i found no improvement.

Please help me!!!!!!!!!

Sounds like a DNS problem to me. Try to add your DNS servers to /etc/resolv.conf

nameserver IP
nameserver IP
...

If that's not working, try to install wireshark and see what's up.
Hope it helps.

---

