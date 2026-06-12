---
title: "Slow WiFi speeds at any range."
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by kenster2001 on 2009-10-15
I've been experiencing a strange problem with jaunty (and karmic alpha) where immediatly after connecting to a wifi point i will get normal speeds(1.5MB/s), then after several minutes the speed will work its way down to about 100KB/s and stay there. At this point, If I reconnect using NetworkManager, the speeds will jump back up to 1.5MB/s.

All speeds were measured by transferring a file from an FTP server on my lan. Distance does not seem to be a factor. If I am right on top of the AP, or 150ft away, I'll end up getting about 100KB/s.

The interesting thing is this is effecting two different computers. It effects an old Compaq laptop (jaunty) with either a Zydas1211 or an RTL8187L, as well as my current laptop, an MSI Ms-1223 (jaunty and karmic alpha) with either an Intel 4965agn or an RTL8187L. I've tried both the drivers shipped with jaunty and the latest stable compat-wireless drivers and it makes no difference with this issue (but now signal strength for the RTL8187L is correctly measured).

I don't think this happened with 8.10 on the old Compaq, but I can't recall for sure.

---

### Post by kenster2001 on 2009-10-16
Bump, and update.

It turns out that it doesn't settle at 100KB/s it just hits a point where the slowdown slows down.

It just keeps dropping until it essentially dies. Transferring files more frequently makes it die faster.

---

