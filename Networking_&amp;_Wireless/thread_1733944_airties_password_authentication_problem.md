---
title: "airties password authentication problem"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by mtphr on 2011-04-19
hi.

i have an msi wind u100 netbook and have been using it for almost 2 years now.

up until december 2010, i had a wireless router (cisco) and i've successfully connected via my netbook (using lot's of ubuntu's, nbr ubuntu's, finally settled at eeebuntu 3.0) without any problems at all.

finally my cisco burnt down (r.i.p.) and i got an airties rt-204v2 wireless adsl modem. i'm connected to the modem through ethernet using ubuntu 10.10 on my desktop, also using windoze on some other laptop via wireless, also through a macbook pro (using mac os x) via wireless. but the problem is, my msi netbook won't connect (again, via wireless). i have used various distributions. all detects the wireless network, entering the WPA 2 Personal password (ofc correctly) it just doesn't respond for a couple of minutes and then asks again for the password again.

i can successfully connect to lots of lots of other wireless networks (at school, cafe's, bars etc.) using the very same netbook with the very same os. (ubuntu) (unfortunately i couldnt try spesifically using another airties modem)

can it be a specific failure of hand shaking between airties and my netbook? it seems odd though, but i'm clueless at the point.

thanks in advance.

---

### Post by bkratz on 2011-04-19
Is your new wireless A/P  set for mixed mode (wpa/wpa2)? Sometimes if you separate it to either wpa or wpa2 but not both, it works a lot better? Just a guess, but maybe it will help.

---

### Post by mtphr on 2011-04-20
wow... that WAS the problem. i just switched from WPA/WPA2 to WPA2 and it connected without any problem.

it's interesting, a little annoying, simple and frustrating that have never thought of a simple solution... thanks!

---

