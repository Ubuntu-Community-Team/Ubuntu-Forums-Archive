---
title: "Samba"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by Barnicle on 2009-04-09
I have successfully configured Samba to authenticate against my Active Directory, but I am still prompted to login after I have logged into my windows domain, and I'm trying to map the drive. Why isn't Samba using my credentials from my domain login?

The only thing I can see that isn't working is my wbinfo -u queries. I get 'Error looking up domain user'

These are all my config files: [http://paste.ubuntu.com/147640/](http://paste.ubuntu.com/147640/)

Please, help!

---

### Post by Barnicle on 2009-04-09
Any help out there?

---

### Post by Barnicle on 2009-04-09
I got wbinfo to work, and I joined the domain ok. I just want to know why it's prompting me for a login when I'm mapping to the drive, if I already have my domain credentials.

---

