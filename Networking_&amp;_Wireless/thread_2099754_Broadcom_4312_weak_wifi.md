---
title: "Broadcom 4312 weak wifi"
date: 2012-12-30
forum: Networking &amp; Wireless
---

### Post by s9032g@comcast.net on 2012-12-30
My built in Broadcom 4312 802.11b/g 14e4 receives a wifi signal with 33% less mps than my Edimax 300Mbps wireless b/g/n usb adapter. Former at 50, latter at 75.

Is there any way to get a better signal from the Broadcom other than replacing it? I have the latest driver for the Broadcom installed.

---

### Post by ahallubuntu on 2012-12-30
The shown Mbps connection rate can be deceiving.  Your real-life throughput may not be as different as you think.  For simply surfing the internet, it may not make much difference.

If you are talking about the transfer rate on an internal network, I'd check the real-time transfer rate.  Copy a large file in Nautilus from your laptop to another computer by dragging it from one folder to the shared folder on another computer.  After about 10 seconds it should report an average transfer rate.  How is that different using one card vs. the other?  That's what really matters, not the indicated connection rate.

Your internal Broadcom card is 802.11g though, so of course it will connect only up to 54Mbps.  The only way to improve that  beyond 54Mbps is to replace the card with an 802.11n card.  If you have an HP or Lenovo laptop, replacing the card may not be possible (they whitelist wireless cards in the BIOS, so you can install only an approved card).  If it's a Dell, Toshiba, Acer, etc. replacing the card might be easier and cheaper than you think.  Depends on the exact model of laptop you have.

---

### Post by s9032g@comcast.net on 2013-01-01
ahallubuntu

Thanks.

I think you are on the mark.

---

