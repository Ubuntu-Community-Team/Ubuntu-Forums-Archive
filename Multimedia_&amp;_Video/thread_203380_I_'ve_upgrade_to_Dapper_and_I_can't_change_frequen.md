---
title: "I 've upgrade to Dapper and I can't change frequency"
date: 2006-06-25
forum: Multimedia &amp; Video
---

### Post by biker3 on 2006-06-25
Hi, I' ve upgraded to Dapper (from Breezy). The old kernel (2.6.12) that I use go correctly the screen, but when I start with the new kernel that Dapper has installed (2.6.15), the monitor show a black screen with a message for I use 60Khz, and not 85Hz!!!!

I don't know because this is. In my xorg.conf I have:
```

        Identifier   "Philips 170S"
        Option      "DPMS"
        HorizSync       30-82
        VertRefresh     56-76
```

 and I change the driver from ati at fglrx, but the problem perssists. Ah, and when I do "fglrxinfo" I only show:
```
Error: couldn't find RGB GLX visual!


```

](*,)

FIXED!!! It was problem of xorg.conf, that It had two devices (ati & fglrx), and Screen used ati although in the rest of file I worked with fglrx identifier.

---

