---
title: "Slow Ubuntu 8.10 samba client performance using CIFS mounts"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by stewartjm on 2009-01-30
Since a picture is worth 1000 words, here's a pic of gkrellm running on my Ubuntu 8.10 file server.  All 3 file copies shown are of the same ~8 gig file:

[IMG]http://home.roadrunner.com/~stewartjm/samba_server_copy_from_test1.jpg[/IMG]

I've tried cifs vs smbfs, and I've tried the directio option to cifs, with no significant difference in throughput.

I would list all my hardware, but I think I can rule that out since all most machines on my network, specifically including 3 Vista 64 and 3 Ubuntu 8.10 64, can achieve 800-990Mbits/sec througput to each other using iperf.

Also I get similar CIFS mount performance using other machines running Ubuntu 8.10 as either client or server.  So I'm pretty sure the problem is on the Ubuntu client side, and in software.

Any ideas?

---

