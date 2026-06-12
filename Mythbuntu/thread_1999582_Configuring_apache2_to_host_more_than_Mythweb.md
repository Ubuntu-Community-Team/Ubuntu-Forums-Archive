---
title: "Configuring apache2 to host more than Mythweb"
date: 2012-06-08
forum: Mythbuntu
---

### Post by lamogo on 2012-06-08
I am using Mythbuntu 12.04 and am attempting to host more than one website with apache2. I have created two directories in /var/www and placed mythweb in one and the default index.html in the other. I made the changes to the two config files in the sites-available available directory, and have two separate dyndns address setup for each one. I can access mythweb properly when I go to the ServerName address, but when I try the other site it adds "/mythweb/" to the end of the address and says 404 not found. How do I change that, I can't find anything in default-mythbuntu, mythweb.conf or my other config that needs to be changed.

How to I allow other sites to also be hosted on my Mythbuntu server?

---

### Post by tgm4883 on 2012-06-08
> **lamogo said:**
> I am using Mythbuntu 12.04 and am attempting to host more than one website with apache2. I have created two directories in /var/www and placed mythweb in one and the default index.html in the other. I made the changes to the two config files in the sites-available available directory, and have two separate dyndns address setup for each one. I can access mythweb properly when I go to the ServerName address, but when I try the other site it adds "/mythweb/" to the end of the address and says 404 not found. How do I change that, I can't find anything in default-mythbuntu, mythweb.conf or my other config that needs to be changed.

How to I allow other sites to also be hosted on my Mythbuntu server?

I believe it's just 

```
dpkg-reconfigure mythweb
```

---

### Post by lamogo on 2012-06-08
Thanks tgm4883. I tried that on apache2 but thanks for the help. Anyways I was on the right track which means I am learning. :)

---

