---
title: "VPN related question"
date: 2012-12-06
forum: Networking &amp; Wireless
---

### Post by arbabnazar on 2012-12-06
I have configured the pptp server on ubuntu 12.04 and these are the logs that I got when I connect to it through vpn client (win xp).
Dec  6 19:35:00 ubuntu pppd[1145]: Using interface ppp0
Dec  6 19:35:00 ubuntu pppd[1145]: Connect: ppp0 <--> /dev/pts/0
Dec  6 19:35:00 ubuntu pptpd[1144]: GRE: Bad checksum from pppd.
Dec  6 19:35:02 ubuntu pptpd[1144]: CTRL: Ignored a SET LINK INFO packet with real ACCMs!
Dec  6 19:35:02 ubuntu pppd[1145]: peer from calling number 10.10.10.254 authorized
Dec  6 19:35:02 ubuntu pppd[1145]: MPPE 128-bit stateless compression enabled
Dec  6 19:35:02 ubuntu kernel: [   98.375862] PPP MPPE Compression module registered
Dec  6 19:35:05 ubuntu pppd[1145]: found interface eth1 for proxy arp
Dec  6 19:35:05 ubuntu pppd[1145]: local  IP address 172.16.10.1
Dec  6 19:35:05 ubuntu pppd[1145]: remote IP address 172.16.10.234

I want to ask that it is succesfull connection or not?
I have doubt on two things?can somebody explain it. 
1)[COLOR="red"]GRE: Bad checksum from pppd.[/COLOR]
2)[COLOR="Red"]CTRL: Ignored a SET LINK INFO packet with real ACCMs![/COLOR]
thanks

---

### Post by SeijiSensei on 2012-12-06
Can you ping the remote's IP address, 172.16.10.234?  If so, you are connected; if not, well....

If there is a firewall running on the remote, it needs to allow GRE traffic.  I think you have to add an iptables rule to allow the GRE protocol.  Do a little google searching for "gre iptables".

---

### Post by arbabnazar on 2012-12-06
> **SeijiSensei said:**
> Can you ping the remote's IP address, 172.16.10.234?  If so, you are connected; if not, well....

If there is a firewall running on the remote, it needs to allow GRE traffic.  I think you have to add an iptables rule to allow the GRE protocol.  Do a little google searching for "gre iptables".

SeijiSensei thanks,

I disabled the firewall and also allow the gre traffic from my edge firewall (which is mikrotik), but still it is giving me the gre bad checksum error.

yes i can ping to my default gateway, in this case 172.16.10.1

---

### Post by SeijiSensei on 2012-12-06
I'm afraid I cannot help much more.  It's been years since I ran a server that supported PPTPD.  Nowadays I use [OpenVPN]("http://www.openvpn.net/") tunnels which are orders of magnitude more secure than PPTP.

If you enter the error text into Google you'll see other discussions.  Searching for "GRE: Bad checksum from pppd" brings up a number of entries.  That's always my first step in diagnosing problems.

The fact that you can ping the remote means the tunnel is working, regardless of the reported errors.

---

