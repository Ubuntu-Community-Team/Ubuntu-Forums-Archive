---
title: "A trend I see"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by BrandonND on 2009-03-22
I have system monitor and I have noticed a trend and it is quite annoying

**caution, rambling ahead**

My cpu will run at about 1% unless I do something at which point it will spiike. Then go down to about 1% again.

My memory will hover on ~30% with the cache taking the rest up.

My Network seems eratic, yesterday i was downloading at 160 kb/s
Now i am downloading clam AV, and it is running at  1974 b/s 
Does this seem irregulaer to anyone besides me? 

When I boot up i get a message about vbox0 being unable to initialize br0. And a few messages once startup and shutdown about my network card.

---

### Post by jtb_90 on 2009-03-22
Might not be too helpful but to lower your RAM usage, open up a terminal and

```
sudo echo 3 | sudo tee /proc/sys/vm/drop_caches
```

Should lower your cache to 3%

---

