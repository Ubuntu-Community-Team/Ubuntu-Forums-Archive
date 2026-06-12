---
title: "Ubuntu slow http traffic through juniper with web filtering"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by pcirne on 2009-08-27
Hi,

I'm going nuts with an issue with Ubuntu 9.04/8.04 Desktop or Server versions, when connecting to Internet through a Juniper SSG-140 with http web filtering the throughput is dramatically slow. 

Testing with speedtest.net, without web filtering I get is 7.6Mb/s upload/download, with web filtering the maximum I get is 2.6Mb/s dowload but the upload is normal at 7.6Mb/s.

This issue only happens with http (no problem with ftp) traffic on Ubuntu boxes, with Windows XP, Windows 2000 or HP-UX I got 7.6Mb/s upload/download with web filtering active.

- I've turned off IPv6 support.
- I've tried with different browsers.
- I've tried with wget.
- I've tried with servers with 1000Mb NIC
- I've tried with my laptop with 100Mb NIC.
- I've tried with a Live Ubuntu CD
- I've tried to download Ubuntu CD, with web filter the speed is only 15Kb/s, without web filtering the speed is 900Kb/s

Has somebody experienced something similar?

Thank you very much!

---

