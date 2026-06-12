---
title: "Note about Broadcom STA driver (wl) and WPA(2)"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by chenxiaolong on 2009-11-26
If you use the Broadcom STA driver (wl), you've probably noticed that it has problems connecting or reconnecting to WPA(2) networks. After changing almost all the settings on my router, I figured out what the problem is. It won't connect (or rarely) to networks with TKIP encryption. All you need to do is to set it to AES encryption. Don't select Auto, even if you router supports it. I also had to change my wireless frequency channel to a frequency between 1 and 6. I originally used channel 8, which would only connect on boot up (of the computer). 

I hope this information is useful :D.

---

