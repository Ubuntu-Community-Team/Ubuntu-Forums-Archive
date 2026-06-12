---
title: "Some web pages won't connect"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by FernandoLB on 2009-08-06
I'm using 9.04. Suddently some web pages like, groups.yahoo.com, ubuntuforums.org, scrib.com and some others just won't connect. Any other pages load fine.

I tryied with Firefox, Opera, Epyphany. Disbled Fsash, JavaScript and all plugins but it didn't help.

I tryied with Links and Dillo and I the mentioned pages got loaded.

I'm posting from an Arch Linux using Opera, in the the pc/hardware and I'm using the same network settings, including the DNS servers. It is working here.

What could be the problem?

---

### Post by snek on 2009-08-06
I've actually had the same problem before with the domain isohunt.com
It worked fine on my other 3 machines at home but my Ubuntu machine just seemed to timeout. I've asked for a solution to this many times, but never got a reply.

Restarting the machine usually helped though, but it's not really a solution to the problem.

---

### Post by FernandoLB on 2009-08-06
> **snek said:**
> 
Restarting the machine usually helped though, but it's not really a solution to the problem.

Well, unfortunately, in my case even restarting doesn't change anything...

---

### Post by superprash2003 on 2009-08-06
try the following
1)disable ipv6 - [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)
2)chansge MTU - [http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html](http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html)

---

### Post by FernandoLB on 2009-08-06
lsmod | grep inet6 does not return anything, so I think I don't have ipv6 enable.

Changing the MTU did not chage the behavior in those web pages.

That is driving me crazy. In Archlinux I don't have any MTU setting. I don't know what to make of this situation. 

Any more ideas are welcome.

Edit: I disabled Network Manager and configured it through /etc/network/interfaces and so far (5 minutes) it seems ok.

Edit: It seems that the problem really was with Network Manager. I don't have any MTUs configuration in /etc/network/interfaces and I didn't have that problem anymore.

---

### Post by cayfer on 2009-08-11
I had the same problem for a long while. Disabling IPV6 DNS as suggested in a lot of places didn't work for me. Finally I closed all Firefox windows; renamed ~/.mozilla/firefox and the problem was gone when I restarted Firefox.

---

