---
title: "Mythweb TV Listings Fatal Error"
date: 2009-02-02
forum: Mythbuntu
---

### Post by rschapman on 2009-02-02
I have a fatal error that's caused by not having enough memory specified somewhere. 

```
Fatal error: Allowed memory size of 33554432 bytes exhausted (tried to allocate 71 bytes) in /usr/share/mythtv/mythweb/modules/tv/includes/objects/Program.php on line 291
```

I have 4GB of RAM so I'm assuming it's not that but rather some PHP variable somwhere. Can someone point me in the right direction. Thanks.

Edit: I found the answer. I should have searched better. I had to changed the php limit. I found it in /etc/apache2/sites-enabled/mythweb.conf I changed the limit from 32MB to 256MB.

---

