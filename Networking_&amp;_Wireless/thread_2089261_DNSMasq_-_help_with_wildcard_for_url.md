---
title: "DNSMasq - help with wildcard for url"
date: 2012-11-28
forum: Networking &amp; Wireless
---

### Post by nozomii on 2012-11-28
[LEFT]Hi!

I've just set up DNSMasq to use specific DNS for sites like hulu and bbc etc.
It works great for those sites but I have a problem with tv.nrk.no.

I managed to get the available live streams to work by adding this to dnsmasq.conf:
```
server=/tv.nrk.no/nrk1-f.akamaihd.net/nrk2-f.akamaihd.net/nrk3-f.akamaihd.net/xxx.xx.xx.xx
```That makes it possible for me to stream the 3 channels that are available live.


The problem is to get the on demand streams to work. They have akamai addresses like this:
```
nordond***xx***-f.akamaihd.net.........
```Where xx changes from every video. Like 10a or 27f etc.


Can I use some kind of wildcard to get it to work with every nordond***xx***-f.akamaihd.net video somehow? I don't want to use the smartdns for every akamai link, just the ones from NRK.

thanks for any help
[/LEFT]

---

### Post by nozomii on 2012-12-07
what was that? oh, right... absolute silence

---

### Post by karloskar on 2013-01-09
I think you will be fine without the first part of the domain name.

```

server=/akamaihd.net/xxx.xxx.xxx.xxx

```

That's what I use for internal wildcard routing altough I use *address* and not *server*.

---

