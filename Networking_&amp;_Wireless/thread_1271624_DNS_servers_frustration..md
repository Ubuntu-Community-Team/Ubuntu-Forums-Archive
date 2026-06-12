---
title: "DNS servers frustration."
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by arpoodle on 2009-09-21
I've googled this estensively, and haven't found a solution to my problem, and I've RTFM but the settings I've applied seem to have no effect, and so here I am.

Using Ubuntu 9.04
Linux 2.6.28-15-generic
64bit system.

A couple of weeks ago, I installed Bind locally, for some testing I was doing at home.  Prior to that my laptop's networking was working fine.  It was picking up DNS settings fron the DHCP server over the wired connection on eth0 at work no problem, equally, it was picking up the DNS settings from my wireless router at home no problem either.

I instaled Bind on the Friday while at home, did what I needed do do, and removed bind on Sudnay night.

When I came into work on Monday morning, nothing was resolving, and I found that resolv.conf was showing...
[FONT=Courier New]
nameserver 127.0.0.1
domain co.[workdomain][/FONT]

I ensured that bind had been removed completely, restarted NetworkManager and nothing changed.  I was getting assigned an IP address by the DHCP server, but DNS was still defaulting to 127.0.0.1

A bit of googling suggested modifying the /etc/dhclient3/dhclient.conf file, adding the following line:
[FONT=Courier New]prepend domain-name-servers 10.[dns], 10.[DNS];[/FONT]

After doing this, and restarting NetworkManager again, it still defaulted to the DNS to 127.0.0.1 within resolv.conf.

Now, even at home, the same things happen, and I need to manually edit resolv.conf after login, at least for the duration of the network connection. 

What,where and why are these settings being applied?  Why does my laptop insist on wanting to use a local DNS?

Due to the way the network at work  operates, I can't use a local DNS server, so re-installing Bind would only work at home.

In a nutshell, it seems that removing Bind doesn't remove something somewhere that controls the local DNS settings.

Any ideas anyone?

tia
a

---

