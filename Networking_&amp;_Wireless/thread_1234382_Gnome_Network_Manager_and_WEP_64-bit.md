---
title: "Gnome Network Manager and WEP 64-bit"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by flylehe on 2009-08-07
Hi,
Does Gnome Network Manager only support WEP 40/128-bit key and WEP 128-bit passphrase, but not WEP 64-bit?
Is there any way to make Gnome Network Manager support WEP 64-bit?
Thanks and regards!

---

### Post by chili555 on 2009-08-07
They are the same. > Standard 64-bit WEP uses a 40 bit key (also known as WEP-40), which is concatenated with a 24-bit initialization vector (IV) to form the RC4 traffic key.From [http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy](http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy)

---

### Post by flylehe on 2009-08-07
Thank you!

If a wireless network is connected with the type "WEP (Hex [0-9/A-F])" specified in WICD, what type would I choose for the same wireless network in Gnome Network Manager? Gnome Network Manager and WICD seem to have different types of WEP at least by looking at their names.

Thanks!

---

### Post by chili555 on 2009-08-07
> what type would I choose for the same wireless network in Gnome Network Manager?Exactly what you inquired about above: 40/128-bit Hex. Be sure to try any letters both upper and lower case:```
096C7F280E
```and, if you don't connect, try:```
096c7f280e
```My test machine loves lower case.

---

