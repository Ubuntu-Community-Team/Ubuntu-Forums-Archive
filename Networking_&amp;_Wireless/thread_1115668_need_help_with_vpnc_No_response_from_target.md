---
title: "need help with vpnc: No response from target"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by sirpelidor on 2009-04-04
Hi, just got Hardy Heron fresh installed on my laptop, and was trying to setup a cisco vpn client to access my office's network.  Following [ this guide]("http://www.spiration.co.uk/post/1293/ubuntu linux VPN connection without cisco vpn client"), I was able to setup vpnc with vpnc.conf file based on my pcf from cisco.

However, when issue: sudo vpnc /etc/vpnc/vpnc.conf    
i got: vpnc: No response from target

but then others user were able to get by with additional natt-mode option:
--natt-mode cisco-udp

I still got No response from target...

when dig around a bit more, a [post]("http://linos.wordpress.com/2007/11/23/vpnc-instead-of-ciscos-vpnclient-authtype5/") suggested i'll need to enable openSSL.

when I recompiled vpnc, run it again...no luck.

if I put additional option: IKE Authmode hybrid
it'll complain that certificate is missing, yet I can't find any certificate from my window box.

someone even [claimed]("http://ubuntuforums.org/showthread.php?t=537670") that they can get it to work by downgrading to vpnc 3.3.   I tried, but this time gets worst... vpnc doesn't even bother to give me any response ...

so now I roll back to latest vpnc, try to run in debug mode:

[PHP]
vpnc version 0.5.1

S1 init_sockaddr
 [2009-04-04 01:54:11]

S2 make_socket
 [2009-04-04 01:54:11]

S3 setup_tunnel
 [2009-04-04 01:54:11]
   using interface tap0

S4 do_phase1
 [2009-04-04 01:54:11]

S4.1 create_nonce
 [2009-04-04 01:54:11]

S4.2 dh setup
 [2009-04-04 01:54:11]

S4.3 AM packet_1
 [2009-04-04 01:54:11]
vpnc: no response from target
[/PHP]

p.s:  the above debug msg is same whether i turn on natt-mode or not...

any thoughts on this?

thank you very much.

---

