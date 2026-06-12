---
title: "localhost virtual server ignored unless I edit /etc/hosts.  what's wrong?"
date: 2009-08-08
forum: Networking &amp; Wireless
---

### Post by quixote on 2009-08-08
I need to test a couple of websites locally, but only sometimes.  The rest of the time I want to access them normally out on the web.  I use a2ensite and a2dissite to enable and disable.  But unless I also manually add a line in /etc/hosts, apache keeps serving the non-local version.  That doesn't seem right.  Here are the details:

I've made an entry in /etc/apache2/sites-available/molvray.com.  I've made a link to it in /etc/apache2/sites-enabled.  I've used **sudo a2ensite molvray.com** to enable it.  I then reload apache2.  When I go to the url in the browser, it gives me the web version, not the local version.

When I add the red line to /etc/hosts, then it gives me the local version:
```
127.0.0.1	localhost
127.0.1.1	snowy
[COLOR="Red"]127.0.2.2   www.molvray.com  molvray.com[/COLOR]

```
When I want to return to the normal, web version of molvray.com, I have to manually comment that line out.  Running **sudo a2dissite molvray.com** and reloading apache is not enough.  

That seems like a bad kludge.  I must be doing something wrong, but I can't figure out what it is.

---

### Post by dmizer on 2009-08-08
Nothing's wrong. You have no DNS in place that points to your local version, so your router just sends the request normally. The way to fix this is either to edit /etc/hosts as you've done, or add a local DNS server.

---

### Post by quixote on 2009-08-08
Thanks!  I'm off to look up how to add a local DNS server.  I'll be back once I'm hopelessly confused. :D

---

### Post by Iowan on 2009-08-09
DNSMasq is supposed to be a DNS/DHCP server.  I haven't tried installing/configuring it, but it was on a dial-up router/firewall I had.

---

### Post by dmizer on 2009-08-09
> **Iowan said:**
> DNSMasq is supposed to be a DNS/DHCP server.  I haven't tried installing/configuring it, but it was on a dial-up router/firewall I had.

Yeah ... painfully simple actually. Just install dnsmasq, and edit /etc/hosts to include the host names on your LAN. But because of this, the DNS server (DNSmasq or otherwise) shouldn't be on a portable computer. It needs to be on a computer that will be dedicated to the LAN because (at least with dnsmasq and most other DNS servers) in order to have a properly configured DNS server, you will need to edit /etc/hosts anyway.

So if your only option for a DNS server is to have it locally on your portable computer, you're probably better off just sticking with the manual /etc/hosts edit as needed. Otherwise, you're adding overhead without adding functionality.

---

### Post by quixote on 2009-08-10
Thanks for the tips, folks.  I'm going to have a look at DNSmasq.  I have an HPMediavault that's permanently attached to the LAN and sounds exactly suited to this sort of thing.

---

