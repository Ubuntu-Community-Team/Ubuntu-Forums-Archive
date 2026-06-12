---
title: "Updated from 9.04 9.10 and now wired internet no longer works"
date: 2010-07-17
forum: Networking &amp; Wireless
---

### Post by ed_d on 2010-07-17
Yeah I know a bit behind.....

I used the "Upgrade" option the last couple of nights to go from 8.04 LTS and was going to go to latest version. Well got the upgrade done last night on 9.10 and now Broadcom gigabit wired connect will not connect to internet. Can ping router just fine. Just cannot get outside of it. Shows as configured in ifconfig. But the name of it under the network manager is odd. Its ifupdown (eth0) (default) and maps to ent1. Gives me the dhcp connection as well.
So any help would be great as I want to continue the upgrade path for my desk top and really do not want to do a reload.

Thanks,
Ed

---

### Post by Iowan on 2010-07-18
Can you ping Internet by IP address (74.125.95.106)? If so, check */etc/resolv.conf*, if not, check **route -n**.

---

