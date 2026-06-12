---
title: "Question regarding DNS / resolv.conf / vpnc"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by eyemou on 2009-04-18
Question re: DNS / [FONT="Courier New"]resolv.conf[/FONT]

Hi,

After installing vpnc, I noticed that web browing, etc. was slow. It turns out that it was a DNS issue, and that the DNS servers for my workplace had superceded my home/ISP DNS in [FONT="Courier New"]/etc/resolv.conf[/FONT] (i.e., they appear first).

I've tried adding the line:
[FONT="Courier New"]
prepend domain-name-servers my.isp's.dns.ip;[/FONT]

to [FONT="Courier New"]/etc/dhcp3/dhclient.conf[/FONT].

But still, no luck on reboot: [FONT="Courier New"]/etc/resolv.conf[/FONT] gets overwritten, and my ISPs DNS is reverted to the bottom of the list, underneath my workplace's DNS servers. Nothing is pre-pended -- or if it is, the workplace DNS addresses are somehow being added to the top of the list, after the fact.

Also, I have listed only my ISPs DNS servers in [FONT="Courier New"]/etc/network/interfaces[/FONT].

Any help/insight appreciated.

Thanks!

BTW, this is on a Kubuntu Intrepid x64 system. In case KDE is handling network things differently. I only say this because when I first opened [FONT="Courier New"]/etc/network/interfaces[/FONT], there was no entry for [FONT="Courier New"]eth0[/FONT] -only loopback.

---

### Post by eyemou on 2009-04-20
Anyone?

---

