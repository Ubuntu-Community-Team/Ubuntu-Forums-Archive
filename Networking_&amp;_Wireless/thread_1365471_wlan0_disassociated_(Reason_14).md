---
title: "wlan0: disassociated (Reason: 14)"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by ddave1 on 2009-12-27
Hi,

I have an Acer Aspire a110 running ubuntu 9.10 (netbook remix).  The wireless networking issues I'm having are driving me insane.  In general the networking seems to work just fine until I attempt to do something that uses the connection constantly (e.g. streaming).  Whenever I do this the connection will restart itself after a few mins (up to 30 mins, sometimes longer).  When I check the kern.log i see the following message:

> wlan0: disassociated (Reason: 14)which is displayed as the connection is about to restart, followed by:

> wlan0: associate with AP 00:17:3f:aa:2e:69
wlan0: associate with AP 00:17:3f:aa:2e:69
wlan0: associate with AP 00:17:3f:aa:2e:69
wlan0: association with AP 00:17:3f:aa:2e:69 timed outwhich repeats a few times before a connection is re-established.

I am using the default ath5k drivers which ship with ubuntu and i havent noticed others reporting this problem.  I guess a start would be to find out what "Reason: 14" is? 

Any help on diagnosing and fixing this issue would be greatly appreciated.

Thanks.

---

### Post by ddave1 on 2010-01-02
Bump.  I'm convinced that this is some sort of bug in the ath5k drivers.

I probably haven't given the correct/enough information to be useful, but if someone could point me in the right direction..

---

