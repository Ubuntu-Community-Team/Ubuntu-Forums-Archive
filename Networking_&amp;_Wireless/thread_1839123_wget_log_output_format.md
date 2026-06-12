---
title: "wget log output format"
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by wdschei on 2011-09-05
I have been doing a lot of testing in support of the "Slow Wireless Connection in Intel 3945abg" over on launcpad ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265?comments=all)) since I upgraded from 9.04 to Ubuntu 10.04. Since then I have gone through 10.10 and am now currently using 11.04.

I am trying to gather some statistics with a wget cron job, but the log it produces has a dynamic field for the speed. That is, it doesn't stay in Kbps or Mbps, rather it switches as it sees fit. This is a pain to parse with a simple script.

I have done some searches on the wget output and have not been very successful. Everything basically says yes it can log and here is the command line option.

Is there any way to tell wget to always use Mbps?

Thanks for the assistance.

2.6.38-11-generic-pae #48-Ubuntu SMP Fri Jul 29 20:51:21 UTC

---

