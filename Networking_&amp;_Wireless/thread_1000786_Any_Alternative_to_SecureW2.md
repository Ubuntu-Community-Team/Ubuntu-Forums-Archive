---
title: "Any Alternative to SecureW2?"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by hexbomber on 2008-12-03
So, my university uses SecureW2 to create an encrypted connection required in order to join the wireless network. The problem is SecureW2 (afaik) is Windows only...

Is there any alternative to SecureW2 for Linux, if so how hard is it to setup?

---

### Post by hexbomber on 2008-12-05
So, looks like there is a solution with wpa_supplicant, although I keep getting errors when trying to bring it up.

---

### Post by marin123 on 2009-12-04
this is how you can do it... if you have wpasupplicant you can simply wait until computer finds wireless signal and then set encryption to wpa2(enterprise) and TTLS (tunnelled TLS)... type in your user name like this [email]xxx@xyz.com[/email] and password... leave the anonymus identity field blank... this should do the trick (works for me)

---

