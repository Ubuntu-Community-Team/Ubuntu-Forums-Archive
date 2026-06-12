---
title: "Always-on dial up"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by troyguffey on 2010-07-18
I just installed 10.04-amd64 on this computer and want to have dial-up internet automatically connect as soon as Ubuntu starts.  This happened automatically on my previous 8.10 install once I had edited /etc/wvdial.conf .   It doesn't do that now.

I've got a Trendnet TFM-560X external serial modem.

How can I get wvdial to run on bootup?

---

### Post by troyguffey on 2010-08-19
> **troyguffey said:**
> I just installed 10.04-amd64 on this computer and want to have dial-up internet automatically connect as soon as Ubuntu starts.  This happened automatically on my previous 8.10 install once I had edited /etc/wvdial.conf .   It doesn't do that now.

I've got a Trendnet TFM-560X external serial modem.

How can I get wvdial to run on bootup?

I figured out how to use the Boot-Up Manager and added wvdial.  It works now.

---

