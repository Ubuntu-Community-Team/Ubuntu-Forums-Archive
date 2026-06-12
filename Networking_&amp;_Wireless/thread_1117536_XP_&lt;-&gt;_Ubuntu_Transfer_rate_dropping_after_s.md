---
title: "XP &lt;-&gt; Ubuntu: Transfer rate dropping after some seconds"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by MacUntu on 2009-04-06
The network: XP PC cable-connected to a WRT54GL router, Ubuntu notebook connected wirelessly.

The problem: LAN transfer rates (tested XP -> Ubuntu via shares and ftp) seem to be fine at first (20-30 seconds) at ~2MB/sec. but then start dropping to unbearable ~200KB/sec.

Restarting the transfer will continue with just ~200KB/sec. unless I restart networking (sudo /etc/init.d/NetworkManager stop+start). Then I again experience the normal start and huge dropping like described above.

For the direction Ubuntu -> XP: transfer rates vary heavily beetween ~200KB/sec. and ~1MB/sec. (~500KB/sec. on average).

Why I suspect Ubuntu to be the culprit: I installed XP on the Ubuntu notebook and the transfer rate between the two XP systems is constant at 2.2-2.5MB/sec. (both directions).

Any ideas?

(I'm using the Jackalope Beta but I'm not convinced that's the problem so I'm posting this here.)

---

### Post by MacUntu on 2009-04-06
Intel wireless driver seems to cause the slow downs: [http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1932](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1932)

---

