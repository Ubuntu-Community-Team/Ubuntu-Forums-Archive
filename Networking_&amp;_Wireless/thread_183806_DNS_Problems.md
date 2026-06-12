---
title: "DNS Problems?"
date: 2006-05-28
forum: Networking &amp; Wireless
---

### Post by werthog on 2006-05-28
I have an old Apple Airport that connects to the internet by dialup. It works fine for the Windows and Apple laptops in my house, but my IBM Thinkpad T40 running Ubuntu is having some problems. 

It doesn't seem to be a driver issue; Ubuntu recognizes both my ethernet card and the built-in wireless, thanks to the MadWifi drivers. I can connect to the Airport by wireless AND with a crossover Ethernet cable. Both connections have the same problem. They can connect to the network easily enough, and I can ping outside IP addresses on both connections. However, I can't ping any domain names, and Firefox doesn't load either.

I've been through the troubleshooting guides for wifi and ethernet, and both have stated that this is indicates that DNS servers aren't set up. However, my computer seems to have the right settings; both the Network GUI settings and the /etc/resolv.conf show the same IP address for the DNS server as the other computers on my network do. Is there any other possible reason for these problems?

Just ask if you need any more information. Thanks for any help you can give!

EDIT: Just discovered that the wireless connection isn't quite as far along as the ethernet; pinging a valid IP address returns "Destination Host Unreachable." Any help with either issue is appreciated.

---

### Post by linuchsan on 2006-05-28
Have you checked the gateway?

---

### Post by werthog on 2006-05-28
[QUOTE=linuchsan]Have you checked the gateway?[/QUOTE]

Yes, the gateway is correct as well.
I just did some tooling around and found that I was wrong about one thing in the previous post; the ethernet connection has the problem I described above, but when I try to ping a valid IP address with the wireless connection, it returns "Destination Host Unreachable." (I'm editing the post to reflect that). As long as I get the ethernet working, I don't need the wireless card; I'd just like to be able to get online SOMEHOW ](*,)

---

