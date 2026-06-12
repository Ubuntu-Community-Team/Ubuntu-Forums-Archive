---
title: "[SOLVED] Can't connect wireless"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by detroit/zero on 2009-01-12
Hi,
Using Hardy with all current updates.

I'm at work, and I brought my laptop. They have wireless access. Given the SSID and the passphrase, I can't make Ubuntu connect to the network. Nm-applet just keeps having me enter and re-enter the password. I know the access point is available - I'm connected right now to the same network on the same computer using my Vista partition.

I'm launching off on a month-long trip to the UK today, and I hope I don't have a bunch of problems connecting to wireless networks wherever I go. I know there was an issue with connecting to public hotspots like at hotels or whatever, where they give you an SSID and there's no password required, and when you connect to their network it takes you to a in-house webpage where you enter your CC# or password or whatever... But I'll cross that bridge when I get to it.

Can someone tell me why, when given an SSID and a WEP-128bit passphrase, will nm-applet not connect me to the network?

---

### Post by detroit/zero on 2009-01-12
I was able to fix it myself in this instance. Turns out it's a WEP 64-bit hex key, and when nm-applet popped up asking for the password, it defaulted to 128-bit hex. By switching from 128- to 64-bit, I was able to connect this time.

Hopefully that trick works when I get around to needing to connect to a public hotspot.

---

