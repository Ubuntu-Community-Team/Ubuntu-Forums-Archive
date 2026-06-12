---
title: "I'm unable to set refresh rate up to 85hz"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by Psyk[o] on 2006-06-03
Hi!
I've just bought a new monitor, a LG Flatron 795FT-plus but I'm unable to set a refreshrate higher than 85hz...
I've tried to edit /etc/X11/xorg.conf:
```

Section "Monitor"
        Identifier      "Flatron795FT"
        Option          "DPMS"
        HorizSync       30-96
        VertRefresh     50-160

```

But nothing happen, I've only one option to each resolution (85hz) with gnome-display-properties..

I'm running Dapper 6.06 with the Nvidia Driver 87.62
Does somebody can help me ?

---

