---
title: "no ping and no nfs mount over pptp vpn tunnel"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by Schneemann on 2009-02-26
Hello 

I am connecting from my Ubuntu 8.04 to a pptp server running on a firewall without any problems over the internet. But once the connection is established I cannot ping any of the ip-addresses within my remote LAN, nor mount one of the nfs shares.
If I do the same using Windows Vista, using the built-in pptp client of ms vista, everything works, ping and mounting, so I assume there is no problem with the remote firewall (remote gateway and pptp server).
From within my LAN mounting and pinging under Ubuntu 8.04 are working without any problems.

What am I doing wrong?

Thanks well in advance,
Christian

---

### Post by Schneemann on 2009-02-28
Dear all, I could solve the problem. It wasn't a pptp-issue, but a firewall issue - there were some protocols blocked.

Best regards, Christian

---

