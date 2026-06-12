---
title: "VPN ridiculously slow"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by 98174 on 2011-07-26
I am currently connecting to a US university VPN during my stay in a foreign country.

After a lot of manual tweaking (creating my own connection in /etc/ppp/peers and modifying ip routes), I finally managed to make it work.

However, it is ridiculously slow.  

If I connect via my normal internet connection (actually PPPoE, sits on ppp0), I get about 250 kB/s.
Via the VPN (on ppp1), I get about 2 kB/s.
On the VPN on Windows, I get about 50 kB/s.

Why this discrepancy?
Ironically, pings to my VPN server through my VPN take longer than pings going through my normal internet connection.

I can provide info from netstat or route or my VPN config if requested.

---

### Post by 98174 on 2011-07-26
Just tested out tracepath with/without VPN.

On VPN, each hop is taking about 250 ms, and there are 12 hops.
Without VPN, each hop is taking about 6 ms, and there are 6 hops.

...?

---

### Post by 98174 on 2011-07-27
Bump.

---

