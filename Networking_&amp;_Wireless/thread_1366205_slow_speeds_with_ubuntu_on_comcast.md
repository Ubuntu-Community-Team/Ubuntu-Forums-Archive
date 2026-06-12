---
title: "slow speeds with ubuntu on comcast"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by earthboom on 2009-12-28
I have Comcast internet i'm running ubuntu 9.10 on a desktop box.  I do not use a router the modem is plugged directly into the built in gigabyte nic on the box. speed tests show my download speeds at around 1.5 Mbs.  if i plug the same modem into an old xp laptop the same speed tests show my speeds at around 12.5 Mbs. this is a significant difference!  I have tested speed with both comcast and cnet speed tests with similar results.  I would be grateful for any help in resolving this issue.  I have been running ubuntu for about a year now, but have very little command line experience.  I mostly use the gui for everything, so please speak slowly using small words so that I might be able to understand.

---

### Post by sliketymo on 2009-12-28
Maybe this will help a little.First,edit your network connection,set the mtu value to 10000.Next,in Firefox set ipv6disabled to "true".Try a speed test and see if that helps.

---

