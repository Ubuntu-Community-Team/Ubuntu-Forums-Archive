---
title: "Wireshark won't work"
date: 2010-08-29
forum: Networking &amp; Wireless
---

### Post by sexyprout on 2010-08-29
Hi guys.
I remember that in the past, I succeed to sniff network traffic with Wireshark but when I tried lately, it didn't work.
- Enabled monitor and promisc mode using the command line and launched Wireshark with option 'promisc mode' on: didn't work.
- Directly launched Wireshark with option 'promisc mode' on: didn't work.
- Did the both previous things with option 'promisc mode' off: didn't work.

I'm using AR5007EG with ath5k.
Please, help me!

PS: I launched Wireshark as root.
And sorry for my poor English.

---

### Post by Jonny87 on 2010-08-30
So It still wasn't working when you ran it as root?

What was happening when it didn't work? Did it have any sort of error message?

---

### Post by sexyprout on 2010-08-30
No error message.
When I try with option 'promisc mode' on and off on my default WLAN interface (wlan0), it doesn't change anything.
When I try with mon0 (monitor mode, enabled with airmon-ng), I don't get TCP packets, or any useful.

---

