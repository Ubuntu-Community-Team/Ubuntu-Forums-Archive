---
title: "adding routes automatically"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by davidmaxwaterman on 2011-03-09
Hi,

I have a script that I run manually when I switch my wireless interface on. The script just adds a bunch of routes.

Is there some file to which I can add these commands so that they are automatically added when the interface comes up?

Max.

---

### Post by koszta on 2011-03-09
/etc/network/if-up.d is your friend - place your scripts there :)

---

