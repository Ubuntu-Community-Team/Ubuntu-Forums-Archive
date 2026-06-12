---
title: "IPV6 and OpenDNS stopped working."
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by Sinsemila on 2009-10-08
Since Ubuntu 9.04 came out and you couldn't disable IPV6 anymore I started using Opendns and it solved the issue on my 2 Ubuntu pc's. For the last week I have been suffering from really slow page loading ( sits there for 10-15 seconds before the page evan starts to load). Disabling IPV6 fixes Firefox but I use Opera as my main browser.
My Windows pc's still fly along and I have Mandriva dual booted on one and it flies after disabling IPV6.
Has there been an update about a week ago that could have caused this as its been fine all year, or is it possible OpenDns has changed something to cause this?
I'm not happy Ubuntu have decided to make it so difficult to disable IPV6 since 9.04 and I'm guessing 9.10 is still the same. In Mandriva you don't evan have to use the terminal to disable IPV6, just click a check box and its gone.

---

### Post by kreggz on 2009-10-10
Pretty sure you can disable it

1.  sudo nano /etc/modprobe.d/blacklist
2. at the bottom of the file put in  blacklist ipv6

---

