---
title: "DNS troubles while downloading big files"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by gkweb on 2009-01-21
Hello,

Context : LAN with 3 Computers behind a Linksys router.

I have installed Ubuntu 8.10 64bits after having given up on OpenSUSE 11.1 (KDE) 64bits. Everything work much better, not necessarily thanks to the distro, but simply may be thanks to the GNOME interface (KDE 4 seemed very buggy on my system and was crashing sometimes).

However I have a problem that I thought to fix by installing Ubuntu, but which is still existing.

While doing classical downloads with Firefox, DNS lookups to visit other websites completely fail (~98% lost). Consequently, no websites successfully load.
As soon as I stop the downloads, all of the websites stuck on the DNS lookup instantly appear.

Under Windows, my downloads peak to 128KB/s which is my upper limit (1Mbps ADSL connection), and the 2 other computers on the LAN can access any websites, as well as my computer (even if slower, connectivity is never cut).

However under Linux I see Firefox displaying sometimes download peaks around 150-160KB/s (real values or error while calculating bandwidth ?), and I cannot access any website, DNS lookups failing after a timeout. The worse is that the 2 other computers on the same LAN are also cut from the Internet.

If Linux is so much powerful and fast that it obliges me to revert back to Windows, isn't that a kind of black humour ? :-)
As an alternative, for an isolated file I can use the following command :
wget --limit-rate 120 UrlDDownload

I have noticed that when using OpenDNS DNS servers instead of my router IP address (and thus my ISP DNS servers), DNS lookups "seemed" to complete a little more often, but I won't swear it.

Is the problem known ? Is there a solution ?

Thanks in advance.
Regards,
Guillaume.

---

### Post by gkweb on 2009-01-22
*up*

---

### Post by gkweb on 2009-01-24
Hello,

I found a fix to my DNS lookups failing on my whole LAN when I was downloading

First I disabled IPV6, which did not solve the problem, but is still a good thing to do as I do not use it :

sudo vi /etc/modprobe.d/blacklist
# Disable IPV6 on all interfaces
blacklist ipv6

Then I modified TCP Window Scaling to the values it was defined in kernels prior to 2.6.17 :
sudo sysctl -w net.ipv4.tcp_rmem="4096 87380 174760"

As it worked, I applied it permanently to the system :
sudo vi /etc/sysctl.conf
net.ipv4.tcp_rmem=4096 87380 174760

In case it could help someone else... ;)

Regards,
gkweb.

---

