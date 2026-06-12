---
title: "Missing links from Applications/Sound &amp; Video"
date: 2009-12-25
forum: Multimedia Software
---

### Post by dictum9 on 2009-12-25
Ubuntu 9.10

sudo apt-get uninstall  libbrasero-media0 

I was troubleshooting DVD non-playing (finally fixed).
Ran this command and I think it deleted something from that menu. I re-ran it and put it back what it deleted.

But when going to Applications/Sound & Video, only see 2 choices, Movie Player and Sound recorder. I am pretty sure there were other choices before.

I just installed Ubuntu today so I am not real familiar with the menus.

---

### Post by mc4man on 2009-12-26
When you removed libbrasero-media0 you also removed brasero and rhythmbox

```
sudo apt-get install brasero rhythmbox
```

---

