---
title: "Upgrading monitor"
date: 2006-06-12
forum: Multimedia &amp; Video
---

### Post by johnleonard on 2006-06-12
Hi

I am thinking of replacing my CRT monitor with a TFT LCD TV/Monitor. I have two questions:

1) Will the new monitor be auto-detected by Dapper?
2) Will it be able to deal with widescreen 16:9 format, given that my current monitor is set at 4:3?

Thanks

---

### Post by Gustav on 2006-06-12
To set up Dapper for your new monitor you should run:```
sudo dpkg-reconfigure xserver-xorg
```(After you have changed to the new monitor)

After that everything should work.

---

