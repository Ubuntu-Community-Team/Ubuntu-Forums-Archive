---
title: "Not sure if xltpd is running l2tp over ipsec openswan vpn configuration issues"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by dbqgeek on 2009-11-06
I've been working on setting up a vpn using openswan (or strongswan) fro the past week now.  I've been running the windows server vpn solution for years, so I'm pretty sure it's not router.

I'm trying to implement my solution behind a firewall and more likely than not clients will also be behind a firewall trying to connect.

I've tried two solutions ([openswan]("http://rootmanager.com/ubuntu-ipsec-l2tp-windows-domain-auth/setting-up-openswan-xl2tpd-with-native-windows-clients.html") and [strongswan]("http://nielspeen.com/blog/2009/04/linux-l2tpipsec-with-iphone-and-mac-osx-clients/"))

I can seemingly get the ipsec to establish over NAT-T with openswan, but it stops at that point and is't almost like xl2tpd isn't even running.

With the strongswan configuration I can't get ipsec to work outside my network, but when in my network i can get the whole thing to work.

So my main question is, has anyone setup an openswan vpn with xl2tpd and the auth.log file stopped at this message

"L2TP-PSK-NAT"[2] xxx.xxx.xxx.xxx #2: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x0197c0dd <0xcf147379 xfrm=AES_128-HMAC_SHA1 NATOA=none NATD=xxx.xxx.xxx.xxx:4500 DPD=none}

Thanks,

Kristofer

---

### Post by Jhongy on 2010-04-14
Exactly the same problem here. IPSec tunnel is created OK, but xl2tpd never seems to do anything -- no logs, nothing to show it is even alive.

Did you manage to solve the problem?

---

### Post by rjmx on 2010-11-14
Don't know if either of you solved the problem, but for the benefit of anyone else reading this:

I had exactly the same problem. IPsec tunnel seemed to be set up ok, but xl2tpd didn't seem to react in any way to a connection attempt. This turned out to be caused by my firewall blocking UDP port 1701 (the l2tp listening port). After I enabled that, the VPN tunnel worked like a charm.

Note that I used strongswan, but I'm sure openswan would be similar. The firewall settings I needed to allow, overall, were
- Protocol 50 (ESP)
- Ports 500/udp, 4500/udp and 1701/udp

If you're using the Shorewall firewall, it has macros for these (IPsecnat and L2TP).

 .....Ron

---

### Post by wlraider70 on 2011-05-30
I'm getting the same log message.

I have all three ports forwarded and the vpn pass-through checked (allowed (i think that will take care of prot 50)

However, I don't see any difference.

---

### Post by ndoggac on 2011-06-08
Does my guide for openswan help at all?

[http://ubuntuforums.org/showthread.php?t=1645473&highlight=openswan+iphone](http://ubuntuforums.org/showthread.php?t=1645473&highlight=openswan+iphone)

---

### Post by yang on 2013-02-06
I had the same problem and this solved it for me (problem with the Windows client):

[https://lists.openswan.org/pipermail/users/2011-July/020774.html](https://lists.openswan.org/pipermail/users/2011-July/020774.html)

---

