---
title: "firefox seems to ignore resolv.conf"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by matteosistisette on 2011-06-01
Hi,

I need to manually override the domain resolution of a given domain name on my computer so that, when I write "www.agivendomain.org" on my browser, it will actually send all the requests to an IP that I decide INSTEAD of asking to the domain server.

So I placed this in /etc/hosts:
```

xx.xx.xx.xx  agivendomain.org
```(where xx.xx.xx.xx is the IP I want agivendomain.org to point to)

However, this didn't work: the name was still being resolved via the DNS server.

So I also placed this in /etc/resolv.conf:
```
order hosts, bind
```which as far as I understand, tells the system to first look at /etc/hosts and only then, if the domain is not found, ask the DNS.

This seems to work partially: if I do a ping to agivendomain.org from the terminal, it actually pings the IP that I've set in /etc/hosts.

However, Firefox still ignores the /etc/hosts and is getting the pages from the real agivendomain.org.

What am I missing?

Or maybe the browser has some domain name cache that I have to flush? If so, how?

thanks
m.

---

### Post by SeijiSensei on 2011-06-01
Actually you want to place it in /etc/hosts.conf, but the default already has this:

```

# The "order" line is only used by old versions of the C library.
order hosts,bind
multi on

```

More problematic is that your entry in /etc/hosts is for "agivendomain.org" not "www.agivendomain.org".  You need to write the entry like this:

```
10.10.10.10    example.com    www.example.com
```

Items after the initial hostname are aliases, so this will resolve both "example.com" and "www.example.com" to 10.10.10.10.

---

### Post by matteosistisette on 2011-06-01
> **SeijiSensei said:**
> More problematic is that your entry in /etc/hosts is for "agivendomain.org" not "www.agivendomain.org".  You need to write the entry like this:

```
10.10.10.10    example.com    www.example.com
```Items after the initial hostname are aliases, so this will resolve both "example.com" and "www.example.com" to 10.10.10.10.

No, that doesn't work either.

---

### Post by tristrambrelstaff on 2011-06-03
In Ubuntu the /etc/host.conf file has been superceded by /etc/nsswitch.conf in which the lookup order '/etc/hosts then dns lookup' is specified by a line like: [INDENT]   hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 
[/INDENT]See the Name Service Switch Configuration section [here]("https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html") for further details.

---

