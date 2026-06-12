---
title: "mounting/extracting a bootable iso"
date: 2009-05-05
forum: Multimedia Software
---

### Post by excogitation on 2009-05-05
I can mount and extract the iso (Win 7) fine,
e.g.
```
sudo mount -t iso9660 -o loop 7100.0.090421-1700_x86fre_client_en-us_retail_ultimate-grc1culfrer_en_dvd.iso tmp/
```
but the problem is that it only shows/extracts a readme.txt without content.
I also tried isomaster but it only shows the txt as well.

I can burn and use the iso, but how do I extract/mount it properly?

---

### Post by excogitation on 2009-05-05
hmmm... seems that wasn't too bright...

```
sudo mount -o loop 7100.0.090421-1700_x86fre_client_en-us_retail_ultimate-grc1culfrer_en_dvd.iso tmp/
```

does work.
Archive mounter could still be improved.

---

