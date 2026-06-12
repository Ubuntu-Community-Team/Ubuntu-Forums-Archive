---
title: "Mythweather &amp; uk_bbc"
date: 2008-05-26
forum: Mythbuntu
---

### Post by Freddie on 2008-05-26
Hi,

I have just installed the mythweather plugin under Mythbuntu 8.04. The problem is that the only available screens are NDFD ones. Since I am in the UK, these are for the most part useless.

In /usr/share/mythtv/mythweather/scripts, however, there is a uk_bbc. Why can I not select these?

Regards, Freddie.

---

### Post by Freddie on 2008-05-27
After a fair bit of playing around I found the problem was that libxml-simple-perl was not installed. A
```

sudo apt-get install libxml-simple-perl

```
fixed this.

Regards, Freddie.

---

