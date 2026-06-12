---
title: "Network Bandwidth affected"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by sportfreak2020 on 2011-07-14
Hey ubuntu world ..

lately i have noticed this weird behavior in my office internet connection .. whenever i run the ubuntu OS updates, on any ubuntu computer, the whole internet connection does dead slow .. i mean we have a corporate T1 line, wherein at any given time the download/upload speed is 10/10 mbps .. but running a simple OS update ( during which the download speed is around 1.5 to 2.5mbps ) almost halts the entire traffic .. any reason why ???

its a simple office setup, with NETGEAR ProSafe VPN Firewall FVS336GV2
and basic portforwarding rules enabled .. thats it .. nothing fancy ...

any inputs would be greatly appreciated. .. thanks ..

---

### Post by jmoorse on 2011-07-15
A very cursory test on my uduntu machine with iptraf and bmon showed just an apt-get update using ingress 200-1000kbps, egress ~400kbps, this is with no packages being downloaded

Are you sure about your bandwidth?  Remember most sites like speedtest.net give you your speed in BITS, and application download speeds are generally given in BYTES.  This means that for each 1MBps download is 8mbps in ISP-speak.

I recommend updating during non-peak hours or policing your apt-get traffic, I am not sure what knobs Netgear offers for traffic engineering.

---

