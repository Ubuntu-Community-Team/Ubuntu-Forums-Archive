---
title: "Have different port direct to different directory on Apache2 webserver?"
date: 2011-10-30
forum: Networking &amp; Wireless
---

### Post by Pithikos on 2011-10-30
I have two websites at the following directories.

```
/var/www/site1
/var/www/site2
```When browsing to _mysite.com_ I want to get to **site1** and when browsing to _mysite.com:1000_ I want to get to **site2**.  Is this possible?

---

### Post by SeijiSensei on 2011-10-30
Yes.  You'll need an additional Listen directive:

```
Listen 10.10.10.10:1000
```

(replacing 10.10.10.10 with your server's actual IP address) then designate the use of port 1000 in the VirtualHost container declaration like this:

```
<VirtualHost 10.10.10.10:1000>

stuff

</VirtualHost>
```

This is how Apache listens for SSL and non-SSL connections on separate ports, 443 and 80.

---

