---
title: "DNS issue on one machine"
date: 2013-02-15
forum: Networking &amp; Wireless
---

### Post by monkeypigs on 2013-02-15
Hi, 

Got two machines, 1 running 13.04 (Which is fine, no issues) and one running 12.10. 

The 12.10 machine has developed (today) a weird DNS issue where it won't resolve to any of the sites on our shared hosting provider. All other sites work fine. 

I can ping the sites fine on this machine, and using a different browser/user makes no effect and there is nothing unusual in /etc/hosts.
I've tried switching to OpenDNS (to prove it's not an ISP blip) I've changed the IP and moved the cable into the next port on the hub in a desperate attempt to figure this out.

I know it's not an issue with our web host, as it resolves fine on the 13.04 machine (and on a virtual Windows machine running on the 12.10 with a bridged network adaptor) so I'm convinced it's 12.10 at fault.

However, having said that, booting a live 12.10 image exhibits exactly the same issue!

Truly stumped now as the live image was my last attempt to try and find in network-manager or dnsmasq was at fault!

Any help or pointers gratefully recieved!

---

### Post by linuxtechguy on 2013-02-15
Try the dig command on a host. What output are you getting.

---

### Post by monkeypigs on 2013-02-16
I get the expected output (attached)

It's odd that I can ping the site, dig's OK, but ssh and wget both fail.

Can network-manager really be that screwed?

---

### Post by SeijiSensei on 2013-02-16
> **monkeypigs said:**
> It's odd that I can ping the site, dig's OK, but ssh and wget both fail.

Can you reach the IP address the query returns with SSH, but not reach it with its hostname?

---

### Post by monkeypigs on 2013-02-16
No, it can't be reached by the IP address either I'm afraid.

---

### Post by SeijiSensei on 2013-02-17
Then it's pretty clearly not a DNS issue. It sounds more like the SSH server isn't running on the remote machine or there's some kind of firewalling rule in place.  Yet, if I understand your first post correctly, there are other machines you can use that connect correctly?  I'm trying to narrow down the problem here now that we know DNS is not at fault.

So can you connect to the remote server SSH from some machines but not others?  On the machines that do connect, can you use the remote's hostname as well as its IP address? 

If you can connect with one machine, watch /var/log/syslog on the remote while the other machine tries to connect?  Do you see the attempt fail, or do you not see the attempted connection at all?

---

