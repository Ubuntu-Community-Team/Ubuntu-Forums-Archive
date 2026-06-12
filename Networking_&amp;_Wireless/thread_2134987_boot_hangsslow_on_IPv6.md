---
title: "boot hangs/slow on IPv6"
date: 2013-04-12
forum: Networking &amp; Wireless
---

### Post by jandrak on 2013-04-12
Hi folks,
suddenly my ubuntu suffers with slow boot.
In dmesg is:
[5.454971] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[133.962575] init: plymouth-stop pre-start process (1924) terminated with status 1

Can anyone give me a hint what is it doing for 128 seconds? I tried disable IPv6 in sysctl but it has no impact.

Thanks a lot. It drives me crazy :)

Jan

---

### Post by Lord_JABA on 2013-05-08
It happens to me to,disabling has no effect. Any ideas?

---

### Post by twipley on 2013-06-02
It happens to me, too. I am on Mint 15, which is based on 13.04. I am on 64 bits, and I first noticed this issue since I have told my system to use the proprietary graphics drivers instead of those that were in use by default.

---

