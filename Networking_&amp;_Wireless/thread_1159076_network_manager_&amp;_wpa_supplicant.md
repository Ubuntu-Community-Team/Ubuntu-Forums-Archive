---
title: "network manager &amp; wpa_supplicant"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by domoso on 2009-05-14
Why is it wpa_supplicant works for network manager but, when networking is configured by hand wpa_supplicant isn't working?

I'm running Ubuntu 8.10.

My wpa_supplicant.conf is assumed proper since it was cut & pasted over from a known working configuration. However, I've double checked the conf file. Everything looks in order.

However, wpa_supplicant reports that it associates with the AP. Then it reports a disconnect. Then it just repeats the process endlessly.

This isn't the first time that I've seen wpa_supplicant not work when configured manually but it works for network-manager. I've seen it in various versions of ubuntu over the years. This is more of an idle curiosity question that a request for help. It just seems odd to me that this would occur. Typically the solution is to compile a newer version of wpa_supplicant and the problem is resolved.

---

