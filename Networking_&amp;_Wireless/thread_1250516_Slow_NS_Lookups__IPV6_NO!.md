---
title: "Slow NS Lookups / IPV6? NO!"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by darthnuri on 2009-08-26
For some reason, I was having issues with my internet connection going slow on initial domain lookups. As soon as it was resolved, and I was connected, things proceeded at normal speeds.

I tried everything, from using alternate name servers, to blacklisting / disabling ipv6 in a variety of ways. Nothing seemed to work.

Finally, I decided to just use aptitude to reinstall all of my browser packages, and this seemed to do the trick. Well, actually, all I had to reinstall was chromium, since that was all I was using!

sudo aptitude reinstall chromium-browser

Just change the package name to whatever browser you want to reinstall, and execute!

Hopefully this solves your issue if you were having the same troubles as me!

---

