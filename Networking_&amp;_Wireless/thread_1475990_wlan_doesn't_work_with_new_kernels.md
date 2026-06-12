---
title: "wlan doesn't work with new kernels"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by tuomonen on 2010-05-07
Hi!
I have networking problem with ubuntu.
my wireles usb stick worked with kernel 2.6.28-11 but after any newer kernel wireles doesn't work anymore.
Is new kernels missing some driver or why it doesn't work anymore?
if i'm sure my wlan stick have ralink 3070 or something. it work with any ubuntu version with this old kernel
but i would want upgrade the kernel. Also that old kernel is hard to get work with new ubuntu versions(atleast for me as i'm not expert).
What should i do?  Could i somehow add drivers from old kernel to new one?

edit: solved. I had to add following into blacklist.conf
```
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
```

I used a half year to solve this and it was this easy!!!:shock:

---

