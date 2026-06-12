---
title: "Openvpn NAT in Ubuntu x64 9.10 Karmic on XEN Vps not working"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by Dando Real on 2010-02-10
Hi,
this is a report, not a question, because with the same settings everything works in Debian 5.0 Lenny 64 bit

The fact:
I have a XEN Vps with Ubuntu 9.10 Karmic x64.
Via apt-get I installed openvpn and iptables.
I set ipv4 forwarding to 1, and the Masquerade
My openvpn conf is so that the default gateway becomes the vpn, so all trafic would be redirected via the tun and then natted.
however, even if packets go through the vpn, leave the server, there is no reply.
I tried with a simple ping, and what I see with tcpdump is that the masquerade works, but there is no reply at server level; then the server sends an ARP request and receive as answer fe:ff:ff:ff:ff:ff, and there is still no reply to ping.
I did this tests after a fresh install, so there is nothing I could have messed up. And, the problem happened with two different hoster (one in US and another in  Italy).

I don't know if it is ubuntu or openvpn: in debian, where I did the exact same passages and works, openvpn is a little order, version rc11, and the init.d script is 3kB lesser.

I hope someone can check this

---

