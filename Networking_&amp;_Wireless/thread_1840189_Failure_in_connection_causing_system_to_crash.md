---
title: "Failure in connection causing system to crash??"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by New00Folder on 2011-09-07
Hi!

My ubuntu system crashes a lot (about once daily). I am running ubuntu 10.10 (linux 2.6.35) and I use a USB modem which connects to a GSM network to connect to the internet. It's of the kind that has to be switched from storage mode to modem mode before use.

I strongly suspect that these crashes occur when something like "dial failed" or "connection failed" errors should occur. I have nothing to support this theory but the comparison of the device's performance in windows7 and linux shows similarity in the timing and frequency of the above mentioned errors in windows and crashes in linux. The syslog entries or kernel messages don't have anything relevant around the time crashes occur. Often the last entry before a crash would be tens of minutes before the crash.

This USB modem comes with drivers for windows and mac but none for linux. So I'm using a driver called option (v 0.7.2) which is perhaps included in the kernel.

It's rainy season here and signal quality is not always ideal. I have to boot windows to access internet which is nearly most of the time.

Please advise me how to avoid these crashes.
(Or to pinpoint what causes the crashes.)
I'm not a novice and I'll try to provide as much information as you might need.

Thanks.

---

### Post by New00Folder on 2011-10-13
The device manufacturer mailed me a program that apparently uses it's own version of "usbserial" and it is working well after a few initial hiccups.

No more crashes!!

---

