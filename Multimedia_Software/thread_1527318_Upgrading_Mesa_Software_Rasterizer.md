---
title: "Upgrading Mesa Software Rasterizer"
date: 2010-07-09
forum: Multimedia Software
---

### Post by biubidboy on 2010-07-09
Hello all.
Having upgraded to the most recent Wine (1.2-rc6), I have discovered that I can no longer run games in 16bpp. Whenever I do, I get the following error:

```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  1067
  Current serial number in output stream:  1071
```I have read that, in most cases, re-installing or upgrading video drivers fixes this problem. I, however, am using the Mesa software drivers included with Ubuntu by default. Would upgrading my installation of Mesa help me out and, if so, how would I go about doing this?

Thanks,
Michael.

---

### Post by biubidboy on 2010-07-12
Bump (sorry guys, but it would be really great to find a solution)

---

### Post by Yellow Pasque on 2010-07-12
It would be helpful to post your /var/log/Xorg.0.log and /etc/X11/xorg.conf (if you have one).

---

### Post by biubidboy on 2010-07-14
Hi. 
Because I have no xorg.conf file, I usually use "startx -- :1 -depth 16" to use games that require 16bpp. Would you like me to post my "Xorg.1.log" file rather than "Xorg.0.log"?
Thank you
Michael.

---

