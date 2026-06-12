---
title: "NFS suddenly slow - throttled?"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by negativ on 2009-12-23
Running server 9.04, which is mainly serving as an NFS file server on a small (~20 clients) LAN.

Server and switch are all 1000baseT, and up until the last couple of days, bandwidth hasn't been a problem.  Now suddenly, bandwidth via NFS seems to be limited to about 250Mbit/sec.  Three clients can comfortably copy (very) large files concurrently, but once we exceed three clients, it slows to a crawl.  Previously, 7 or 8 concurrent transfers could happen without much of a strain on bandwidth.  

I have narrowed it down to being specifically an NFS problem.  scp copying a large file works fine, and iperf tests were ~ 800Mbits/sec, which is about what I'd expect.  NFS seems to be the culprit.

Nothing has changed on the server or clients configuration-wise.  Any clues would be appreciated.

---

