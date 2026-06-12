---
title: "loadkeys: $sun_t6_custom missing"
date: 2011-02-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by zika on 2011-02-04
As of some time today, instead of (perfectly) working loadkeys in console I get:
```
:~$loadkeys hr
Loadinh hr
Unknown name $sun_t6_custom
:~$
```

The same happens with rs, or any other keyboard layout I try...

Any ideas?
(To explain: in main console I do, always, use US keyboard layout. But, since I have rs keyboard, I do change it in /etc/rc.local with:

loadkeys hr
setfont Uni2-VGA16.psf.gz

(hr in order not to bother with two alphabets in rs domain, that is sorted out, once X is up))

---

### Post by zika on 2011-02-08
Upgrade solved this &#8222;problem&#8220;...

---

