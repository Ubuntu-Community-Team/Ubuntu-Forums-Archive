---
title: "Making a Router out of a Netbook"
date: 2013-08-29
forum: Networking &amp; Wireless
---

### Post by racush2 on 2013-08-29
Greetings,

I apologize in advance for asking a question which has probably been asked before - I had some difficulty finding exactly what I need using the search function and therefore decided to ask for guidance on the forums.
My envisioned set-up should look something like the following: ISP (modem) -> Netbook running Ubuntu Server 12.04 (via eth0) -> broadcast wifi via wlan0 -> all other users on the network access it through wireless. 
The netbook, as can be deduced from the above information - has one ethernet port and one wifi card (g standard); It'd be wonderful if someone could point me in the right direct, specifically - how to turn the netbook into a consumer router equivalent. (or something like that) 

Thanks in advance.

P.S - I will probably use a torrent client to download directly to the router; will that require special configuration in terms of which iface will be used for torrent traffic? (would prefer to leave some bandwidth on wlan0, it's quite slow as is)

---

### Post by Lars Noodén on 2013-08-29
I had something similar to that set up temporarily a while back.   I used multiple ethernet ports rather than wi-fi, but the use of iptables should be about the same.   From my notes, you'll need to do two things.  You'll need to allow packet fowarding *sysctl -w net.ipv4.conf.all.forwarding="1"* And you'll need to tell what to forward and where *iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE*

Maybe that is enough to help dig up proper documentation or guides and hopefully someone more experienced will add to or correct that.  There is also the question of what to do in the case of IPv6, but most ISP are still failing to support that.

---

### Post by GwL3eNC on 2013-08-29
Hello,

i think this is a ittle bit more work to do. First you must be shure that your wlan card support 
access point in master mode. If you have an atheros card you can use either madwifi or
the ath5k modul.

Additional you need the hostapd and the dnsmasq packages. The configuration not fast done 
and also not simple. If you understand a little german you can abstract all information out of
the given link or find an equivalent english side.

[http://wiki.ubuntuusers.de/WLAN_Router](http://wiki.ubuntuusers.de/WLAN_Router)

---

