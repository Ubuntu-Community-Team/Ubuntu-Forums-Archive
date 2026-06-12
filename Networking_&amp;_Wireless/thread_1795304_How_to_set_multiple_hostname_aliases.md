---
title: "How to set multiple hostname aliases?"
date: 2011-07-02
forum: Networking &amp; Wireless
---

### Post by jazzgossen on 2011-07-02
I'd like to know if there's a good way to specify a list of possible aliases for a hostname. What I'm after is something like it could be to specify the following in /etc/hosts:

192.168.1.1 my_host
my_host.dnsalias.org my_host
some.other.domain my_host

and when doing "ssh me@my_host" the list of hostnames aliased by my_host would be looked up in order, connecting to the first one that works.

Since I want to use names and not just IP addresses, multiple lines in /etc/hosts won't work. I could write a script to accomplish the same thing, but is there already a solution to this problem?

---

### Post by SeijiSensei on 2011-07-02
It's built right into the format of /etc/hosts:

```
10.10.10.10    myhostname     myalias1 myalias2 myalias3
```

---

### Post by jazzgossen on 2011-07-05
But that line would require that my host always has IP 10.10.10.10, right? What I'm after is something that would also work with dynamic DNS.

---

### Post by helgman on 2011-07-05
> **jazzgossen said:**
> But that line would require that my host always has IP 10.10.10.10, right? What I'm after is something that would also work with dynamic DNS.

Yes, and if this document ([http://unixhelp.ed.ac.uk/CGI/man-cgi?hosts](http://unixhelp.ed.ac.uk/CGI/man-cgi?hosts)) is not out of date, that is exactly what /etc/hosts is supposed to do:

> This manual page describes the format of the /etc/hosts file. This file is a simple text file that associates IP addresses with hostnames,  one line per IP address.

Regards,
Helgman

---

### Post by jazzgossen on 2011-07-05
So I guess there isn't a way to accomplish what I was asking for in the first post without writing my own script for it, then?

---

### Post by helgman on 2011-07-05
> **jazzgossen said:**
> So I guess there isn't a way to accomplish what I was asking for in the first post without writing my own script for it, then?

Not that I know of, no. (But then again there's a lot of things I don't know ...)

Are you just setting up some automated function (have to work in unknown environments without user interaction) or is it for the convenience of not having to know if your at home or at work? 

I had a similar situation (wanted to use DNS-name for a couple of machines without running my own DNS-server at home) but I solved it with IPv6, don't know if that's an option for you ...

Regards,
Helgman

---

### Post by jazzgossen on 2011-07-05
It's for making an rsnapshot backup script work for my laptop both when I'm at work (with a static IP via eth0) and at home (with DynDNS via wlan0). 

What did you do with IPv6?

---

### Post by helgman on 2011-07-05
> **jazzgossen said:**
> What did you do with IPv6?

The (global) IPv6 address is by its nature "public" so I can use the same address (and therefore DNS-name) to connect to the server no matter where I am (and what Internet facing DNS-server I'm using at the moment).

As for your problem, I guess you'll need a script that finds out just where it is and then makes the connection according to the location. Someone must have done it before so there might be a script out there somewhere.

Regards,
Helgman

---

### Post by SeijiSensei on 2011-07-05
> **jazzgossen said:**
> It's for making an rsnapshot backup script work for my laptop both when I'm at work (with a static IP via eth0) and at home (with DynDNS via wlan0).

Perhaps you should consider, as an alternative, setting up a OpenVPN tunnel from your laptop to the backup destination.  Does that machine have a static address?  Make the laptop the client and use the "remote" directive to contact the backup server.  See [this]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") for some basics.

---

