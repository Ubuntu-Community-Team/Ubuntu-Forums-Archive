---
title: "I confused were domain part in local email is defined"
date: 2011-10-02
forum: Networking &amp; Wireless
---

### Post by Horatio on 2011-10-02
This is a digression of:
[http://ubuntuforums.org/showthread.php?p=11304516]("http://ubuntuforums.org/showthread.php?p=11304516")

because I found a new question.

Okay I found a quick fix.

I was typing example@earth in the drupal 7 email field, and it was rejected.

I just was able to change the email in the field from a gmail email to a local email address in the form, [email]example@earth.local[/email] ( I had tried example@earth .

but nslookup still does not work as I'm expecting:
```


nslookup earth.local
Server:         192.168.1.1
Address:        192.168.1.1#53

** server can't find earth.local: NXDOMAIN

```

I had tryed:
```

$ nslookup earth
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   earth
Address: 63.251.179.13
Name:   earth
Address: 8.15.7.117


```

and ip

```

 nslookup 192.168.1.100
Server:         192.168.1.1
Address:        192.168.1.1#53

** server can't find 100.1.168.192.in-addr.arpa.: NXDOMAIN

```

I guess I don't need a verifyable NXDOMAIN then for drupal to accept my local email address. I just need to be more specific about the domain part.

So

1. where is, "local" in, "example@earth.local" being defined? 

2. do I need to install and configure bind for nslookup to be able to do a reverse name lookup, but then why does it fail to give any local network information when I can ping using my host name, no my ip?

Thanks

---

